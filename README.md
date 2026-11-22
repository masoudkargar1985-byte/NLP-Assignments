# NLP Assignments — Masoud Kargar / مسعود کارگر

Four Jupyter notebooks for the deep learning / NLP assignments:

| Notebook | Task |
| --- | --- |
| [01_stackoverflow_bag_of_embeddings.ipynb](01_stackoverflow_bag_of_embeddings.ipynb) | Four-class Stack Overflow classification with pooled embeddings |
| [02_stackoverflow_rnn.ipynb](02_stackoverflow_rnn.ipynb) | Four-class classification with a bidirectional GRU |
| [03_shahnameh_language_model.ipynb](03_shahnameh_language_model.ipynb) | Character-level Transformer language model for Shahnameh |
| [04_persian_to_english_translation.ipynb](04_persian_to_english_translation.ipynb) | Persian-to-English encoder–decoder Transformer, Shenasa parallel dataset subset |

## Run on the original datasets

Use Google Colab with internet access, preferably a GPU runtime. Run all notebook cells in sequence while `NB_OFFLINE_SMOKE` is unset (or `0`). Required libraries include PyTorch, NumPy and scikit-learn; the translation notebook has a dependency-install cell for `datasets`.

For a quick offline code test, set `import os; os.environ["NB_OFFLINE_SMOKE"]="1"` before running the first cell.

## Results and limitations

**The outputs currently saved in the notebooks are from tiny offline smoke tests, not training and evaluation on the real datasets.** Do not report the smoke-test metrics as accuracy or translation quality on the original datasets. Actual full-data results must be generated and saved separately before academic submission.

The Stack Overflow notebooks preserve capitalization and code punctuation instead of destructive standardization, have **four output classes**, and use the multiclass `CrossEntropyLoss`.

## References

- [Stack Overflow text-classification exercise](https://github.com/Alireza-Akhavan/deeplearning-tensorflow2-notebooks/blob/master/26-text_classification.ipynb)
- [Language model notebook](https://github.com/Alireza-Akhavan/transformers/blob/main/01_language_model.ipynb)
- [Shenasa English–Persian parallel dataset](https://huggingface.co/datasets/shenasa/English-Persian-Parallel-Dataset)
