# Predicting-Auto-Insurance-Claim-Frequency-A-Poisson-Model
A Poisson regression model for how often motor insurance policyholders claim, built on approximately 678,000 French motor policies.

## The question
How often will a given policyholder claim in a year, and which factors drive that frequency? Unlike a severity model (claim size), frequency modelling has to deal with two things that make it distinctly actuarial: **rare events** and **exposure**.

## The data 
- Approximately 678,000 policies
- Target: ClaimNb - Number of claims per policy
- Key column: Exposure - The fraction of a year each policy was observed
- Risk factors: Driver age, vehicle age and power, fuel type, brand, the bonus-malus (no-claims) score, region, area, and population density

## Method
- **Exposure offset**: A policy observed for a full year has more opportunity to claim than one observed for a month. The model predicts a claim rate and weighs each policy by its exposure
- **Scaling**: Features are standardised so the optimiser converges
- **Model**: Poisson Regression
- **Split**: 80/20

 ## Findings
 From our findings, we found out that:
- **Bonus-malus score** raised claim frequency the most (worse no-claims
  history predicts more claims).
- **Vehicle age** and **driver age** lowered it (older cars and older drivers
  claim less often).
- **Urban/denser areas** raised frequency while **rural areas** lowered it, consistent
  with more traffic meaning more incidents.

Every major factor moves in the direction real insurance experience would
predict, which is a good sign the model learned something.

**But the predictive lift is modest.** The model's Poisson deviance (approx. 0.3293)
was only slightly better than the naive baseline (approx. 0.3314). In other words, the
risk factors *do* help but only a little.

## Takeaway
**Individual claim occurrence is dominated by randomness.** Risk factors shift the odds in somewhat sensible directions,
but they don't determine whether a specific driver claims next year; that's
mostly luck. This is the fundamental nature of insurance frequency, and it's
exactly *why* insurers price by pooling thousands of policies rather than
predicting individuals. A model claiming to predict individual claims with high
confidence would be a red flag, not a success.

## What I'd do next
The next thing I'd do would be pairing this model with a severity model to get a full frequency x severity price. I will also try using a model that catches non-linear patterns and compare its deviance. From there, I will clean any implausible records that might distort the results, such as policies with exposure over 1 or with unrealistically high claim counts.
