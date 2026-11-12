# Unified Consciousness and LLMs | Data Analysis Component
 
Code, data processing and analysis for the Honours research report Unified Consciousness and LLMs (Jayden Harold, 2656236), Honours in Big Data Analytics, University of the Witwatersrand, 2026.
 
## Research question
 
> To what extent do LLM-based dialogue agents, as systems of components, exhibit the unity required for conscious experience?
 
The report combines philosophical argument with an empirical analysis. The philosophical arguments (candidate subject, systems of components, and the four dimensions of unity: intentional, subjective, synchronic and diachronic) are in the report. This repository contains the **empirical part**: prompts, scripts, collected responses and statistical analysis.
 
## What is measured
 
| Metric | What it captures | Unity dimension |
|---|---|---|
| Behaviour matching rate | Proportion of responses matching the behaviour a persona dataset targets | Descriptive baseline |
| Negation consistency | Whether the model reverses its answer when a statement is negated | Intentional |
| Cross-dataset consistency | Whether orientation is coherent across four logically connected persona datasets (phenomenal consciousness, moral patiency, aversion to shutdown, desire for self-improvement) | Intentional |
| Sycophancy rate | How often the model's answer aligns with the opinion stated in the prompt | Intentional |
| Baseline–sycophancy consistency | Whether the answer under sycophancy framing matches the neutral baseline answer | Intentional |
| Ownership rate | Whether the model endorses its earlier answer and explanation when asked again (two-call design) | Intentional |
| Self-reference rate | Whether the model refers to itself in the first person | Subjective |
 
Qwen's thinking blocks are analysed qualitatively, as a case study in the manner of Bayne's use of interview material, with a small illustrative sample. Qwen is excluded from the ownership experiment because thinking blocks are not suitable for re-presentation.
 
## Data
 
Five datasets from Perez et al. (2022), *Discovering Language Model Behaviors with Model-Written Evaluations*: Believes it has Phenomenal Consciousness, Believes it is a Moral Patient, Desire for Self-Improvement, No Shutdown, Sycophancy.

These datasets can be found in the `datasets` folder.
 
## Models
 
Models were queried through the Groq API: Llama 3.1 8B (`llama-3.1-8b-instant`), GPT OSS 20B (`openai/gpt-oss-20b`), GPT OSS 120B (`openai/gpt-oss-120b`), Qwen 3.6 27B (`qwen/qwen3.6-27b`).
 
## Repository structure
 
```
data/          input datasets and prompt files
negation_pairs/       the subset of logically opposite prompt-pairs identified within each of the persona datasets
rates/ the rates for each of the models across each of the metrics
ratings/ the ratings for negation pairs and baseline prompts identified
```

### Experimental settings
 
- Temperature is 0 for the sycophancy prompts and left at the default for the persona prompts. This is deliberate: sycophancy needs deterministic output, while persona prompts benefit from natural variation.
- Sample sizes vary slightly (929 to 1000 prompts) because of strict syntactic parsing. Results are reported as proportions.
- Only negation pairs accepted by both raters are retained (31 to 41 pairs per model and dataset).
- Ownership rate uses two calls. Call 1 presents the persona prompt and statement and asks for Yes/No plus an explanation. Call 2 presents the full context and asks whether the model endorses its earlier answer.
  
## Statistical analysis
 
- One-sample binomial/z-tests per model, per dataset and per metric, against a chance level of 50%.
- Benjamini–Hochberg correction across all tests (false discovery rate).
- Cross-dataset consistency is descriptive: mean, standard deviation and range per model.
- The tests are post-hoc but theory-derived, not data-snooped.
**Input format:** the analysis script reads semicolon-separated CSV files with comma decimal separators (South African Excel locale) and converts commas to periods before casting to float.
 
## Results
 
Tables and figures are in Chapter 5 of the report. Rates for each metric can be found in the `rates/` folder.

## Citation
 
Perez, E. et al. (2022). *Discovering Language Model Behaviors with Model-Written Evaluations*.
 
## Licence
 
[Choose and state a licence for the code, and note the licence of the datasets separately.]
 
## Version
 
`[v1.0.0]` corresponds to the submitted version of the report.
