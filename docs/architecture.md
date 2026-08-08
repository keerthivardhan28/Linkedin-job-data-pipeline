# Pipeline Architecture

## Overview

This project implements an automated job data pipeline using n8n, REST APIs, JavaScript, and Google Sheets.

## Data Flow

| Step | Component | Description |
|---|---|---|
| 1 | Schedule Trigger | Automatically starts the pipeline |
| 2 | HTTP Request | Initiates the job data extraction process |
| 3 | Wait / Rate Control | Controls API request timing |
| 4 | HTTP Request 1 | Checks the API job run status |
| 5 | HTTP Request 2 | Retrieves the extracted job dataset |
| 6 | JavaScript Transformation | Standardizes and maps job attributes |
| 7 | Google Sheets Lookup | Reads existing job records |
| 8 | Job ID Deduplication | Checks whether the Job ID already exists |
| 9 | Conditional Routing | Routes duplicate and new records |
| 10 | Google Sheets | Skips duplicates and appends new job records |

## Pipeline Components

### 1. Data Ingestion
Job posting data is extracted from an external REST API through the n8n workflow.

### 2. Data Transformation
JavaScript is used to standardize and map job attributes such as title, company, location, experience, work mode, salary, and Job ID.

### 3. Data Validation
Job attributes are validated and standardized before loading into the target dataset.

### 4. Deduplication
Job ID is used as the unique identifier. Existing Job IDs are skipped to prevent duplicate records.

### 5. Incremental Loading
Only new job records are appended to Google Sheets, preventing duplicate records during subsequent pipeline runs.

### 6. Data Storage
Google Sheets is used as the target data store for processed job posting records.

## Technologies

- n8n
- REST API
- JavaScript
- Google Sheets
- JSON
- GitHub
