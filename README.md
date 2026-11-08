# NimbusPay Ticket Triage — simple fine-tuning project

This repository is a **starter implementation** for the VIMA3YA take-home assignment. It is intentionally small and organized so you can explain each step.

## What it does
A small instruction-tuned language model reads a support ticket and generates the required 8-field JSON triage record. The notebook uses QLoRA (4-bit loading + LoRA adapter) on a free Google Colab T4.

## Files
- `notebook.ipynb` — complete Colab workflow: inspect data, clean noisy labels, load model, train, evaluate, and generate test predictions.
- `cleaning_log.csv` — audit log for rows excluded by the initial conservative label audit.
- `report_template.md` — fill this with **your actual run results** after running the notebook.
- `src/audit_data.py` — local data audit helper.
- `requirements.txt` — packages used in Colab.

## Before running
1. Download `training_assessment.zip` from the assignment email.
2. Open Google Colab and choose **Runtime → Change runtime type → T4 GPU**.
3. Upload this notebook to Colab.
4. Run cells from top to bottom. When prompted, upload `training_assessment.zip`.
5. Save the adapter, notebook outputs, report, and predictions to your Google Drive / project folder.

## Model choice
Default: `Qwen/Qwen2.5-0.5B-Instruct` (0.5B parameters). It is comfortably below the 4B limit and is a practical starting point for a T4. The notebook uses 4-bit QLoRA to reduce GPU memory use.

## Important limitations
- The cleaning log is a conservative first-pass audit: it drops malformed JSON labels and labels with a corrupted priority field. Review the excluded examples and document any further decisions.
- Do **not** invent experiment scores, GPU memory, training time, or adapter files. The report contains placeholders until you run the notebook.
- This starter includes the workflow, not a pre-trained adapter. The adapter and `predictions_test.jsonl` are generated only after training and inference finish.
- The assignment explicitly permits AI assistants but requires you to disclose their use. Be ready to explain and modify the code yourself.

## Reproducibility
Do not commit the original training/dev/test data or base model. Keep the repository private until the deadline as requested by the assignment.
