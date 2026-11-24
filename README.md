# Who should we email? An uplift modeling study

Which customers does an email campaign actually change, as opposed to customers who would have bought
anyway? This project estimates the causal effect of email on visits, conversions and spend, models who is
persuadable, and turns that into a targeting policy with an expected revenue gain.

**Status:** in progress.

## Data

`data/raw/hillstrom_email.csv` is the Kevin Hillstrom MineThatData E-Mail Analytics and Data Mining
Challenge dataset (2008). It has 64,000 customers, randomly assigned to one of three groups for a
two-week campaign:

| segment | customers |
|---|---|
| Mens E-Mail | 21,307 |
| Womens E-Mail | 21,387 |
| No E-Mail (control) | 21,306 |

Features are `recency`, `history_segment`, `history`, `mens`, `womens`, `zip_code`, `newbie` and
`channel`. Outcomes are `visit`, `conversion` and `spend`.

## Plan

1. **A/B readout.** Treatment vs. control lift, confidence intervals and a power check for each email
   version.
2. **Uplift models.** T-learner, X-learner and causal forest (`causalml` / `econml`), evaluated with Qini
   and uplift curves.
3. **Observational check.** Hide the randomization, estimate the effect with propensity matching and
   inverse-propensity weighting, and compare it with the true randomized effect.
4. **Targeting policy.** Who to email, and the incremental conversions and revenue compared with
   emailing everyone.
5. **Optional, later.** Repeat at scale on the Criteo Uplift dataset (about 14M rows), and a
   difference-in-differences example.

## Layout

```
data/raw/     source data (unchanged)
notebooks/    exploration and analysis
src/          reusable code
reports/      writeup and figures
```
