# criteo-uplift

## Project objectives

This mini project is designed to help me learn and practice:

- causal inference principles, especially randomized experiments and treatment effects
- A/B testing concepts and how to interpret results from randomized assignment
- uplift modeling ideas and how exposure differs from assignment
- data-quality checks, statistical estimation, and confidence intervals
- communicating findings clearly in a reproducible notebook format

The notebook uses the public Criteo Uplift dataset and focuses on a real-world advertising experiment with treatment assignment, exposure, visits, and conversion outcomes.

## What I am learning

- How to estimate an intention-to-treat (ITT) effect from randomized assignment
- Why actual ad exposure is not the same as randomized treatment
- How to compare binary outcomes across treatment and control groups
- How to validate assumptions, check balance, and interpret statistical uncertainty
- How to frame causal claims carefully and distinguish them from naive attribution

## What I have learned so far

### Treatment and control versus exposure and no exposure

In this dataset, `treatment` represents randomized assignment to the group eligible to receive ads; it does not mean that the user necessarily saw an ad. `exposure` records whether the user actually saw an ad.

- Comparing the treatment and control groups is valid for estimating the intention-to-treat effect because assignment was randomized. The control group estimates the outcome that would occur without making users eligible for the campaign.
- Comparing exposed and unexposed users is only descriptive because exposure was not randomized. Users who see an ad may differ systematically from users who do not—for example, they may browse more often or already have stronger purchase intent.
- Consequently, the exposed-versus-unexposed difference combines the possible effect of seeing an ad with selection into exposure. A conversion that follows an ad can be attributed to the ad in a user journey, but it was not necessarily caused by the ad. This is the distinction between attribution and incrementality.

### Interpreting lift carefully

The observed treatment-control lift is an estimate of the causal effect, not proof that the entire observed difference was caused by treatment. Even under random assignment, one realized experiment contains random variation:


$$
\text{observed lift}=\text{true treatment effect}+\text{randomization error}.
$$

Confidence intervals and hypothesis tests help determine how much of the observed lift could plausibly be due to random variation. Absolute and relative lift must also be distinguished:

- **Absolute lift** is the difference in outcome rates, usually reported in percentage points.
- **Relative lift** measures that difference relative to the control-group baseline.

A large relative lift can correspond to a small absolute change when the baseline conversion rate is low. For this reason, lift should be reported with the group rates, its confidence interval, and a practical measure such as estimated incremental visits or conversions.

## AI collaboration disclaimer

This repository was created in collaboration with AI. I prompt questions and ideas, and the AI helps with analysis, code, and explanation. I review, adapt, and validate the work as part of my learning process.
