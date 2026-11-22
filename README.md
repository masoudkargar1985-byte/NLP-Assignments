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

## Automated real-data notebook execution

A [GitHub Actions workflow](.github/workflows/train_real_data.yml) runs the four notebooks in parallel with `NB_OFFLINE_SMOKE=0` on GitHub-hosted Linux CPU workers. It validates completed notebooks and commits real-data results back to `main` **only if all four jobs succeed**. This is not a Google Colab GPU run. The workflow may fail due to data downloads, execution-time limits, dependencies or hardware resource limits; check the [Actions page](../../actions) before making any result claims.

Current notebook outputs that identify themselves as `OFFLINE SMOKE TEST` are synthetic code checks, not actual dataset training results.

## November 22, 2026 – review and corrections

The original full-data run completed successfully, but its generation quality was limited: the Shahnameh character model produced fragmented Persian, and the from-scratch Persian→English translator produced semantically inaccurate English. The four main assignments were therefore revised:

- Classification notebooks now use validation-based best-checkpoint selection / early stopping, plus learning curves and confusion matrices. They preserve case and programming punctuation.
- Shahnameh retains the corpus-trained causal Transformer and adds learning curves plus a separately labeled **word-level trigram model trained on the same Shahnameh text** for a qualitative comparison. The trigram output is not Transformer output.
- Translation retains its original 100,000-pair from-scratch Transformer, adds a comparison against an **externally pretrained mT5 Persian→English translator**, and measures illustrative held-out chrF++. The external model is not claimed as trained from scratch in this project.

**Verification status:** the revised notebooks must be re-executed successfully with the real datasets before the added outputs can be presented as measured results. See the latest [Actions runs](../../actions). The earlier 81.2% / 82.3% classification accuracies belong to the prior full-data run; new best-checkpoint metrics may differ.

### Formal academic explanation (Persian)

[REPORT_FA.md](REPORT_FA.md) documents the actual baseline results, requirements mapping, overfitting evidence, model-quality failures, and the exact changes applied in the revised notebooks.
