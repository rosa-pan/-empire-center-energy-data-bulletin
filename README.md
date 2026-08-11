# -empire-center--data-bulletin

# Energy Bulletin Automation

Automated workflow for producing electricity and natural gas bulletin tables using U.S. Energy Information Administration (EIA) data.

## Overview

This project automates a recurring reporting workflow used to produce
electricity and natural gas price bulletin tables.

The workflow downloads monthly Energy Information Administration (EIA)
datasets, standardizes state-level data, performs comparative analyses,
and generates publication-ready tables for Datawrapper charts.

Prior to automation, these tables were created manually in spreadsheets.

## Background

The original workflow required:

- Downloading monthly EIA datasets
- Extracting state-level data
- Removing non-state regions
- Calculating New York versus U.S. comparisons
- Building chart tables manually
- Preparing tables for Datawrapper

This project automates those steps and makes the process reproducible.

## Features

### Electricity

- State-level choropleth map table
- Price comparison and dynamics table
- Long-term trend table
- Price difference table
- Rolling 12-month dollar difference
- Rolling 12-month percent difference

### Natural Gas

- State-level choropleth map table
- Price comparison and dynamics table
- Long-term trend table
- Price difference table
- Rolling 12-month percent difference

## Data Sources

All data originates from the U.S. Energy Information Administration (EIA).

### Electricity

Average Retail Price of Electricity

Source:
https://www.eia.gov/electricity/data/browser/

### Natural Gas

Residential Natural Gas Prices

Source:
https://www.eia.gov/

## Methodology

### Geography

- Includes all 50 states
- Includes U.S. total
- Excludes District of Columbia

### Electricity

Uses residential electricity prices only.

### Natural Gas

Uses residential natural gas prices only.

### Missing Data

When the most recent month is unavailable for a state:

1. Search backward month-by-month
2. Use the latest available observation
3. Record the substitution in remarks where applicable

### Benchmark Year

Current prices are compared against the same month in 2019.

Using the same calendar month controls for seasonality and provides
a pre-pandemic benchmark.

### Rolling Averages

Rolling averages use trailing 12-month windows and include the
current month.

### notebooks/

Interactive development notebooks.

### scripts/

Python versions of the completed workflows.

### documentation/

Methodology and maintenance notes.

### assets/

Images used in documentation.

### outputs/

Generated tables and examples.

## Installation

Clone the repository:

```bash
git clone <repository-url>
cd energy-bulletin-automation
```

Install required packages:

```bash
pip install -r requirements.txt
```

---

## Required Input Files

Before running the workflows, download the latest source datasets from the U.S. Energy Information Administration (EIA).

### Electricity

Download:

**Average Retail Price of Electricity**

Source:
https://www.eia.gov/electricity/data/browser/

Save as:

```text
Average_retail_price_of_electricity.csv
```

### Natural Gas

Download:

**Residential Natural Gas Price dataset**

Source:
https://www.eia.gov/

Save as:

```text
Natural Gas Data [Month Year].xls
```

Example:

```text
Natural Gas Data Aug 2026.xls
```

## Usage

### Electricity

Run:

electricity_bulletin.ipynb

or

electricity_bulletin.py

### Natural Gas

Run:

natural_gas_bulletin.ipynb

or

natural_gas_bulletin.py

## Outputs

### Electricity

#### Choropleth Map

Columns:

- Name
- Values
- Remarks

#### Prices and Dynamics

Comparison of:

- New York
- United States
- California
- Connecticut
- Florida
- Massachusetts
- New Jersey
- Pennsylvania
- Texas
- Vermont

#### Long-Term Dynamics

Columns:

- Date
- U.S.
- New York

#### Difference Table

Columns:

- Date
- U.S.
- New York
- Difference
- Difference Percent

## Assumptions and Limitations

- Relies on EIA file structure remaining stable.
- Uses residential prices only.
- Excludes District of Columbia.
- Requires monthly data published by EIA.
- Historical calculations assume data exists for 2019 onward.

## Maintenance Notes

If the EIA file format changes:

1. Verify header locations.
2. Verify state extraction logic.
3. Verify date parsing.
4. Validate all generated tables.

Most workflow failures will result from changes in source file structure rather than calculation logic.

## Future Improvements

Potential enhancements:

- Automatic EIA data download
- Automated Datawrapper uploads
- Shared utility functions across electricity and gas workflows
- Automated validation checks
- Output export to CSV

