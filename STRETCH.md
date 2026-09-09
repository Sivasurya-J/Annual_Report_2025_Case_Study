**Next Immediate Action Items:**



Better section detection --> better deduplication--> model comparison--> richer golden queries --> stronger testing --> prompt refinement





1. **Fine-tune Risk Section Detection** - It identifies the boundaries of the Principal/Main Risks section instead of relying mainly on risk related keywords. This would reduce false positives from financial notes, sustainability sections and other areas which are outside the intended scope

2. **Improve Risk Deduplication -** Risks can appear in multiple sections using slightly different wording. I'd add semantic similarity or rule-based normalisation to identify closely related risks and consolidate them while preserving all relevant source pages



**3. Compare LLM Models -** For different LLM options, I could have collected, risk recall, Precision, Groundedness, Page accuracy, response consistency, Latency and Token usage/cost



Based on the results, select the model that provides the best balance of accuracy, speed, and cost for this use case rather than assuming the largest model is always the best choice.



**4. Expand the Golden Dataset -** The current golden set should be expanded with more diverse queries covering different aspects of the report.



Examples: Principal risks, Cybersecurity risks, Geopolitical risks, Project and operational risks, Financial risks, Risk mitigation, Evidence and source-page questions, Risks mentioned across multiple pages



I would also add negative queries to test whether the system incorrectly treats other material risks as principal risks.



**5. Improved Evaluation -** Extend the evaluation framework to provide a clearer view of extraction quality. The golden dataset would also be reviewed to ensure that exhaustive gold annotations are used when measuring precision.



**6. More Robust Testing -** Add integration and regression tests using different report sections and representative document samples. 



Tests would specifically cover: Risks spanning multiple pages, Duplicate risks, Missing sections, Different wording for the same risk, Incorrect page references, Empty or incomplete LLM responses



**7. Improve Prompt and Output Quality -** Iterate on the extraction prompt based on the evaluation results.



The goal would be to make the model more consistent about: What qualifies as a principal risk, Risk categorisation, Concise descriptions, Mitigation extraction, Evidence selection, Avoiding unsupported conclusions

