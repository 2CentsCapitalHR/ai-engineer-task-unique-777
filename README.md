[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vgbm4cZ0)
# ADGM-Compliant Corporate Agent - Document Review Tool

## Overview

This project provides a comprehensive solution to analyze corporate legal documents in Microsoft Word format (`.docx`), with a focus on verifying compliance with ADGM (Abu Dhabi Global Market) regulations. It automates the identification of document types, checks for mandatory incorporation documents, detects legal red flags, and annotates the documents with comments highlighting issues. The system offers an interactive web interface built with Gradio for easy document upload, analysis, and report generation.

## Features

- **Document Type Identification:** Automatically classifies uploaded `.docx` files according to legal document types relevant to company incorporation.
- **Mandatory Document Checklist:** Checks uploaded documents against a predefined list of mandatory company incorporation documents and reports missing items.
- **Red Flag Detection:** Scans document contents to identify compliance risks and ambiguous clauses using predefined keywords and contextual analysis.
- **In-Document Commenting:** Inserts detailed, color-coded comments directly into the Word documents near the relevant paragraphs to highlight detected issues.
- **Detailed Reporting:** Generates structured JSON reports and markdown summaries outlining findings, severity levels, and recommendations.
- **Downloadable Outputs:** Provides reviewed documents in a ZIP archive and the JSON analysis report for download.
- **Interactive Web UI:** Enables users to upload multiple documents and view instant compliance feedback through an easy-to-use Gradio interface.

## Components

### 1. Document Analysis (`analyze_documents` function)

- Accepts a list of uploaded `.docx` file paths.
- Reads each document into memory and extracts text.
- Identifies document types using text matching and scoring mechanisms.
- Validates presence of mandatory documents for company incorporation.
- Performs detailed red flag detection by analyzing clause content.
- Inserts review comments into documents at relevant locations.
- Compiles per-file and aggregate markdown summaries.
- Creates a ZIP file of annotated documents and a JSON report summarizing all findings.
- Returns markdown outputs, structured data, and file paths for downloads.

### 2. Comment Insertion (`insert_comments_in_docx` function)

- Receives a document in-memory and a list of issues to comment on.
- Locates paragraphs matching issue context or keywords.
- Inserts formatted, italicized, red-colored comment text adjacent to relevant paragraphs.
- Avoids commenting on section headers directly by targeting the following paragraph where appropriate.
- Saves the modified document to a `BytesIO` stream for further processing.

### 3. Section Heading Detection (`find_section_for_keyword` function)

- Scans `.docx` paragraphs for potential section headings using both Word heading styles and regex patterns matching legal numbering schemes.
- Finds the closest preceding heading for a given keyword or text snippet.
- Supports detection of headings formatted as numbered sections, clauses, Roman numerals, and uppercase titles.
- Returns meaningful fallback messages if no heading is found.

### 4. Web Interface (Gradio UI)

- Allows multiple `.docx` file uploads.
- Triggers document analysis on button click.
- Displays compliance checklist, per-file detailed summaries, and structured JSON reports inline.
- Provides download links for reviewed documents (ZIP) and analysis reports (JSON).
- Designed for quick, interactive feedback on legal document compliance.

## Installation and Requirements

- Python 3.7 or higher
- Required Python packages:
  - `python-docx`
  - `gradio`
  - Other dependencies: `io`, `os`, `json`, `tempfile`, `zipfile`, `re`

Install dependencies with pip:

<img src="" width="400">
