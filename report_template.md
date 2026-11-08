# NimbusPay Ticket Triage — Experiment Report

> Complete this report using results from your own Colab run. Do not leave placeholders in the final submission.

## 1. Data audit
Training rows received: **1445**  
Rows retained by first-pass audit: **1350**  
Rows logged for dropping: **95**

The first-pass audit found invalid JSON labels and schema-corrupted labels that used `prio` instead of the required `priority` field. The `prio` values included non-schema values such as `low` and `medium`, so I did not guess a mapping. I excluded those rows and recorded each exclusion in `cleaning_log.csv`.

## 2. Model and method
- Base model: `Qwen/Qwen2.5-0.5B-Instruct`
- Fine-tuning: 4-bit QLoRA with a LoRA adapter
- Runtime: Google Colab T4
- Maximum sequence length: 1024 tokens (review truncation and consider a longer length if memory permits)
- Training objective: predict assistant JSON tokens; prompt tokens are masked from the loss.

## 3. Baseline and experiments

| Run | Change | Dev exact match | Mean field accuracy | Peak GPU memory | Training minutes |
|---|---|---:|---:|---:|---:|
| Base model | No fine-tuning | TO FILL | TO FILL | N/A | N/A |
| Prompt-rules reference | Rules added to prompt (baseline only) | TO FILL | TO FILL | N/A | N/A |
| Experiment 1 | Raw vs cleaned data | TO FILL | TO FILL | TO FILL | TO FILL |
| Experiment 2 | LoRA vs QLoRA | TO FILL | TO FILL | TO FILL | TO FILL |
| Experiment 3 | Change LoRA rank / learning rate / epochs | TO FILL | TO FILL | TO FILL | TO FILL |
| Experiment 4 | Your own controlled change | TO FILL | TO FILL | TO FILL | TO FILL |

Only report experiments that you actually ran. Change one variable at a time.

## 4. Error analysis
After evaluating the best adapter on dev, list at least 10 wrong predictions. For each, include the ticket ID, incorrect field, expected value, predicted value, and likely reason.

| Ticket ID | Field | Expected | Predicted | Why it failed |
|---|---|---|---|---|
| TO FILL | TO FILL | TO FILL | TO FILL | TO FILL |

## 5. Next steps
Describe one or two improvements you would test with another week, based on the observed errors.

## 6. AI-tool disclosure
I used ChatGPT to help structure the starter notebook, explain the assignment requirements, and review the workflow. I inspected the code, ran the experiments, checked the outputs, and am responsible for the submitted results.
