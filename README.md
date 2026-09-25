# NYC Taxi Operations Intelligence

Interactive BI case study built from a **public sample** of NYC Taxi and Limousine Commission trip records distributed through seaborn-data.

## Business question
Which pickup hours are busiest within this sample, and how do trip volume and fares differ by pickup borough and payment method?

## Dashboard
Open [index.html](index.html) in a browser. No install or account required. Filters update all four KPIs and the daily and hourly charts. Hover over chart marks for exact values.

## Findings from the supplied sample
- The transformed March 2019 slice contains **6,432 trips** and **$119,118.67** in reported total charges.
- These totals describe **the supplied sample**, not all NYC taxi trips. Do not extrapolate them to citywide demand.
- One source pickup record dated February 28 is excluded so the analysis period is strictly March.

## Model and metric definitions
Source grain: one trip. Dashboard grain: one combination of pickup date, pickup hour, pickup borough, and payment method (**2,212 groups**). Missing borough or payment labels become `Unknown`. Trips count valid March pickup records. Trip total sums the source `total` field; average fare is `SUM(fare) / SUM(trips)`; tips per trip is `SUM(tip) / SUM(trips)`. Totals include source charges beyond the fare, so fare and total are deliberately separate. No claim is made that tips are complete for cash trips.

## Source and reproducibility
[seaborn-data taxis.csv](https://github.com/mwaskom/seaborn-data/blob/master/taxis.csv), Git blob SHA `ded045b462d361b8a0e5ddcdd6c3361cce4ddab4`, sampled from [NYC TLC trip records](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page). `data.js` embeds only aggregate rows and no source trip-level detail. Run `python build_data.py` to regenerate it after checking the pinned source; the script stops if upstream content changes. The underlying TLC data and sample are subject to source documentation and collection limitations.

## Portfolio skills
ETL aggregation, grain design, sample-aware KPIs, dimensional filters, operational demand patterns, and source traceability.
