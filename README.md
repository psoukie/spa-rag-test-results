# SPA-RAG Evaluation Dataset

This repository accompanies the LocWorld microtalk **_SPA-RAG: A Smarter Way to Validate and Fix Terminology in AI Workflows_**.

It provides the data used to evaluate **SPA-RAG**, a _special-purpose algorithm RAG_ that improves terminology QA efficiency by invoking large language models only when they add value.

## What This Repository Contains

|File / Folder|Description|
|---|---|
|[auto-generated_glossary.csv](auto-generated_glossary.csv)|Automatically extracted bilingual glossary (English–German) from _The Wonderful Wizard of Oz_.|
|[MT_fixed_with_RAG.json](MT_fixed_with_RAG.json)|Raw baseline RAG output (segment judgments, corrections, token stats).|
|[MT_fixed_with_SPA.json](MT_fixed_with_SPA.json)|Raw SPA-RAG output under identical conditions.|
|[RAG_SPA-RAG_analysis.csv](RAG_SPA-RAG_analysis.csv)|Combined table comparing both methods: source/target segments, judgments, corrections, and retrieved entries.|
|[METHODOLOGY.md](METHODOLOGY.md) _(planned)_|Description of test setup, glossary generation, RAG setups, and metrics. (Coming this week.)|
|`notebooks/` _(planned)_|Public, cleaned-up scripts to reproduce the baseline RAG workflow (In coming weeks).|

---

## Summary of Methodology

- **Source Text**: Public-domain _The Wonderful Wizard of Oz_ (English).
- **Glossary**: Generated automatically from reference human translation into German.
- **Test Translation**: Machine-translated (NMT) version of the English text to generate realistic inconsistencies.
- **Evaluation**:
    - _Baseline RAG_: OpenAI Text Embedding 3 applied to source terms, Chroma DB, retrieval injected into prompt for GPT5-mini for each segment.
    - _SPA-RAG_: Inflected forms generated with LLM, custom deterministic prefilter to detect longest non-overlapping terms, and skip obviously compliant segments; LLM only for uncertain cases.
        
- **Metrics Collected**: adherence judgment, correction, retrieved entries, token counts.
- **Key Finding**: ~80 % fewer LLM calls, 3–5× fewer tokens, with ~81 % agreement between methods.

See [METHODOLOGY.md](https://chatgpt.com/c/METHODOLOGY.md) for full details. (Coming soon.)

---

## Code Availability

The deterministic matching component of SPA-RAG is proprietary and excluded.

A cleaned-up public version of the **baseline RAG evaluation code** (data loading, retrieval, LLM prompting, metrics) will be added here in the coming weeks.

---

## License

Data and documentation © 2025 Pavel Soukenik.  
Released under the **MIT License**.  
Proprietary components remain excluded.

---

## Citation

> Pavel Soukenik. _SPA-RAG: A Special-Purpose Algorithm for Efficient Terminology Validation in AI Workflows._  
> LocWorld Microtalk 2025.
