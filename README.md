# Logistic growth simulation of an *Escherichia coli*
This is a repository containing the code to simulate the growth of an isolate of the bacterium *Escherichia coli* (*E. coli*) in a test tube containing 1ml of growth medium.
<br>
I am looking to estimate the initial population size of the bacterial population (N0), rate of growth (r) and the carrying capacity (K) from experimental data. I am then investigating the logistic growth model of the population in comparison with an exponential growth model.

The experimental data used to simulate this growth comes from the 'experiment1.csv' file, downloaded from the **Logistic growth data** project on Open Science Framework's website (contributor Jose Gabriel Nino Barreat).

The versions of the packages which I have used for each file are listed in the 'package-versions.txt' file in the repository.


## Hypotheses
### For the given data set
We expect that the bacteria will initially enter a lag phase, where the population will be adjusting to the environment of the growth medium. During this phase, there will be cellular activity, but we do not expect large changes in population size, and the non-transformed graph will likely appear flat during this timeframe.

We then expect to see an exponential increase in population size, as the bacteria divide via binary fission, with the population doubling in size after each period of generation.

As the population continues to grow, the resources will be depleted and the waste products will build up in the population. This is a closed system, which means that the resources are not being replenished, and therefore we will not see exponential growth continued for an infinite time period. The resources will begin to become scarce, and at this point, we expect the growth rate of the population to decline. Eventually the population size will remain constant, entering the stationary growth phase, where the number of cells dividing and number of cells dying occur at the same rate. This is the carrying capacity of the bacterial population.

### For the simulated exponential growth
Under simulated exponential population growth, we do not expect to see this same pattern. We expect the bacterial population will show the same initial lag phase as it adjusts to the environment, but following this we expect to see an extended period of growth, with no limiting carrying capacity. Exponential growth would occur in a bacterial system not limited by resources and not constrained by a build up of waste products.

## Method and Results
### Q1: Initial plots
I first plotted the data from the 'experiment1.csv' file using the package ggplot2, to observe the behaviour of the graph. This formed a logistic growth curve. This can be seen here:

  <p align="center">
     <img src="https://github.com/1066509/logistic_growth/blob/8ffe7632233e801a613fe843581e98e485691e78/initial_plot_logisitic_growth.png">
  </p> 

I then plotted the data with a logarithmic scale on the y axis, to observe the relationship between population size and time as a linear relationship. This plot can be seen here:

  <p align="center">
     <img src="https://github.com/1066509/logistic_growth/blob/1a3a93fd8a22e1e30ecccd561d26b37f8546455f/initial_plot_log_scale_q1.png">
  </p>

The code for these plots can be found in the 'plot_data.R' file within this repository. 

### Q1: Applying a linear model
I then fitted a linear model to the log-transformed data. This allowed me to estimate the model's parameters using a linear approximation. Firstly, I have created code to output the values for N0 and r, using a value of t<1000 which is within the exponential growth section of the graph.
<br>
I have then created code to output the carrying capacity value, using a t value of t>3180 where the graph has reached carrying capacity.
<br>
This code can be found in the 'fit_linear_model.R' file within this repository.

**Results:**

From the linear model I have run, I found the following estimated values:

**N0 = 976**
<br>
This value for N0 I have estimated as 976, after rounding it up from 975.5486.
<br>
**r = 0.01004**
<br>
**K = 60,000,000,000**

### Q1: Plotting data and linear model
Finally, I have plotted the data set again, with the linear model as a function on the graph. This allows me to visualise the linear model's parameter estimations alongside the actual data points. This plot can be seen below and the code for this can be found in the 'plot_data_and_model.R' file in the repository:

  <p align="center">
     <img src="https://github.com/1066509/logistic_growth/blob/9c8cd97a671978dc208ef1874d4d1a6d8ae4d85d/plot_data_and_model_graph_q1.png">
  </p>

### Q2: Comparing the exponential and logistic models for population size at t = 4980
I have created an exponential growth function and logistic growth function, and used them to simulate the bacterial population size at t=4980 under each condition, using the parameters estimated from the linear model applied above. This code can be viewed in the 'calculate_exponential_growth_Q2.R' file.
<br>
This t value has been chosen because it is the time when the last data point was recorded in the data set. Therefore, it will allow us to be certain that we will be obtaining values for population size which represent the differences in the exponential and logistic growth curves - ie. we expect to obtain the carrying capacity value for the logistic growth curve and a much higher value for the exponential growth curve.
<br>
<br>

**Results:**

**Exponential growth**: Using the parameter estimates of the N0 and r values, I found the population size at t=4980 under exponential growth:

**N = 5.06e+24**

**Logistic growth**: I then compared this with the population size predicted at t=4980 under logistic growth:

**N = 6e+10**
<br>
This output is the carrying capacity value.

When we have exponential growth, we find that population sizes are able to reach much higher numbers, and are not limited by resource availability or the build up of waste products, as in a logistic growth model. Therefore, this is why we see the much higher population size under an exponential growth curve compared with a logistic growth curve.


### Q3: Graphs comparing the exponential growth and logistic growth of the *E. coli* population
I have then plotted the exponential and logistic growth curves. I have plotted them together on a singular graph, but have also plotted them separately to see the non-transformed graph shapes over a set period of time (0 - 4980 minutes). The code for these growth curves can be seen in the 'logistic_and_exponential_growth.R' file in the repository.
<br>
Since the model of exponential growth reaches much higher population numbers over the same period of time, we are unable to see the shape formed by the non-transformed logistic growth curve when they are plotted together. The separate graphs allow clearer visualisation of the non-transformed patterns, and the graph with both curves allows visualisation of the patterns together, when the y-scale (population size variable) has been log-transformed.

The code for these growth curves can be seen in the 'logistic_and_exponential_growth.R' file in the repository and the graph itself can be found here:

  <p align="center">
     <img src="https://github.com/1066509/logistic_growth/blob/919e7d13d08b5d5ce002e68f1c637f0cc0c18314/logistic_vs_exponential_graphs_q3.png">
  </p>


## Discussion
The linear model we have created for the data set is able to estimate the initial population size, rate of growth and carrying capacity parameters. From the plot of this model alongside the data, we can see that this estimate creates the same overall sigmoidal shape as the data set itself and runs through the data points of the data set. Therefore, it provides a good estimate of the parameters of the data.

When we simulate what the data would do if we had exponential growth, we find that the population size at t=4980 is much higher than the the population size under logistic growth. The logistic growth curve has reached the carrying capacity at t=4980, whereas the population under simulated exponential growth has been able to continue multiplying. This is expected because we can see the carrying capacity is reached at around t=2500 in the initial plot of the data - the data set follows a logistic growth curve. Equally, exponential growth is unrestricted by limited resources, and so we would expect growth under this simulation to reach much higher population sizes for the same initial population size and growth rate.

When we plot these exponential and logistic growth curves, we can visualise this pattern. On the graph labelled 'Logistic vs Exponential Growth', we can see that the population under exponential growth surpasses the carrying capacity, which is reached at around t=2500, and we can visualise the continued population growth from this point. The population under logistic growth is constrained by the carrying capacity. 





