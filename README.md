# Data Quality Automation with n8n

An automated sales data quality workflow built with n8n and Google Sheets.

The workflow validates transaction data, identifies data quality issues,
separates clean and problematic records, maintains an issue history,
and generates an AI-assisted data quality analysis with email notification.

## Overview

This project demonstrates how workflow automation can be used to perform
repeatable data quality checks without manually reviewing every transaction.

The workflow combines:

- Rule-based data validation
- Issue tracking and resolution history
- Automated reporting
- AI-assisted data quality analysis
- Email notification

### Workflow

Google Sheets
→ Normalize Data
→ Data Quality Check
→ Quality Status
→ Clean / Review
→ Final Report
→ Notification Condition
→ AI Analysis
→ Email Notification

At the same time, clean and review records are logged separately
for traceability and follow-up.

## Data Quality Checks

The workflow currently checks for:

- Missing required fields
- Invalid quantity
- Quantity less than or equal to zero
- Invalid category
- Duplicate transaction IDs
- Multiple issues in a single transaction

## Key Features

### Data Validation

- Automated processing of transaction data from Google Sheets
- Data normalization before validation
- Rule-based data quality checks
- Classification of records into `CLEAN` and `NEEDS_REVIEW`

### Issue Tracking

- Review issues are logged separately
- Each issue contains a transaction reference and issue description
- Issue history uses a `Log Key` to prevent duplicate logging
- Supports repeated workflow execution without duplicating the same issue
- Resolved issues remain available as historical records

### Automated Reporting

The workflow generates a final quality report containing:

- Overall report status
- Total records
- Clean records
- Records requiring review
- Issue summary by type

Example:

```json
{
  "report_status": "NEEDS_REVIEW",
  "total_records": 207,
  "clean_records": 167,
  "review_records": 40,
  "issue_summary": {
    "Missing Customer": 24,
    "Missing Quantity": 4,
    "Missing Unit Price": 3
  }
}
