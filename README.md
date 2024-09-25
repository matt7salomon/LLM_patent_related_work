# LLM_patent_related_work


# Patent Novelty and Obviousness Checking with Multiple Data Sources

## Dataset and API Information:
This version allows you to choose between various patent data sources:
- **Lens.org**: API-based patent search, requires API key.
- **USPTO Bulk Data**: Public patent data from the US Patent Office, no key required.
- **Google Patents**: Requires a Google Cloud Project for BigQuery.
- **WIPO Patentscope**: Global patent search, requires API key.

## Patent Search Function
The `search_patents()` function selects the appropriate data source based on the flag set at the beginning of the code.

## Prior Art Retrieval
The `retrieve_prior_art()` function uses the selected API to pull related patents for comparison.

## Similarity Calculation using LLMs
We use a pre-trained Hugging Face model for semantic similarity and calculate cosine similarity using TF-IDF vectors.

## Novelty Check Pipeline
The `patent_novelty_check()` function brings it all together, helping us check the novelty of a new patent claim against prior art from different data sources.


# Patent claim generator code:

## Explanation:

**Function analyze_patent_claims_for_suggestions:** 
This function takes the extracted patent claims and uses GPT-4 to suggest ways to broaden or narrow the claims.
It prompts GPT-4 to act as a patent expert and provides suggestions for improving the claims.

**Function upload_and_analyze_patent_claims:**
This function simulates reading a patent document (in this case, a .txt file with the claims), and it passes the claims to GPT-4 for analysis.
The uploaded file should contain claims in plain text for GPT-4 to analyze.

**Pipeline patent_claim_suggestion_pipeline:**
This pipeline coordinates the process by uploading the claims, analyzing them, and returning suggestions.

### Steps:
Upload Patent Claims: The patent claims can be uploaded as a .txt file. You can modify this to handle other formats (e.g., PDFs) if needed.
Analyze with GPT-4: GPT-4 will suggest ways to either broaden or narrow the claims to improve the likelihood of patent approval and the scope of protection.

### Example Workflow:
Place the patent claims in a text file (e.g., patent_claims.txt).
Run the patent_claim_suggestion_pipeline(file_path) with the path to the file.
GPT-4 will analyze the claims and suggest improvements based on its understanding of the claims and potential strategies for approval.
