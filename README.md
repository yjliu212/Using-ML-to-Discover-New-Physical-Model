# Using-ML-to-Discover-New-Physical-Model

Using ML to Discover New Physical Model for Seafloor Temperature Prediction.

Reference Paper:

Forrest, J., E. Marcucci, and P. Scott, 2005, Geothermal gradients and  subsurface temperatures in the Northern Gulf of Mexico: Gulf Coast  Association of Geological Societies Transactions, 55, 233–248. 

Liu, Y., J. H. Casado, M. El-Toukhy, and S. Tai, 2021, Basin-wide  empirical rock-physics transform and its application in Campeche  Basin: The Leading Edge, 40, no. 3, 178–184. (https://library.seg.org/doi/10.1190/tle40030178.1)

Notes:

The input file is the .csv file and it will be loaded and be used to run the optimization in the Jupiter Notebook: [Use_ML_Discover_New_Physical_Model.ipynb](/Use_ML_Discover_New_Physical_Model.ipynb).

Decription:

In Liu et al. (2021), we developed a physical model to estimate seafloor temperature based on the mean seafloor temperature data published by Forrest et al. (2005). The comparison of the model's predictions with the original data is shown below:

![image](https://github.com/user-attachments/assets/1961c89c-204d-4be9-9b06-1164108e7629)

For most of the data, the model provides a good match. However, there is some deviation in the middle section, indicating potential for further improvement. This original model was based on empirical experience. In rock physics, many trends, such as porosity, exhibit a similar decreasing pattern. Following this logic, we derived the original equation: Tsfl=40+37*(1-0.00025*D)**2.9, where D is water depth in feet and Tsfl is the seafloor temperature in degrees Fahrenheit (F).

To improve the model’s accuracy, we explored using machine learning techniques. We began by applying several regressions, including linear, polynomial, and logarithmic. However, none provided a satisfactory fit. As shown below.

![image](https://github.com/user-attachments/assets/9a65bd4d-35e9-4dda-a818-613d9552c2fb)

We then tried the exponential decay and logistic models, both of which performed better. However, the seafloor temperature should not drop below a threshold close to 40°F, which these models initially failed to account for.

To address this, we set a lower limit for the modeled seafloor temperature, ensuring it doesn't fall below 40°F, effectively resolving the issue.

![image](https://github.com/user-attachments/assets/50227782-b9ae-4b94-8939-7ef8f57a9bb1)

This example demonstrates how machine learning can help refine physical models, offering better fits to empirical data. While this is a simple case, it illustrates the basic steps involved in model discovery.

In conclusion, we recommend the following new model for predicting seafloor temperature:

Exponential Decay Model: Tsfl = 38.45 + 40.22 * exp(-0.0008 * D),
with a lower limit set to 40 F.

Here, D is water depth in feet, Tsfl is seafloor temperature in F.
