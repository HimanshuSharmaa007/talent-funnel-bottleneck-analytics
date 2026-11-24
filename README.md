Talent Funnel Bottleneck Analytics — WhiteCollar Realty

An end-to-end recruitment analytics and executive visualization project built to diagnose hiring pipeline drop-offs, measure recruiter call-delay SLAs, and evaluate sourcing channel ROI across multi-market real estate roles (Gurgaon, Noida, and Dubai).

Business Problem & Objectives

High-volume recruitment pipelines often suffer from hidden conversion bottlenecks—such as delayed candidate outreach, high Face-to-Face (F2F) interview no-shows, and mismatched candidate profiles. Without stage-level visibility, Talent Acquisition teams struggle to pinpoint whether pipeline leakage stems from sourcing quality, role/location mismatches, or slow recruiter follow-ups.

Core Objectives

Standardize & Clean Raw Data: Deduplicate candidate records by normalized phone numbers, standardize date formats, and resolve inconsistent status labels.

Engineer Funnel & SLA Features: Map raw statuses into structured hiring stages, extract primary rejection reasons from recruiter remarks, and calculate call-delay SLA buckets (0–1d, 2–3d, 4+ days).

Quantify Bottlenecks: Measure how outreach delays impact F2F interview attendance and identify which sourcing channels yield the highest-converting hires.

Executive Visualization: Deliver an interactive single-page Power BI scorecard (Funnel Bottleneck Overview) to monitor stage progression, rejection root causes, and recruiter performance.

Repository Structure

talent-funnel-bottleneck-analytics/
├── data/
│   ├── raw_hiring_tracker.csv                  # Raw candidate outreach and status logs
│   ├── clean_hiring_tracker.csv                # Deduplicated and standardized hiring dataset
│   └── enriched_hiring_tracker.csv             # Analysis-ready dataset with funnel, rejection & SLA features
├── notebooks/
│   ├── 01_data_generation_and_cleaning.ipynb   # Data ingestion, phone normalization, deduplication & validation
│   └── 02_eda_and_bottleneck_analysis.ipynb    # Feature engineering, SLA impact analysis & visual EDA
├── dashboard/
│   └── talent_funnel_dashboard.pbix            # Interactive Power BI executive dashboard
└── README.md


Tech Stack

Python (pandas, numpy, matplotlib, seaborn): Data cleaning, deduplication, feature engineering, and exploratory visual analysis in Jupyter Notebook.

Microsoft Power BI Desktop: Data modeling, custom DAX measures, conditional formatting, and interactive executive reporting.

Analytical Workflow

1. Data Cleaning & Deduplication (01_data_generation_and_cleaning.ipynb)

Standardized 10-digit mobile numbers and removed duplicate candidate entries while preserving the latest interaction state.

Cleaned inconsistent text casing across roles (HR Recruiter, Pre-Sales, Sales Executive, Sales Manager, VP Sales), target markets (Gurgaon, Noida, Dubai), and sourcing channels (Naukri, LinkedIn, Indeed, Apna, Walk-In, Referral).

Validated chronological consistency between applied_date and contacted_date.

2. Feature Engineering & Bottleneck EDA (02_eda_and_bottleneck_analysis.ipynb)

Funnel Stage Mapping: Categorized raw statuses into sequential stages (1. Screened / Cold through 6. Joined).

Rejection Root-Cause Extraction: Parsed unstructured recruiter remarks into standardized rejection categories (No Real Estate Exp / Irrelevant, Skill / Communication Gap, Salary Mismatch, Location / Role Mismatch, and Other).

Call-Delay SLA Bucketing: Computed call_delay_days (contacted_date - applied_date) and grouped leads into three response tiers:

1. Same / Next Day (0-1d)

2. Moderate Delay (2-3d)

3. High Delay (4+ days)

3. Power BI Executive Dashboard (dashboard/talent_funnel_dashboard.pbix)

Built on a single-page executive layout (Funnel Bottleneck Overview) with dynamic slicers for Target Market, Role, and Recruiter:

Top KPI Bar: Tracks Total Leads, F2F Appeared, F2F Rate %, Total Joined, and Join Rate %.

Hiring Funnel Drop-off by Stage: Visualizes candidate volume and conversion attrition from initial screening to final joining.

Top Rejection Reasons: Highlights primary disqualification drivers among rejected applicants (excluding active/non-rejected records).

F2F Show-Up Rate by Call Delay (SLA): Demonstrates the drop in interview attendance as recruiter response time increases beyond 24 hours.

Sourcing Channel ROI & Conversion: Compares lead volume against actual F2F show-ups across job boards, walk-ins, and referrals.

Recruiter Performance Scorecard: Matrix view tracking recruiter-level lead volume, F2F appearance rates, and final join conversions with conditional data bars and color scales.

Key Analytical Insights

Call Delay (SLA) Directly Drives Show-Up Rates: Candidates contacted within 0–1 day (Same / Next Day) achieve significantly higher F2F interview attendance compared to leads delayed by 4+ days, proving that recruiter response speed is the primary lever for top-of-funnel conversion.

Primary Rejection Drivers: Lack of relevant real estate experience, communication/skill gaps, and compensation or location mismatches account for the majority of post-screening rejections.

Channel Volume vs. Conversion Trade-off: High-volume job boards generate the largest lead counts, whereas Employee Referrals and targeted sourcing deliver superior F2F show-up and final joining conversion rates.

Recruiter & Market Variance: Side-by-side recruiter scorecards highlight performance gaps in F2F conversion and offer-to-join ratios across Gurgaon, Noida, and Dubai hiring markets.

How to Run This Project

Clone the repository:

git clone https://github.com/<your-username>/talent-funnel-bottleneck-analytics.git
cd talent-funnel-bottleneck-analytics


Run the Jupyter Notebooks:
Open and execute notebooks/01_data_generation_and_cleaning.ipynb followed by notebooks/02_eda_and_bottleneck_analysis.ipynb to generate data/enriched_hiring_tracker.csv.

Explore the Power BI Dashboard:
Open dashboard/talent_funnel_dashboard.pbix in Power BI Desktop. If prompted for data source path updates, go to Transform data > Data source settings, point the CSV source to your local data/enriched_hiring_tracker.csv file, and click Refresh.
