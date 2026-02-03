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
To introduce non-linearity, each NO₂ value (`x`) is converted into a transformed variable (`z`) using a transformation function that depends on the university roll number.

The transformation is defined as:

\[
z = x + a_r \sin(b_r x)
\]

Where:
- \( a_r = 0.05 \times (r \bmod 7) \)
- \( b_r = 0.3 \times (r \bmod 5 + 1) \)
- \( r \) represents the university roll number

This step ensures that the transformation is unique for each student.

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

