# Predicting-Auto-Insurance-Claim-Frequency-A-Poisson-Model
A Poisson regression model for how often motor insurance policyholders claim, built on approximately 678,000 French motor policies.

## The question
How often will a given policyholder claim in a year, and which factors drive that frequency? Unlike a severity model (claim size), frequency modelling has top deal with two things that make it distinctly actuarial: **rare events** and **exposure**.

## The data 
- Approximately 678,000 policies
- Target: ClaimNb - Number of claims per policy
- Key column: Exposure - The fraction of a year each policy was observed
- Risk factors: Driver age, vehicle ageand power, fuel type, brand, the bonus-malus (no-claims) score, region, area, and population density

## Method
