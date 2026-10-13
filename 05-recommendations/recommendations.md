# Recommendations

Based on the [process analysis](../03-process/process-analysis.md) and the [data analysis](../04-data-analysis/analysis-summary.md).
Requirements are defined in [user-stories.md](../02-requirements/user-stories.md).

> All figures come from synthetic data and must be validated with real order data before implementation.

## 1. Summary
The delivery problem is concentrated in peak hours. Three process stages (restaurant confirmation, courier assignment and waiting at the restaurant) explain 61% of the extra peak delay, and 91% of cancellations are caused by process bottlenecks.
Six changes are recommended, delivered in three phases.

## 2. Recommendations

| # | Recommendation | Bottleneck | User stories | Goal | Estimated impact | Effort |
|---|---|---|---|---|---|---|
| R1 | 3-minute confirmation timer for restaurants with auto-cancel | B1 | US-05 | G1, G2 | About -0.9 min avg delivery time; targets 33% of cancellations | Low |
| R2 | Automatic courier matching (nearest courier, 60 sec accept window) | B3 | US-09 | G1, G2 | About -1.5 min; targets 30% of cancellations | Medium |
| R3 | Restaurant sets prep time and marks order ready; courier dispatch is timed to it | B2 | US-07, US-08 | G1 | About -1.4 min | Medium |
| R4 | ETA before ordering and live order tracking with status notifications | B4 | US-01, US-02 | G2, G3 | Targets 27% of cancellations (long wait) | Medium |
| R5 | Item checklist at pickup and in-app problem reporting | B5, B6 | US-11, US-04 | G3 | Fewer wrong or missing items, faster resolution (not quantified) | Low to medium |
| R6 | Operations KPI dashboard, delay alerts and peak capacity management | B7 | US-12, US-13 | G1, G2 | Targets the remaining peak delay in preparation and travel, up to about -2.4 min | Medium to high |

Estimates: each stage is reduced from its peak average to its off-peak average (confirmation 4.0 to 1.9 min, assignment 7.0 to 3.5 min, wait 5.1 to 1.8 min). Peak orders are 42% of delivered orders, so the effect on the overall average is smaller than on peak orders.
Effort ratings are analyst assumptions and must be validated with the development team.

## 3. Expected Results

| KPI | Today | After R1-R4 (estimate) | Target |
|---|---|---|---|
| Avg delivery time | 40.9 min | about 37 min | 34 min |
| Cancellation rate | 11.0% | about 6% | 7% |

- Delivery time: R1-R3 together save about 3.8 min (40.9 to about 37.2).
- Cancellation rate: if each of the three process-related causes (30 of 33 cancellations) is halved, about 15 cancellations are saved, giving 18 of 300 orders (6.0%).
- Customer rating (4.1 now, target 4.4) is not estimated. It depends on ETA accuracy, order accuracy (R5) and peak performance.

**Note on goal G1:** even if peak performance fully reaches off-peak level, the average delivery time would be about 34.8 min, so the 34 min target also needs a small off-peak improvement. An interim target of 37 min after phase 2 is realistic. G1 should be reviewed after phase 3.

## 4. Roadmap

| Phase | Timing | Scope |
|---|---|---|
| 1. Quick wins | Weeks 1-6 | R1 confirmation timer, order status notifications (US-02), KPI dashboard (US-12) to measure the baseline, menu availability (US-06) |
| 2. Core process | Weeks 7-12 | R2 automatic courier matching, R3 prep time and ready status, ETA before ordering (US-01) |
| 3. Quality and control | Months 4-6 | R5 item checklist and problem reporting, delay alerts (US-13), peak capacity management, review of targets |

## 5. Success Metrics (monitor weekly)
- Avg delivery time, split into peak and off-peak
- Duration of each stage (confirmation, assignment, wait at restaurant)
- Cancellation rate by reason
- SLA breach rate (delivery over 45 min)
- Avg customer rating

## 6. Risks and Mitigation

| Risk | Mitigation |
|---|---|
| Restaurants ignore the confirmation timer | Training, onboarding support, performance feedback to restaurants |
| Couriers reject automatic assignments | Pilot with a small courier group, collect feedback, adjust matching rules |
| Stage timestamps are not captured accurately | Define data capture in the requirements, validate data quality before the pilot |
| Results from synthetic data do not match reality | Re-run the analysis with real data before committing budget |

## 7. Next Steps
1. Validate the findings with real order and timestamp data
2. Review the recommendations with the Operations Manager and Product Owner
3. Convert the prioritized user stories into a backlog
4. Pilot R1-R3 in one or two districts and compare with the rest of the city
5. Update the TO-BE process after the pilot