# Detecting Sentiment Shifts in Financial News


## Research Paper

### Summary  
The goal of the FinBERT paper is to introduce a financial BERT model fine‑tuned on domain‑specific text. General BERT models struggle with financial vocabulary (e.g., “debt” can be neutral or positive in earnings calls). FinBERT is pretrained on 4.9 B tokens of financial documents—earnings transcripts, filings, etc.—allowing it to capture those nuances. The authors demonstrate that FinBERT outperforms general BERT on multiple benchmarks by correctly classifying subtle financial sentiments.

### Bibliographical Info
- **Title:** FinBERT: A Pretrained Language Model for Financial Communications  
- **Authors:** Yi Yang, Mark Christopher Siy Uy, Allen Huang  
- **Publication:** arXiv preprint, 2020  
- **URL:** [https://arxiv.org/pdf/2006.08097](https://arxiv.org/pdf/2006.08097)  

### Background  
FinBERT addresses the lack of specialized sentiment analysis tools for finance. While BERT excels broadly, it misclassifies domain‑specific terms. Inspired by BioBERT and SciBERT, the authors train a BERT variant on financial corpora, yielding significant gains on the FiQA, Financial PhraseBank, and AnalystTone datasets. This motivates our project’s use of FinBERT as a backbone for temporal sentiment analysis.

### Summary of Contributions
- **FinVocab:** Custom vocabulary generated via SentencePiece on financial text.  
- **FinBERT:** BERT variant pretrained on 4.9 B financial tokens.  
- **Evaluation:** Outperforms general BERT on Financial PhraseBank, AnalystTone, and FiQA.  
- **Reproducibility:** Open‑sourced code and model weights.

### Limitations & Discussion  
- **Sentence-level focus:** FinBERT only classifies individual sentences and does not model sentiment evolution over time.  
- **Marginal token gains:** FinVocab yields only minor improvements over BERT’s base vocabulary, questioning its cost–benefit.

### Why This Paper  
Our project tracks sentiment shifts around financial events; FinBERT proves that domain‑pretraining boosts classification accuracy. We will build on its techniques to extend from sentence‑level to time‑series sentiment analysis.

### Wider Research Context  
This follows the trend of domain‑adapted LMs (e.g., BioBERT, SciBERT). Techniques like vocabulary adaptation, transformer fine‑tuning, and specialized corpora are broadly applicable to other domains (legal, medical).

---

## Project Description

### Goals  
- **Sentiment Classification:** Fine‑tune transformer models (RoBERTa, FinBERT, DistilBERT) to label each headline as positive/neutral/negative.  
- **Temporal Shift Detection:** Aggregate headline sentiments over time and apply changepoint detection (PELT, Bayesian methods) to highlight shifts around predefined events (earnings calls, Fed announcements).

### Data  
- **Headlines:** [Kaggle Financial News Headlines](https://www.kaggle.com/datasets/notlucasp/financial-news-headlines)  
- **Event Timelines:** Earnings calendars, macroeconomic policy announcements, etc.

### Methods  
1. **Baseline:** Naive Bayes & Logistic Regression with TF‑IDF; random and majority‑vote classifiers.  
2. **Fine‑tuned Transformers:** RoBERTa, FinBERT, DistilBERT for sentence‑level sentiment.  
3. **Aggregation & Changepoint Detection:** Rolling windows of sentiment scores; PELT or Bayesian algorithms.  
4. **Correlation Analysis (optional):** Pearson/Spearman correlations between sentiment indices and market metrics.

### Evaluation  
- **Classification Metrics:** Accuracy, precision, recall, F1‑score on held‑out headlines.  
- **Changepoint Detection:** Statistical significance tests (t‑tests) for sentiment pre/post events.  
- **Market Alignment:** Correlate detected shifts with stock movements.

---

## References

1. Guo, Y., Hu, C., & Yang, Y. (2023). *Predict the Future from the Past? On the Temporal Data Distribution Shift in Financial Sentiment Classifications*. arXiv:2310.12620.  
2. Malo, P., Sinha, A., Korhonen, P., Wallenius, J., & Takala, P. (2014). *Good debt or bad debt: Detecting semantic orientations in economic texts*. Journal of the Association for Information Science and Technology, 65(4), 782–796.  
3. Tetlock, P. C. (2007). *Giving content to investor sentiment: The role of media in the stock market*. The Journal of Finance, 62(3), 1139–1168.  
4. Yang, Y., Uy, M. C. S., & Huang, A. (2020). *FinBERT: A Pretrained Language Model for Financial Communications*. arXiv:2006.08097.

---
