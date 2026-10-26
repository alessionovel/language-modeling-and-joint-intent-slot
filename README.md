# Language Modeling and Slot Filling

Project for the **Natural Language Understanding** course at the University of Trento. It has two parts, each split into two assignments:

- **[LM](LM)**: next-word prediction on the Penn Treebank, evaluated with perplexity (lower is better).
- **[NLU](NLU)**: joint intent classification and slot filling on ATIS, evaluated with accuracy and F1.

Every change is added one step at a time, with hyperparameter tuning (mainly the learning rate). Unsuccessful experiments are kept and discussed in the reports.

## Results

| Part | Model | Best test result |
| --- | --- | --- |
| [LM / Part A](LM/part_A) | RNN baseline → LSTM → dropout → AdamW | Perplexity 155.03 → **104.10** |
| [LM / Part B](LM/part_B) | LSTM + weight tying → variational dropout → NT-AvSGD | Perplexity 134.49 → **98.61** |
| [NLU / Part A](NLU/part_A) | IAS baseline → bidirectional → dropout (+ AdamW) | Slot F1 0.933 → **0.951**, intent accuracy 0.926 → **0.960** |
| [NLU / Part B](NLU/part_B) | Fine-tuned BERT-base (multi-task) | Slot F1 **0.958**, intent accuracy **0.978** |

The full analysis is in the reports: [LM/report_LM.pdf](LM/report_LM.pdf) and [NLU/report_NLU.pdf](NLU/report_NLU.pdf). Each part has its own README with the requirements, the experiments and how to run the code.

## Structure

The folder layout follows the one required for the project submission:

```
LM/
├── part_A/        RNN/LSTM language model
├── part_B/        LSTM with advanced regularization
└── report_LM.pdf
NLU/
├── part_A/        Intent and slot filling with an LSTM (IAS model)
├── part_B/        Intent and slot filling with BERT
└── report_NLU.pdf
```

Each part contains `main.py`, `model.py`, `functions.py`, `utils.py`, the dataset, the results of every experiment (`experiments_results.json`) and the training plots.
