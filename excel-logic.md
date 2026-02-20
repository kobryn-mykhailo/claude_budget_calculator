# Excel Formula Logic — FPP v7.3

This documents the key calculation logic from `Project-Budget-for-FPP-v7_3.xlsx` that the web app replicates.

## Core Calculation Flow

```
Features Estimate (PERT) → Dev Hours per Phase
                        ↓
Input Data (params)   → Stabilization, Contingency, Prep, Post-Release
                        ↓
Project Team (rates)  → COGS, Revenue, DPM
                        ↓
Risks (EMV)           → Added to Contingency Reserve
                        ↓
Project Estimate      → Final Budget Summary
```

## PERT Estimation (Features Estimate sheet)

```
Expected = (Optimistic + Pessimistic + 4 × MostLikely) / 6
StdDev = (Pessimistic - Optimistic) / 6
Variance = StdDev²
DevHours = Expected × 8  (man-days to hours)
RiskFlag = (Pessimistic - Optimistic) > Optimistic
```

## Role Effort Distribution

Each role's hours are proportional to DEV headcount ratio:
```
RoleHours = (TotalDevHours / DEV_count) × Role_count
```

## Stabilization
```
StabilizationHours = TotalExecutionEfforts × StabilizationPct
```

## Contingency Reserve
```
ContingencyHours = TotalExecutionEfforts × ContingencyPct + SUM(RiskEMV)
RiskEMV = EstimateHours × Probability
```

## Preparation
```
PrepHours = PrepWorkload × 40 × PrepMembers × PrepWeeks
```

## Revenue Calculation
```
Revenue_ExtRate = TotalHours × AvgExternalRate
Revenue_DPM = COGS / (1 - DPM_target)
DPM = (Revenue - COGS) / Revenue
```

## Project Team Rate Aggregation

```
AvgInternalRate = SUM(HourlyRate × Count) / TotalCount
AvgExternalRate = SUM(ExtRate × Count) / TotalCount
RoleAvgRate = SUM(Role_HourlyRate × Count) / Role_Count
```
