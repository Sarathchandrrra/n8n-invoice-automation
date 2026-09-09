# Invoice Automation with n8n

An invoice processing workflow built with n8n.

The workflow takes invoice PDFs received through Gmail, extracts the invoice information using an AI model, validates the extracted data, checks for existing invoices, and routes the invoice based on the result.

## Workflow

Gmail
↓
Extract PDF
↓
Information Extractor
↓
JavaScript normalization
↓
Validation
↓
Duplicate check
↓
├── Duplicate
│   ├── Label email
│   └── Send alert
│
├── Needs Review
│   ├── Label email
│   └── Send review alert
│
└── New Invoice
    ├── Create database record
    ├── Add to Google Sheets
    └── Label email

## What it does

- Detects invoice emails from Gmail
- Extracts information from invoice PDFs
- Uses an AI model to structure invoice data
- Validates extracted information
- Checks for duplicate invoices
- Stores new invoices
- Adds invoice information to Google Sheets
- Labels processed Gmail messages
- Sends alerts for duplicates and invoices requiring review

## Tech Stack

- n8n
- Gmail
- OpenAI
- Supabase
- Google Sheets
- JavaScript

## Example Use Case

A new invoice arrives in Gmail.

The workflow extracts the PDF, identifies the relevant invoice information, validates it, and checks whether the invoice already exists.

If the invoice is already present, it is marked as a duplicate.

If the invoice is valid and new, the invoice information is stored and added to Google Sheets.

Invoices that cannot be reliably processed are sent for manual review.

## Testing

The workflow was tested using sample invoice PDFs covering:

- New invoices
- Duplicate invoices
- Invalid invoices requiring review

## Setup

1. Import `workflow/invoice-automation.json` into n8n.
2. Configure the required Gmail credentials.
3. Configure the AI model credentials.
4. Configure the Supabase connection.
5. Configure Google Sheets.
6. Update the relevant IDs, fields and filters.
7. Test the workflow with a sample invoice before enabling it.
