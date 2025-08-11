[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/vgbm4cZ0)
# Section Heading Finder for Word Documents

## Overview
This Python function helps identify the relevant section heading in a Word document (`.docx`) where a specific keyword or exact text appears. It is useful for parsing structured documents like contracts, reports, or manuals to locate contextual headings.

## Features
- Detects section headings using both paragraph styles (e.g., Word's built-in Heading styles) and regex patterns matching common heading formats.
- Supports multiple heading formats including numbered sections, clauses, Roman numerals, uppercase titles, and sub-headings.
- Finds the closest preceding heading to the paragraph containing the keyword or matched text.
- Returns meaningful fallback messages if no match or heading is found.

## How It Works
1. Extract all potential section headings from the document using regex patterns and heading styles.
2. Search paragraphs for the given `match_text` or fallback `keyword`.
3. From the found paragraph, move upward to find the nearest preceding heading.
4. Return the heading text or a default message if none found.

## Usage
- Requires the `python-docx` library to read `.docx` files.
- Call `find_section_for_keyword(doc, keyword, match_text)` with a loaded document and search terms.
- Example:
  ```python
  import docx
  doc = docx.Document("document.docx")
  section = find_section_for_keyword(doc, keyword="Confidentiality", match_text="")
  print(section)
2.insert_comments_in_docx Function:
This function inserts review comments into a DOCX document based on a list of issues by locating matching paragraphs through keywords or context. It appends formatted, colored comment text to the appropriate paragraphs, avoiding headings when possible. The updated document is saved into a BytesIO object and returned for further use. The function handles errors gracefully and ensures no duplicate comments are added.

3.Mandatory Documents List
Defines a dictionary MANDATORY_DOCS mapping the key "Company Incorporation" to a list of essential documents required for company formation. These include foundational legal and administrative documents such as Articles of Association, Memorandum of Association, and various resolution templates. This structured list can be used for validation, checklist generation, or document management in corporate workflows.

4..analyze_documents Function:
This function processes uploaded .docx files to identify document types, check mandatory documents for company incorporation, detect legal red flags, and generate detailed issue reports. It returns markdown summaries, structured JSON data, and prepares reviewed documents zipped for download. The function handles errors gracefully, skips unreadable files, and annotates documents with comments on detected issues. Temporary files for ZIP and JSON outputs are created and returned for downstream use.

5.Gradio UI for Document Review:
This Gradio interface allows users to upload multiple .docx legal documents for compliance analysis. Upon clicking "Analyze Documents," it calls the analyze_documents function and displays a checklist summary, per-file detailed markdown, and a structured JSON report. Users can download reviewed documents as a ZIP file and the full analysis report as a JSON file. The interface is designed for easy, interactive feedback on uploaded corporate legal documents.
