# Data Quality Automation with n8n

An automated data quality workflow built with n8n and Google Sheets.

The workflow validates transaction data, identifies data quality issues,
separates clean and problematic records, and maintains a review log.

## Overview

This project demonstrates how workflow automation can be used to perform
basic data quality checks without manually reviewing every transaction.

### Workflow

Google Sheets
→ Normalize Data
→ Data Quality Check
→ Quality Status
→ Clean / Review
→ Logging

## Data Quality Checks

The workflow currently checks for:

- Missing required fields
- Invalid quantity
- Invalid category
- Duplicate transaction IDs
- Multiple issues in a single transaction

## Key Features

- Automated processing through Google Sheets trigger
- Data normalization
- Rule-based data quality validation
- Separate clean and review paths
- Review detail logging
- Log key for duplicate prevention
- Supports repeated workflow execution without duplicating the same issue

## Example

Input:

| Transaction ID | Customer | Product | Quantity |
|---|---|---|---:|
| TRX-1187 | Andi Saputra | Keyboard | 1 |

If the date is missing:

```text
Status: NEEDS_REVIEW
Issue: Missing Date
Log Key: TRX-1187|Missing Date
