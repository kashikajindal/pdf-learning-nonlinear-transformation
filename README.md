# Learning a Probability Density Function from Air Quality Data

## Project Description
This project focuses on learning a probability density function (PDF) from real-world air quality measurements.  
A roll-number-dependent non-linear transformation is applied to the data before estimating the parameters of the distribution. This makes the modeling process both personalized and non-linear.

---

## Data Source
- **Dataset:** India Air Quality Dataset  
- **Platform:** Kaggle  
- **Dataset Link:** https://www.kaggle.com/datasets/shrutibhargava94/india-air-quality-data  
- **Selected Attribute:** NO₂ (Nitrogen Dioxide concentration)

---

## Step 1: Data Transformation
In this step, each value of the NO2 feature (denoted as *x*) is transformed into a new variable *z* using a roll-number-parameterized non-linear transformation function.

The transformation function is defined as:

T_r(x) = x + a_r * sin(b_r * x)

Thus, the transformed variable is given by:
z = T_r(x)
Where:
- `a_r = 0.05 × (rmod 7)`
- `b_r = 0.3 × (rmod 5 + 1)`
- `r` is the university roll number

---

## Step 2: Probability Distribution Modeling
After transformation, the variable `z` is assumed to follow a Gaussian-like distribution.  
The probability density function is given by:

\[
\hat{p}(z) = c \cdot e^{-\lambda (z - \mu)^2}
\]

The parameters are estimated using **Maximum Likelihood Estimation (MLE)**:
- **μ (Mu):** Mean of the transformed data  
- **σ (Sigma):** Standard deviation of the transformed data  
- **λ (Lambda):** \( \frac{1}{2\sigma^2} \)  
- **c:** \( \frac{1}{\sqrt{2\pi\sigma^2}} \)

---

## Results
The final estimated parameters obtained from the transformed NO₂ data are listed below:

| Parameter | Estimated Value |
|---------|-----------------|
| λ (Lambda) | 0.0014609760484308439 |
| μ (Mu) | 25.812999155899675 |
| c | 0.02156485844361762 |

These parameters define the learned probability density function for the transformed variable `z`.

---

## Conclusion
This experiment demonstrates how non-linear transformations and statistical estimation techniques can be combined to learn a probability distribution from environmental data. The results confirm that the transformed data follows a smooth and well-defined probability density function.

