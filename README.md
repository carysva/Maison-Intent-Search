# Maison Intent Search (Intent-Aware Luxury Product Discovery)

## About
A text-mining-based recommendation prototype that translates natural-language intent into ranked luxury product recommendations. The system combines TF-IDF representations, synonym-aware query expansion, cosine-similarity ranking, and explainable matching.

## Business Problem
Keyword search fails to capture luxury client intent (use case, occasion, vibe, and styling constraints). The goal is to improve e-commerce discovery by:
- Understanding intent-driven queries (e.g., "quiet luxury for work", "travel-friendly shoes that pack easily")
- Returning results that feel relevant even when users do not know exact product names or structured filter values
- Providing transparency into why recommendations match a query

## What I Built
- Query normalization and intent expansion:
  - Lowercasing, punctuation/number cleanup, stopword removal
  - Optional synonym expansion using a curated luxury-specific dictionary
- Explainable similarity-based ranking:
  - Product documents are built by concatenating product text fields (name + category hierarchy, plus merchandising tags)
  - TF-IDF (unigrams + bigrams) transforms query and product documents into a shared vector space
  - Cosine similarity scores query-product alignment
  - Top-k recommendations are shown with an overlap-style explanation to highlight high-weight terms
- Optional structure for navigation:
  - Clustering (e.g., KMeans) groups products into coarse themes ("intent shelves") aligned with common merchandising categories

## Included Files
- `Carys_Van_Atta_MaisonIntentSearch.ipynb` (Maison Intent Search prototype code)
- `Carys_Van_Atta_MaisonIntentSearch_ (2).docx` (project narrative + methodology)

## Method Summary (BA-friendly)
- Transform unstructured intent text into measurable features (TF-IDF)
- Use similarity search to rank candidates
- Add explainability so the output supports user trust and sales-associate style guidance

## Portfolio Notes
This project demonstrates applied text mining and explainable ranking for a real business context (luxury clienteling and discovery), emphasizing interpretability rather than black-box performance alone.

