# Dataset and measure notes

## Source

[Hallucination Reduction in RAG-Based LLMs — Kaggle](https://www.kaggle.com/datasets/sohaibdevv/hallucination-reduction-in-rag-based-llms)

The Power BI model contains 6,000 samples from this dataset. The repository package includes the PBIX report; it does not add a separate raw-data export.

## Fields in the model

| Field | Role in this report |
| --- | --- |
| sample_id | Sample identifier; counted to determine the number of observations. |
| domain | Knowledge-domain category used to compare rates. |
| hallucination_label_without_rag | Dataset label for whether the response without RAG is marked as a hallucination (0/1). |
| hallucination_label_with_rag | Dataset label for whether the response with RAG is marked as a hallucination (0/1); the residual page filters this field to 1. |
| hallucination_type | Categorical label used to group residual hallucinations. The report shows unsupported_claim, contradiction, factual_error, and partially_correct. |
| source_support_label | Source-support category used on the residual page: not_supported or partially_supported. |
| question | Question associated with the sample. |
| retrieved_context | Retrieved context associated with the sample. |
| ground_truth_answer | Ground-truth answer field supplied with the sample. |
| llm_response_without_rag | Model response without RAG. |
| llm_response_with_rag | Model response with RAG. |
| context_relevance_score | Source-provided evaluation score. The scale and threshold are not redefined in this report. |
| factual_consistency_score | Source-provided evaluation score. The scale and threshold are not redefined in this report. |
| final_target_label | Target-label field supplied with the source data; it is not used in the displayed measures. |

## Measures and filters

- **Hallucination Rate Without RAG:** share of counted samples with hallucination_label_without_rag = 1.
- **Hallucination Rate With RAG:** share of counted samples with hallucination_label_with_rag = 1.
- **Reduction (percentage points):** rate without RAG minus rate with RAG. The overall result displayed is 49.9 percentage points (57.6% − 7.7%).
- **Domain view:** applies the same rate measures within each domain. Sample counts differ by domain; the overview page includes a sample-count tooltip.
- **Residual type/source-support view:** filters hallucination_label_with_rag to 1, then counts samples by hallucination_type and source_support_label. The filtered total is 463.

## Residual counts

| Hallucination type | Not supported | Partially supported | Total |
| --- | ---: | ---: | ---: |
| unsupported_claim | 62 | 60 | 122 |
| contradiction | 49 | 66 | 115 |
| factual_error | 57 | 56 | 113 |
| partially_correct | 59 | 54 | 113 |
| **Total** | **227** | **236** | **463** |

These are descriptive counts from the dataset labels. They do not establish why an output received a label, and the report does not present a causal or universal claim about RAG performance.
