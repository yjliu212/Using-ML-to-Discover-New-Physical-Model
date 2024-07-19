# Using-ML-to-Discover-New-Physical-Model

Using ML to Discover New Physical Model for Seafloor Temperature Estimation

Reference Paper:

Forrest, J., E. Marcucci, and P. Scott, 2005, Geothermal gradients and  subsurface temperatures in the Northern Gulf of Mexico: Gulf Coast  Association of Geological Societies Transactions, 55, 233–248. 

Liu, Y., J. H. Casado, M. El-Toukhy, and S. Tai, 2021, Basin-wide  empirical rock-physics transform and its application in Campeche  Basin: The Leading Edge, 40, no. 3, 178–185,

Notes:

The input file is the .csv file and it will be called into the Jupiter Notebook.

Decription:

In Liu et al., (2021), I provided a physical model to model the seafloor temperature based on the mean seafloor temperature data published in Forrest et al., (2005). Once we compare this model results to the original data, it looks like below:

![image](https://github.com/user-attachments/assets/1961c89c-204d-4be9-9b06-1164108e7629)

We can see that for majority of the figure, the match is OK, however, there are still room to improve in the middle portion of the figure. How I came up with this original physical model is by picking an equation that I like from many empirical rock physics models, which in general has this decreasing trend. I forgot which one exactly.

Now, I want to further improve the accuracy and find a better physical model to satisfy the original data. Why not use machine learning to do it.

So I first try a few regressions, inclusing linear, polynomial, and Logarithmic Regressions. However, the results are not very satisfactory.

![image](https://github.com/user-attachments/assets/9a65bd4d-35e9-4dda-a818-613d9552c2fb)

Then I try the exponential decay model and logistic model. They worked out OK except that the seafloor temperature will not be lower than a limit close to 40 F.

![image](https://github.com/user-attachments/assets/328384a4-ba3c-451a-b414-5405d8fb83ce)
![image](https://github.com/user-attachments/assets/2bb957ab-f38e-4491-8fcf-b66b163bb267)

So to fix this we just need to set a lower limit to the seafloor temperature and the problem solved.

![image](https://github.com/user-attachments/assets/50227782-b9ae-4b94-8939-7ef8f57a9bb1)

In general, using ML, it is able to discover better physical models that fit the data. The final model that I like to use in the future for estimation seafloor temperature would be:

Exponential Decay Model Equation: Tsfl = 38.45 + 40.22 * exp(-0.0008 * D)
with a lower limit set to around 40 F.
