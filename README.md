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
