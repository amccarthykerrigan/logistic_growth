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

## Methods
### Initial plots
I first plotted the data from the 'experiment1.csv' file using the package ggplot2, to observe the behaviour of the graph. This formed a logistic growth curve.
<br>
I then plotted the data with a logarithmic scale on the y axis, to observe the relationship between population size and time as a linear relationship. 
<br>
These plots can be found in the 'plot_data.R' file within this repository. 

### Applying and plotting a linear model
**Applying linear model**
<br>
I then fitted a linear model to the log-transformed data. This allowed me to estimate the model's parameters using a linear approximation. Firstly, I have created code to output the values for N0 and r, using a value for t which is within the exponential growth section of the graph.
<br>
I have then created code to output the carrying capacity value, using a t value where the graph has reached carrying capacity.
<br>
This code can be found in the 'fit_linear_model.R' file within this repository.

**Plotting data and linear model**
<br>
Finally, I have plotted the data set again, with the linear model as a function on the graph. This allows me to visualise the linear model's parameter estimations alongside the actual data points. This plot can be found in the 'plot_data_and_model.R' file in the repository.

### Simulating and comparing exponential growth and logistic growth
**Calculations with the exponential and logistic growth functions**
<br>
I have created an exponential growth function and logistic growth function, and used them to simulate the bacterial population size at t=4980 under each condition, using the parameters estimated from the linear model applied above. This code can be viewed in the 'calculate_exponential_growth_Q2.R' file.
<br>
This t value has been chosen because it is the time when the last data point was recorded in the data set. Therefore, it will allow us to be certain that we will be obtaining values for population size which represent the differences in the exponential and logistic growth curves - ie. we expect to obtain the carrying capacity value for the logistic growth curve and a much higher value for the exponential growth curve.

**Plotting the exponential and logistic growth curves**
<br>
I have then plotted the exponential and logistic growth curves. I have plotted them together on a singular graph, but have also plotted them separately to see the non-transformed graph shapes over a set period of time (0 - 4980 minutes). The code for these growth curves can be seen in the 'logistic_and_exponential_growth.R' file in the repository.
<br>
Since the model of exponential growth reaches much higher population numbers over the same period of time, we are unable to see the shape formed by the non-transformed logistic growth curve when they are plotted together. The separate graphs allow clearer visualisation of the non-transformed patterns, and the graph with both curves allows visualisation of the patterns together, when the y-scale (population size variable) has been log-transformed.


## Results
### Linear model estimated parameters for the data set
From the linear model I have run, I found the following estimated values:

**N0 = 7**
<br>
This value for N0 I have estimated as 7, after rounding it up from 6.883.
<br>
**r = 0.01004**
<br>
**K = 60,000,000,000**


### Comparing the exponential and logistic models for population size at t = 4980
Using the parameter estimates of the N0 and r values, I found the population size at t=4980 under **exponential growth**:

**N = 3.626392e+22**


I then compared this with the population size predicted at t=4980 under **logistic growth**:

**N = 6e+10**
<br>
This output is the carrying capacity value.

When we have exponential growth, we find that population sizes are able to reach much higher numbers, and are not limited by resource availability or the build up of waste products, as in a logistic growth model. Therefore, this is why we see the much higher population size under an exponential growth curve compared with a logistic growth curve.


### Graphs comparing the exponential growth and logistic growth of the *E. coli* population
The code for these growth curves can be seen in the 'logistic_and_exponential_growth.R' file in the repository and the graph itself can be found here:

  <p align="center">
     <img src="https://github.com/amccarthykerrigan/logistic_growth/blob/eae22840c2ca41bd69f241428698e76a03b19e22/logistic_and_exponential_growth_graphs.jpeg">
  </p> 



## Discussion
The linear model we have created for the data set is able to estimate the initial population size, rate of growth and carrying capacity parameters. However, since this is only an estimate, we observe that the function, when plotted alongside the data set, does not exactly align with the position of the data's logistic growth curve. This estimate still creates the same overall sigmoidal shape as the data set itself, though. We would expect that the linear model will not match the pattern in the data set exactly, since it is only an estimation.

When we simulate what the data would do if we had exponential growth, we find that the population size at t=4980 is much higher than the the population size under logistic growth. The logistic growth curve has reached the carrying capacity at t=4980, whereas the population under simulated exponential growth has been able to continue multiplying. This is expected because we can see the carrying capacity is reached at around t=2500 in the initial plot of the data - the data set follows a logistic growth curve. Equally, exponential growth is unrestricted by limited resources, and so we would expect growth under this simulation to reach much higher population sizes for the same initial population size and growth rate.

When we plot these exponential and logistic growth curves, we can visualise this pattern. On the graph labelled 'Logistic vs Exponential Growth', we can see that the population under exponential growth surpasses the carrying capacity, which is reached at around t=2500, and we can visualise the continued population growth from this point. The population under logistic growth is constrained by the carrying capacity. 





