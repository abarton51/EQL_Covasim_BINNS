# Equation Learning for COVASIM with added Adaptive Behaviors using Biologically-Informed Neural Networks

All equation learning and BINNs code has been adapted from [[1.]](https://arxiv.org/abs/2005.13073) and [Xin Li](xli86@ncsu.edu).

All code under the folder titled "covasim" is the work of the ***["Institute for Disease Modeling"](https://github.com/InstituteforDiseaseModeling/covasim)***.
***
## Abstract
&emsp; Mathematical models have been shown to be valuable tools for forecasting and evaluating public health interventions during epidemics such as COVID-19. Covasim is an open-source agent based model (ABM) that was recently developed to simulate the transmission of COVID-19. Covasim uses an advanced Susceptible, Exposed, Infected, Recovered (SEIR) that has additional states involving other details e.g., symptomatic and quarantine statuses. Covasim has been validated with real-world data and utilized for simulating the potential effect of public health interventions.  Covasim’s base model does not implement adaptive behaviors; however, by leveraging Covasim’s flexibility, we can utilize its resources to generate data for scenarios where human behavior can adapt based on the current state of the model. Human behaviors, such as compliance to masking guidelines, have been shown to be variable between individuals and variable in time, i.e., individuals adapt their masking behavior in response to their perceived risk of infection as infection rates fluctuate. We extended the Covasim model to incorporate adaptive masking behavior to investigate its effect on Covasim’s predicted forecast. We ran the data generated from this model through Biologically Informed Neural Networks (BINNs) to learn an ordinary differential equation (ODE) approximation of this model. We performed sensitivity analysis on the learned ODE to determine the parameters with the largest influence on how masking behavior affected infection prevalence. The extended Covasim and BINNs computational pipeline we developed will be open-sourced to provide a quantitative framework for incorporating adaptive human behavior into forecasting future epidemics.
***
### Introduction
&emsp; COVASIM is an agent-based simulation created by the Institute for Disease Modeling in response to the COVID-19 pandemic and the apparent need for resources on simulating, studying, modeling, and predicting disease spread. The creators of COVASIM created custom features for users to interact with and change the dynamics of the simulator. In the paper, "Covasim: An Agent-Based Model of COVID-19 Dynamics and Interventions", the simulation using a variety of features to model agent interactions and probabilities of infection, tracing, quarantining, etc. However, adaptive behaviors of the agents have not been thoroughly studied or modeled. In order to accurately model the spread of disease in a human population, we must take into account the adaptive and maladaptive behaviors of agents in response to the current state of the disease as well as other attributes of their own setting.

&emsp; Biologically-Informed Neural Networks attempt to tackle the *model specification* problem by using multilayer perceptrons as nonlinear functional parameters as surrogate models in order to minmize *a priori* assumptions about the form of the differential equation(s) as well as expand the number of possible solutions to such a model. Physics-Informed Neural Networks, first introduced in [2018](https://www.sciencedirect.com/science/article/abs/pii/S0021999118307125), primarily tackle the issue of inferring a surface of solutions to a system of differential equations. This inherently requires prior knowledge and assumptions of the governing dynamics. One of the most apparent assumptions, which is directly addressed by [1.] and mentioned in [3.], is the form of each of the parameters in the governing system of equations. Generally, these parameters may be linear, nonlinear, or constant functions. If they are nonlinear, the space of possible functions is too large to accurately solve for without making large assumptions using methods of sparse regression. Hence, using a universal function approximator (such as an MLP) allows us to learn these nonlinear components and then infer underlying relationships and functions *a posteriori*.

***
#### References

1. Lagergren, J. H., Nardini, J. T., Baker, R. E., Simpson, M. J., & Flores, K. B. (2020). Biologically-informed neural networks guide mechanistic modeling from sparse experimental data. PLOS Computational Biology, 16(12). https://doi.org/10.1371/journal.pcbi.1008462 

2. Kerr, C. C., Stuart, R. M., Mistry, D., Abeysuriya, R. G., Rosenfeld, K., Hart, G. R., Núñez, R. C., Cohen, J. A., Selvaraj, P., Hagedorn, B., George, L., Jastrzębski, M., Izzo, A., Fowler, G., Palmer, A., Delport, D., Scott, N., Kelly, S., Bennette, C. S., … Klein, D. J. (2020). Covasim: An Agent-Based Model of COVID-19 Dynamics and Interventions. https://doi.org/10.1101/2020.05.10.20097469
