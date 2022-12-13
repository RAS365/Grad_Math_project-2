# Grad_Math_project-2

# Do Modelling Papers Lie to US?

The paper had 4 different types of model which the author had used to model the immune responses of mice inoculated with both H5N1 and H1N1. The model which had all the parameters with value was model 4. 
- Due to this, my assessment will also use model 4, i.e., the values of $r_{I,M}$ and $r_{V,M}$ will be set to an arbitrarily low number (1e-04 units). The paper sets these values to 0, but a value of 0 cannot be used to perform parametric sensitivity analysis.

Note to self- DO NOT USE SOLVE_IVP FOR ANYTHING WHICH INVOLVES A LOT OF ITERATIONS. PARAMETRIC SENSITIVITY TOOK ME 4H OF RUNTIME IN SOLVE_IVP COMPARED TO 2 MINUTES IN ODEINT. ONE EVENING WASTED.

The parameters used has been tabulated below:
![image](https://user-images.githubusercontent.com/112502037/207427272-34c11b30-72a8-47bf-b609-f759ee1e6cc7.png)

The preliminary plots made using the parameters given in the paper are as follows:

![image](https://user-images.githubusercontent.com/112502037/207427869-a6f15b0c-9aaf-4ee3-ab9a-5b3fd6a458a4.png)

These plots do follow the behaviours shown in the paper, but don't really have simlar values, especially for the macrophages. Macrophages are a glorious mess in terms of the cell counts. This most likely has to do with the parameter values.

### Parametric sensitivity analysis

Here, we try to perform a global sensitivity analysis by varying the parameters to a range of 20% in both the directions. We also choose a sample size of 5000 (arbitrary).


![image](https://user-images.githubusercontent.com/112502037/207428137-fc912672-b187-47e0-890d-e12cf9140a79.png)

We can see that all the variables show a change in their steady state values when subject to a change in the parameters. We do not notice any behaviour changes for any of the variables by changing any parameter.

We now take a look at the regression results for the sensitivity analysis.

![image](https://user-images.githubusercontent.com/112502037/207428859-06519c8f-53c8-4ddf-a4b6-3ca38e21bf9f.png)

We can see that there are parameters which have no sensitivity. These are mostly the ones associated with the equation governing the macrophage cell count.

We select the parameter $r_{V,I}$ because of its high sensitivity, and perform a bifurcation analysis by varying it.

![image](https://user-images.githubusercontent.com/112502037/207429500-ca00b595-30b1-4e5d-b2eb-d5380f727a6c.png)

We can see that, despite choosing the parameter with the highest sensitvity, the flow of V does not change significantly.

We do see significant changes in the behaviour of V and M:

![image](https://user-images.githubusercontent.com/112502037/207430173-3987b9d6-65ce-4f90-bd2d-f254f530d3b9.png)

![image](https://user-images.githubusercontent.com/112502037/207430219-a31dbdd3-ccff-4b2b-b00c-51e6ecee9e76.png)

### Data fits:

![image](https://user-images.githubusercontent.com/112502037/207430316-f1acdd43-d56e-48cb-899b-92ee73ee0c09.png)

Here, we observe that when we try fitting our data to 3 points as instructed and compare it to fitting the data in the Ackerman et al. paper, we  can find that the fit which uses 3 points does not replicate the behaviour expected, in contrast with the fit perfomed on the Ackerman data.

### Conclusions

- The authors might not have mentioned specific constraints set to the solvers, which results in the fit mismatch.
- Authors perform a parametric space analysis by using “MCMC” and “Basin hopping” methods – useful getting more reasonable fits
- Sometimes, no matter what we do, the model just refuses to fit. 




