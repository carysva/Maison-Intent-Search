# Maison Intent Search

**An Intent-Aware Discovery System for Luxury E-Commerce · BZAN 557 – Text Mining · University of Tennessee, Knoxville**

## Overview
Most e-commerce search matches keywords, not meaning. When a client searches "quiet luxury everyday bag," they're describing an intent, something a boutique associate would understand immediately rather than a product code to look up. Maison Intent Search is a text-mining pipeline built to close that gap, translating natural-language client queries into ranked luxury product recommendations with a transparent "why this" explanation behind each result.

## Data Source
Louis Vuitton's internal product catalog isn't available for third-party use, so this project uses a public Hugging Face Datasets catalog (published under the DBQ namespace as "Louis.Vuitton.Product.prices," with country-specific versions for markets including Singapore, France, and the UK) to emulate one. These are web-scraped Louis Vuitton product listings and prices captured from the brand's site for a specific market, with each row representing a single product: product name, category hierarchy, product/image URLs, price and currency, and a capture timestamp. This demo uses the Singapore dataset.

## Architecture
- Constructs a single searchable document per product (name plus full category path), preserving house-specific vocabulary (bandouliere, monogram, keepall) that generic text cleaning usually strips out
- Vectorizes the catalog and queries with TF-IDF (scikit-learn, unigrams and bigrams), chosen deliberately over heavier embedding models for interpretability, brand safety, and real-time, CPU-only feasibility
- Expands client language before vectorization using a curated luxury-intent synonym map (e.g., "quiet luxury" maps to understated, minimalist, subtle)
- Ranks results by cosine similarity, with a "why this" output surfacing the exact overlapping terms driving each recommendation
- Validates the representation with MiniBatchKMeans clustering (K=8) on the TF-IDF matrix; resulting clusters mapped cleanly onto real LV merchandising categories (Leather Goods & Travel Bags, Ready-to-Wear Tops, Sneakers & Footwear, Outerwear & Jackets, Tailored Pants, Wallets & Small Leather Goods, Eyewear, Belts/Bracelets/Jewelry)

## Why It Matters
A client engaging with a luxury house online should feel the same intelligence and attentiveness as walking into a flagship boutique instead of a search bar returning whatever has the most matching keywords. Better intent-matching also carries operational upside: fewer surprise returns, a lift in customer satisfaction when a recommendation validates a client's choice, and reduced shipping and repackaging waste from mismatched orders.

## Phase II Concept
A predictive-clienteling layer classifying clients into LV-coded archetypes (e.g., "Heritage Vanguard") from purchase history, so a sales associate could anticipate client wants before being asked. The same approach extends Maison-wide: matching exceptional High Jewelry or specialty pieces to the right client before inventory even reaches boutiques.

## Tech Stack
Python, scikit-learn (TF-IDF, cosine similarity, MiniBatchKMeans), Pandas, NumPy, Hugging Face Datasets, Google Colab, Git/GitHub

---
Graduate proof of concept, not affiliated with Louis Vuitton or LVMH.
