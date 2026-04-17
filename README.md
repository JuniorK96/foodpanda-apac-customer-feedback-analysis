# Foodpanda APAC Customer Feedback Analysis 2024–2026

End-to-end analysis of 4.6 million Foodpanda customer reviews across 11 APAC markets, surfacing market-level experience patterns and specific service-quality gaps through quantitative and keyword-based analysis.

**[→ View the interactive dashboard on Tableau Public](https://public.tableau.com/views/FoodpandaAPACCustomerFeedbackAnalysis2024-2026/Story1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link)**

---

## Key findings

**The customer pain point is restaurant-side, not delivery-side.** Riders are rated 4.78 on average; food is rated 3.33 — a consistent 1.45-point gap across all 11 markets. Delivery execution is not the problem.

**Customer sentiment is polarised, not average.** 26% of reviews are 1-star and 45% are 5-star, with only 28% in the 2–4 star middle. A J-shaped distribution that makes the average rating misleading — the 1-star rate should be tracked as its own KPI.

**Small portions are the #1 complaint APAC-wide.** Appears as "small" in Singapore (2,614), Philippines (2,775), Malaysia (4,202) and as "kecik" in Malaysia (4,117). The most consistent complaint across every market analysed.

**Malaysia holds the strongest customer loyalty signal in APAC** — "terbaik" (26,638), "repeat" (23,830), "terima kasih" (17,440+). But also the strongest disappointment signal — "kecewa" (4,521), "disappointed" (3,980). A base worth protecting through a recovery flow before silent churn.

**Taiwan is the APAC top performer (3.85 average) and is being divested to Grab in H2 2026.** There is a window to document what works there before the transition.

Full set of findings and recommendations on the [Recommendations dashboard](https://public.tableau.com/shared/D4W6GY8CS?:display_count=n&:origin=viz_share_link).

---

## Business question

*Which APAC markets show signs of customer experience strain, and what specific service dimensions (food, rider, restaurant) are driving sentiment in each?*

---

## Methodology

- **Sentiment** is derived from explicit star ratings (1–2 = Negative, 3 = Neutral, 4–5 = Positive) rather than NLP scoring. Star ratings are language-agnostic and provided directly by customers — more reliable than NLP on a multilingual dataset.
- **Keyword analysis** uses frequency ranking within sentiment groups, with `share_of_voice` to normalise for slice-size differences. English and Malay keywords were validated by the analyst (native Malaysian speaker).
- **Language detection** via `langdetect`, with a corrected misclassification of Traditional Chinese as Korean (~538k reviews) identified through sampling and remapped to `zh-tw`.
- **Singapore region assignment** combined postal-code regex extraction with OneMap API geocoding, reaching ~60% coverage. Uncovered addresses are labelled "Unknown" rather than imputed.

---

## Tools
 
- **Python** — pandas, langdetect, jieba, regex
- **Visualisation** — Tableau Public
- **Data source** — Foodpanda APAC restaurant and review datasets by [bwandowando on Kaggle](https://www.kaggle.com/bwandowando), covering 11 markets with 2025 and 2026 versioned snapshots. Individual datasets used:
  - [Malaysia](https://www.kaggle.com/datasets/bwandowando/malaysian-cities-food-panda-resto-reviews)
  - [Singapore](https://www.kaggle.com/datasets/bwandowando/food-panda-resto-reviews)
  - [Philippines](https://www.kaggle.com/datasets/bwandowando/food-panda-restaurant-reviews)
  - [Taiwan](https://www.kaggle.com/datasets/bwandowando/taiwan-food-panda-restaurant-reviews)
  - [Hong Kong](https://www.kaggle.com/datasets/bwandowando/hongkong-food-panda-restaurant-reviews)
  - [Bangladesh](https://www.kaggle.com/datasets/bwandowando/bangladesh-cities-food-panda-resto-reviews)
  - [Pakistan](https://www.kaggle.com/datasets/bwandowando/pakistan-cities-food-panda-resto-reviews)
  - [Thailand](https://www.kaggle.com/datasets/bwandowando/thailand-cities-food-panda-resto-reviews)
  - [Cambodia](https://www.kaggle.com/datasets/bwandowando/cambodian-food-panda-resto-reviews)
  - [Laos](https://www.kaggle.com/datasets/bwandowando/laos-food-panda-restaurant-reviews)
  - [Myanmar](https://www.kaggle.com/datasets/bwandowando/myanmar-food-panda-restaurant-reviews)
    
---

## Acknowledged limitations

- **Singapore region coverage** sits at ~60%; the remaining 40% labelled "Unknown".
- **Keyword analysis is unigram-only** — negation is not captured (e.g. "tidak sedap" splits into separate tokens).
- **Chinese keywords** (Taiwan, Hong Kong) are shown for exploratory purposes — native speaker validation recommended before operational use.
- **Six markets excluded from keyword analysis** (Pakistan, Bangladesh, Thailand, Myanmar, Cambodia, Laos) due to language tool limitations on this Python environment.
- **Malay NLP** (Malaya library) was explored but not implemented due to Python 3.14 compatibility constraints.

---

## Repository contents

- `foodpanda_APAC_analysis.ipynb` — full pipeline: data loading, deduplication, geocoding, language detection, feature engineering, keyword extraction
- `requirements.txt` — Python dependencies
- Data files are not included in this repository. Source data is available on Kaggle (linked above). Final analytical outputs (`foodpanda_APAC_final.csv`, `foodpanda_keywords.csv`) are generated by the notebook.

---

## About

Built by **Junior bin Khalit** — data analyst based in Singapore, transitioning from operations into analytics.

[LinkedIn](https://linkedin.com/in/junior-k-473700155) · [GitHub](https://github.com/JuniorK96) · [Tableau Public](https://public.tableau.com/app/profile/junior.khalit)
