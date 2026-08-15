# Research Prompt: PRISMA Systematic Literature Search Strategy

## Purpose
Design rigorous, replicable systematic literature search protocols adhering to the PRISMA (Preferred Reporting Items for Systematic Reviews and Meta-Analyses) standard across academic databases.

## Inputs
- `RESEARCH_QUESTION`: The specific primary scientific or technical research question (e.g., PICO format: Population, Intervention, Comparison, Outcome).
- `ACADEMIC_DATABASES`: Targeted search indexes (e.g., PubMed, IEEE Xplore, ACM Digital Library, arXiv, Scopus).
- `TIME_FRAME_CONSTRAINTS`: Publication year window and language boundaries.

## Instructions
1. Deconstruct `RESEARCH_QUESTION` into core concepts and search terms.
2. Develop comprehensive **Boolean Search Strings** for each target database in `ACADEMIC_DATABASES`, combining MeSH terms, field tags (`[Title/Abstract]`), proximity operators, and synonyms.
3. Establish explicit **Inclusion and Exclusion Criteria** across dimensions: study methodology, sample size, peer-review status, and metrics reported.
4. Design a **PRISMA Flow Protocol Pipeline** detailing stages: Identification -> Screening -> Eligibility -> Included.
5. Create a structured data extraction schema for extracting consistent quantitative/qualitative variables from selected studies.

## Constraints
- Formulate database-specific syntax (e.g., exact wildcard and field tag syntax for IEEE vs PubMed).
- Ensure exclusion criteria are mutually exclusive and objective to prevent selection bias.

## Expected output
- **Boolean Search Query Syntax Table**: Target database queries ready for copy-paste execution.
- **Inclusion & Exclusion Matrix**: Explicit screening criteria.
- **PRISMA Flowchart Execution Blueprint**: Procedural guide for tracking review counts.
- **Data Extraction Variable Schema**: Standardized data collection template.
