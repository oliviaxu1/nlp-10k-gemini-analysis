# NLP Analysis of AI Signals in 10-K Filings with Gemini

This project applies natural language processing and Gemini-based information extraction to identify AI-related risks, opportunities, investment disclosures, and high-level sentiment in ten US companies' Form 10-K filings. The original implementation used Gemini 2.0 Flash.

The project originated in graduate coursework for **FNCE90084 Applications of Machine Learning in Finance at the University of Melbourne**. This repository is a public portfolio adaptation: course instructions, grading material, teaching templates, and course-provided data have been removed.

![Project workflow](assets/project-overview.svg)

## Methodological focus

- **Document NLP:** converts heterogeneous filing HTML into normalised text with Beautiful Soup and regular expressions.
- **Prompt specification:** defines task scope, semantic categories, null handling, numeric units, and a predictable response structure.
- **Information extraction:** maps unstructured model responses into risk, opportunity, investment, and numeric-value fields.
- **Corpus-level inference:** applies a consistent extraction function across ten long-form financial documents.
- **Downstream classification:** transforms extracted representations into constrained firm-level sentiment labels.
- **Research evaluation:** identifies limitations involving context length, hallucination, evidence grounding, schema robustness, and cross-company comparability.

The empirical outputs demonstrate the pipeline, but they are not the main contribution of this portfolio project. The emphasis is on NLP research design and on how an exploratory LLM workflow could be developed into a reproducible, evidence-grounded information-extraction system.

## Repository structure

```text
nlp-10k-gemini-analysis/
├── assets/
│   └── project-overview.svg
├── data/
│   └── README.md
├── .env.example
├── .gitignore
├── README.md
├── nlp_10k_gemini_analysis.ipynb
└── requirements.txt
```

Generated files such as `10k_extracted_info.csv` and `AI_sentiment_ranking.txt` are excluded from version control and can be recreated locally by running the notebook with authorised source filings.

## Data

The original workflow used ten 10-K HTML files supplied within the University of Melbourne course environment. These files are not uploaded, copied, or embedded here.

To reproduce the workflow, obtain the corresponding public filings from SEC EDGAR and save them locally as:

```text
data/NVDA_latest_10K.html
data/GOOGL_latest_10K.html
data/MSFT_latest_10K.html
data/AMZN_latest_10K.html
data/META_latest_10K.html
data/TSLA_latest_10K.html
data/IBM_latest_10K.html
data/INTC_latest_10K.html
data/CRM_latest_10K.html
data/ORCL_latest_10K.html
```

Because filing dates and contents can differ from the original course dataset, a new run may not reproduce the preserved outputs exactly.

## Setup

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
export GOOGLE_GEMINI_API_KEY="your-key-here"
jupyter notebook nlp_10k_gemini_analysis.ipynb
```

Never commit a real API key.

## Limitations

- Full 10-K filings can strain model context windows.
- Generative-model outputs may vary or contain unsupported claims.
- Reported capital expenditure and R&D are not necessarily AI-only investment.
- Extracted investment values are not automatically comparable across companies.
- A production version should use chunk-level retrieval, evidence quotations, schema-constrained output, and programmatic source validation.

## Responsible use

This repository is an educational portfolio artifact, not investment advice. Verify every extracted claim against the original SEC filing before using it in research or decision-making.
