# Judgment log: <Cindy Nguyen>

## How I used AI in this project

(Final submission only.)

## Entries

### Nov 12: baseline for the 1650 to 1750 cm⁻¹ region

**Judgment log 1 for working draft**

- **What the assistant suggested:** Claude suggested exploring the dataset before choosing a prediction method. This included checking the variables and units, examining the concentration distributions, comparing the chemical concentrations, plotting the UV-Vis spectra, checking for outliers or baseline shifts, and investigating how absorbance at different wavelengths relates to each chemical concentration.

- **What I did:** I used Claude’s suggestions to guide my analysis of the UV-Vis dataset. I focused on examining the relationship between absorbance and the four chemical concentrations: Bromide, Fluopyram, Diflufenican, and Mesosulfuron. I then used curve fitting to compare linear and quadratic models for each chemical.

- **Why, from my data:** The curve-fitting results showed that the linear model performed better than the quadratic model for all four chemicals. Bromide had the strongest result, with an R² of 0.2701 at 217.5 nm, while Fluopyram, Diflufenican, and Mesosulfuron had negative R² values. This suggests that using only one wavelength for each chemical does not predict the concentrations reliably. Claude’s suggestion to examine multiple wavelengths is therefore important for further investigation, because the full spectrum may contain more useful information than a single wavelength.

**Judgment log 2 for working draft**

- **What the assistant suggested:** Claude recommended PLS regression because the dataset contains 221 highly correlated absorbance measurements. It suggested using grouped cross-validation to select the number of latent variables instead of choosing an arbitrary number.

- **What I did:** I accepted Claude's recommendation and tested between 1 and 15 latent variables. Instead of using the maximum of 15 for every chemical, I selected 4 for Bromide, 4 for Fluopyram, 1 for Diflufenican, and 1 for Mesosulfuron.

- **Why, from my data:** Cross-validation showed that using fewer latent variables within 5% of the minimum CV RMSE was a way to avoid unnecessary model complexity. The selected numbers were different for each chemical, showing that each concentration required a different model complexity. The held-out test results also showed that PLS did not predict all four chemicals reliably, so choosing the latent variables carefully did not guarantee accurate predictions.