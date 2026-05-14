# Development Log - Project 14
# Efficient Extractive Question Answering on SQuAD with Distilled Models

**Team Members:** Sherouk | Mostafa | Salma  
**Course:** CISC 867 Deep Learning  
**Repository:** https://github.com/Salma-21/Lightweight-Extractive-Question-Answering-on-SQuAD-Using-DistilBERT#

---

## Week 1

### Date: 03/05/2026 - 09/05/2026

#### Progress
- [ ] Sherouk: Downloaded SQuAD v1.1 and explored JSON structure
- [ ] Sherouk: Built data loading and subset filtering script
- [ ] Sherouk: Completed tokenization pipeline with answer span offsets
- [ ] Sherouk: Created train/validation/test splits
- [ ] Mostafa: Read DistilBERT paper and studied HuggingFace QA API
- [ ] Mostafa: Set up environment (dependencies, CPU config)
- [ ] Mostafa: Ran sanity-check forward pass on DistilBertForQuestionAnswering
- [ ] Salma: Studied SQuAD evaluation metrics (EM, F1)
- [ ] Salma: Implemented/adapted official SQuAD evaluation script
- [ ] Salma: Built results-logging utility (predictions to CSV)

#### Key Decisions
- Chose subset size of [X] QA pairs because [reason, e.g., fits within CPU memory/time budget]
- Chose to use HuggingFace `Trainer` over a custom loop because [reason]
- Decided on [X]% / [Y]% / [Z]% train/val/test split because [reason]
- [Any other decisions made as a team]

#### Issues & How They Were Resolved
- **Issue:** [e.g., Answer span offsets misaligned after tokenization]  
  **Resolution:** [e.g., Used `return_offsets_mapping=True` in tokenizer]  
  **Resolved by:** Sherouk

- **Issue:** [e.g., HuggingFace version conflict on one machine]  
  **Resolution:** [e.g., Pinned transformers==4.x.x in requirements.txt]  
  **Resolved by:** Mostafa

#### Relevant Commits
- `[commit hash]` - Sherouk: Add SQuAD data loader and subset script
- `[commit hash]` - Mostafa: Set up environment and model sanity check
- `[commit hash]` - Salma: Add SQuAD evaluation script

---

## Week 2

### Date: 10/05/2026 - 16/05/2026

#### Progress
- [ ] Sherouk: Implemented TF-IDF / rule-based baseline
- [ ] Sherouk: Computed baseline EM and F1 scores
- [ ] Sherouk: Documented data pipeline in README
- [ ] Mostafa: Wrote full training loop with loss, optimizer, scheduler
- [ ] Mostafa: Fine-tuned DistilBERT on subset; logged metrics per epoch
- [ ] Mostafa: Saved checkpoints and wrote inference script
- [ ] Mostafa: Created hyperparameter config file
- [ ] Salma: Ran evaluation against baseline and model outputs
- [ ] Salma: Produced comparison tables and plots
- [ ] Salma: Completed first-pass qualitative error analysis (10-15 examples)

#### Key Decisions
- Chose learning rate of [X] because [reason, e.g., default from HuggingFace examples, then tuned]
- Chose batch size of [X] due to CPU memory constraints
- Decided on [X] max sequence length due to [reason]
- [Any other decisions made this week]

#### Issues & How They Were Resolved
- **Issue:** `offset_mapping` function contained a `return` statement inside the chunk loop,
  causing it to always exit after the first chunk regardless of whether the answer was found.
  For multi-chunk examples this produced incorrect `(0, 0)` positions pointing to `[CLS]`
  instead of the real answer span, silently corrupting training labels.<br>
  **Resolution:** Moved the `return` outside the loop by collecting all chunk results in a
  `results` list and returning it after the loop completes. Updated all three encoding loops
  (train, val, test) to iterate over `chunk_positions` using `enumerate` instead of a fixed
  range, ensuring each chunk gets its own correctly computed start and end position.<br>
  **Resolved by:** Sherouk.<br>
  
- **Issue:** [e.g., Training too slow on CPU, one epoch taking 3+ hours]  
  **Resolution:** [e.g., Reduced max sequence length from 512 to 256]  
  **Resolved by:** Mostafa

- **Issue:** [e.g., Evaluation script crashing on empty predictions]  
  **Resolution:** [e.g., Added null-answer fallback in inference script]  
  **Resolved by:** Salma

#### Preliminary Results
| Model | Exact Match | F1 Score |
|-------|-------------|----------|
| Baseline (TF-IDF) | [X]% | [X]% |
| DistilBERT (fine-tuned) | [X]% | [X]% |

#### Relevant Commits
- `[commit hash]` - Sherouk: Add baseline implementation and scoring
- `[commit hash]` - Mostafa: Fine-tuning loop and checkpoint saving
- `[commit hash]` - Mostafa: Add hyperparameter config file
- `[commit hash]` - Salma: Add evaluation plots and error analysis notes
