# Using-ML-to-Discover-New-Physical-Model

Using ML to Discover New Physical Model for Seafloor Temperature Prediction.

Reference Paper:

Forrest, J., E. Marcucci, and P. Scott, 2005, Geothermal gradients and  subsurface temperatures in the Northern Gulf of Mexico: Gulf Coast  Association of Geological Societies Transactions, 55, 233–248. 

Liu, Y., J. H. Casado, M. El-Toukhy, and S. Tai, 2021, Basin-wide  empirical rock-physics transform and its application in Campeche  Basin: The Leading Edge, 40, no. 3, 178–184. (https://library.seg.org/doi/10.1190/tle40030178.1)

Notes:

The input file is the .csv file and it will be loaded and be used to run the optimization into the Jupiter Notebook: [Use_ML_Discover_New_Physical_Model.ipynb](/Use_ML_Discover_New_Physical_Model.ipynb).

Decription:

In Liu et al., (2021), we provided a physical model to model the seafloor temperature based on the mean seafloor temperature data published in Forrest et al., (2005). When we compare this model's result to the original data, it looks like below:

![image](https://github.com/user-attachments/assets/1961c89c-204d-4be9-9b06-1164108e7629)

We can see that for majority of the figure, there is a good match, however, in the middle portion of the figure, there are some mis-match which indicates that the model can be further improved. This original physical model was created from experience. There are many empirical equations in rock physics that have a decreasing trend, such as porosity. So we simulated such a trend and obtained the original equation: Tsfl=40+37*(1-0.00025*D)**2.9, here D is water depth in feet and Tsfl is the seafloor temperature in F.

Now, let's further improve the accuracy and find a better physical model to satisfy the original data. Why not use machine learning to do it.

So let's first try a few regressions, including linear, polynomial, and logarithmic regressions. However, the results are not very satisfactory, as shown below.

![image](https://github.com/user-attachments/assets/9a65bd4d-35e9-4dda-a818-613d9552c2fb)

Then let's try the exponential decay model and logistic model. They both worked out OK except for that the seafloor temperature should not be lower than a limit that is close to 40 F.

To fix this issue, we just need to set a lower limit to the modeled seafloor temperature and the problem is solved.

![image](https://github.com/user-attachments/assets/50227782-b9ae-4b94-8939-7ef8f57a9bb1)

In general, using ML, we are able to discover better physical models that satisfy the data. This exercise is a simple example but demonstrated some basic steps to achieve a discovery. 

In conclusion, through this exercise a simple new model that we can recommend to predict seafloor temperature is:

Exponential Decay Model: Tsfl = 38.45 + 40.22 * exp(-0.0008 * D),
with a lower limit set to 40 F.

Here, D is water depth in feet, Tsfl is seafloor temperature in F.
