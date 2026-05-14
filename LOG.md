# Development Log - Project 14
# Efficient Extractive Question Answering on SQuAD with Distilled Models

**Team Members:** Student A | Student B | Student C  
**Course:** CISC 867 Deep Learning  
**Repository:** https://github.com/Salma-21/Lightweight-Extractive-Question-Answering-on-SQuAD-Using-DistilBERT#

---

## Week 1

### Date: 03/05/2026 - 09/05/2026

#### Progress
- [ ] Student A: Downloaded SQuAD v1.1 and explored JSON structure
- [ ] Student A: Built data loading and subset filtering script
- [ ] Student A: Completed tokenization pipeline with answer span offsets
- [ ] Student A: Created train/validation/test splits
- [ ] Student B: Read DistilBERT paper and studied HuggingFace QA API
- [ ] Student B: Set up environment (dependencies, CPU config)
- [ ] Student B: Ran sanity-check forward pass on DistilBertForQuestionAnswering
- [ ] Student C: Studied SQuAD evaluation metrics (EM, F1)
- [ ] Student C: Implemented/adapted official SQuAD evaluation script
- [ ] Student C: Built results-logging utility (predictions to CSV)

#### Key Decisions
- Chose subset size of [X] QA pairs because [reason, e.g., fits within CPU memory/time budget]
- Chose to use HuggingFace `Trainer` over a custom loop because [reason]
- Decided on [X]% / [Y]% / [Z]% train/val/test split because [reason]
- [Any other decisions made as a team]

#### Issues & How They Were Resolved
- **Issue:** [e.g., Answer span offsets misaligned after tokenization]  
  **Resolution:** [e.g., Used `return_offsets_mapping=True` in tokenizer]  
  **Resolved by:** Student A

- **Issue:** [e.g., HuggingFace version conflict on one machine]  
  **Resolution:** [e.g., Pinned transformers==4.x.x in requirements.txt]  
  **Resolved by:** Student B

#### Relevant Commits
- `[commit hash]` - Student A: Add SQuAD data loader and subset script
- `[commit hash]` - Student B: Set up environment and model sanity check
- `[commit hash]` - Student C: Add SQuAD evaluation script

---

## Week 2

### Date: 10/05/2026 - 16/05/2026

#### Progress
- [ ] Student A: Implemented TF-IDF / rule-based baseline
- [ ] Student A: Computed baseline EM and F1 scores
- [ ] Student A: Documented data pipeline in README
- [ ] Student B: Wrote full training loop with loss, optimizer, scheduler
- [ ] Student B: Fine-tuned DistilBERT on subset; logged metrics per epoch
- [ ] Student B: Saved checkpoints and wrote inference script
- [ ] Student B: Created hyperparameter config file
- [ ] Student C: Ran evaluation against baseline and model outputs
- [ ] Student C: Produced comparison tables and plots
- [ ] Student C: Completed first-pass qualitative error analysis (10-15 examples)

#### Key Decisions
- Chose learning rate of [X] because [reason, e.g., default from HuggingFace examples, then tuned]
- Chose batch size of [X] due to CPU memory constraints
- Decided on [X] max sequence length due to [reason]
- [Any other decisions made this week]

#### Issues & How They Were Resolved
- **Issue:** [e.g., Training too slow on CPU, one epoch taking 3+ hours]  
  **Resolution:** [e.g., Reduced max sequence length from 512 to 256]  
  **Resolved by:** Student B

- **Issue:** [e.g., Evaluation script crashing on empty predictions]  
  **Resolution:** [e.g., Added null-answer fallback in inference script]  
  **Resolved by:** Student C

#### Preliminary Results
| Model | Exact Match | F1 Score |
|-------|-------------|----------|
| Baseline (TF-IDF) | [X]% | [X]% |
| DistilBERT (fine-tuned) | [X]% | [X]% |

#### Relevant Commits
- `[commit hash]` - Student A: Add baseline implementation and scoring
- `[commit hash]` - Student B: Fine-tuning loop and checkpoint saving
- `[commit hash]` - Student B: Add hyperparameter config file
- `[commit hash]` - Student C: Add evaluation plots and error analysis notes
