# Week 1 — Research Note

**Researcher:** Nguyễn Phúc Cát  
**Project:** Online Machine Learning for Real-Time Credit Card Fraud Detection  
**Course:** Đồ án tổng hợp  
**University:** Ho Chi Minh City University of Technology (HCMUT)

---

## 1. Research Focus

During the first week, the main focus was to understand the basic concepts behind Online Machine Learning and why it is relevant to real-time credit card fraud detection.

The research started from the characteristics of the problem:

- Credit card transactions can arrive continuously over time.
- A fraud detection model may need to process new transactions incrementally.
- Fraud patterns may change over time.
- Fraud datasets are usually highly imbalanced, with fraudulent transactions representing only a small portion of all transactions.

The main research question at this stage is:

> How can Online Machine Learning be applied to continuously arriving transaction data while allowing the model to update and adapt over time?

---

## 2. Online Machine Learning

Online Machine Learning is a learning approach in which a model processes data incrementally instead of requiring the entire training dataset to be available before learning.

In a typical online learning process, the model receives an observation, makes a prediction, receives the true label when available, and then updates itself using that observation.

A simplified workflow is:

New Transaction  
↓  
Prediction  
↓  
Fraud / Not Fraud  
↓  
True Label Available  
↓  
Model Update  
↓  
Next Transaction

This differs from traditional batch learning, where a model is generally trained using a fixed dataset and may need to be retrained when new data becomes available.

For the project's fraud detection problem, the incremental learning process is relevant because transactions can be treated as observations arriving sequentially.

---

## 3. Streaming Data

Streaming data refers to data that arrives continuously over time rather than being provided only as one fixed dataset.

For credit card fraud detection, individual transactions can be considered observations in a data stream:

Transaction 1 → Model  
Transaction 2 → Model  
Transaction 3 → Model  
...  
Transaction N → Model

This creates a different learning environment from conventional batch machine learning.

A streaming learning system needs to consider:

- Continuous data arrival
- Incremental processing
- Limited or controlled memory usage
- Processing speed
- Changes in the underlying data distribution

The important point for this project is that the model should be able to process observations sequentially rather than depending entirely on periodic retraining from the complete dataset.

---

## 4. Concept Drift

Concept Drift refers to changes in the underlying data distribution or in the relationship between input data and the target output over time.

For fraud detection, this is particularly relevant because transaction behavior and fraudulent behavior are not necessarily constant.

For example, suppose that a model initially learns a relationship represented by:

Pattern A → Fraud

After some time, transaction behavior may change:

Pattern A → Normal  
Pattern B → Fraud

If the model continues relying only on its historical knowledge, its performance may decrease when the current data no longer follows the previous pattern.

Concept drift is therefore an important issue in streaming data classification. Research on concept drift generally considers three related tasks: detecting changes, understanding the changes, and adapting the learning process to them.

---

## 5. Batch Learning vs Online Learning

The main difference investigated during Week 1 is how the two approaches handle data.

| Aspect | Batch Learning | Online Learning |
|---|---|---|
| Data | Usually works with a fixed dataset | Processes observations incrementally |
| Training | Trains on a dataset or batch | Updates progressively |
| New data | May require retraining | Can be incorporated incrementally |
| Streaming data | Not naturally designed for continuous updates | Designed for sequential data |
| Adaptation | Usually periodic | Can adapt during the learning process |
| Concept drift | Often requires retraining or additional mechanisms | Can incorporate adaptation mechanisms |

The important distinction is not simply that online learning is "faster". Its main relevance to this project is the ability to learn incrementally from continuously arriving observations.

---

## 6. Algorithms Investigated

During the initial research, several machine learning approaches for streaming data were investigated.

### 6.1 Decision Tree

A Decision Tree represents a classification process using a tree structure.

Each internal node represents a decision based on a feature, and the final leaf represents a prediction.

A standard Decision Tree is conceptually different from an ensemble such as Random Forest because it uses a single tree structure.

For streaming data, however, a conventional batch Decision Tree is not necessarily sufficient because the model needs to deal with continuously arriving observations and possible changes in the data distribution.

This led to investigating tree-based algorithms specifically designed for data streams.

---

### 6.2 Random Forest

Random Forest is an ensemble method consisting of multiple decision trees.

Instead of relying on a single tree, multiple trees contribute to the final prediction.

A simplified view is:

Tree 1 → Fraud  
Tree 2 → Not Fraud  
Tree 3 → Fraud  
Tree 4 → Fraud  
↓  
Final prediction → Fraud

The main idea investigated here is the difference between a single decision tree and an ensemble of multiple trees.

However, a conventional Random Forest is still primarily associated with batch learning. Therefore, using Random Forest directly does not automatically make a system an Online Machine Learning system.

---

### 6.3 Adaptive Random Forest

Adaptive Random Forest (ARF) was investigated because it is specifically designed for evolving data streams.

The key idea is to combine an ensemble of randomized decision trees with mechanisms that allow the ensemble to adapt when the data distribution changes.

This makes ARF conceptually relevant to the project's two main requirements:

1. Processing streaming data.
2. Adapting to changes in the data stream.

Research on Adaptive Random Forests describes them as an approach for classification in evolving data streams, including situations involving concept drift.

At this stage, ARF is considered a candidate approach rather than a final algorithm selected for the project.

---

### 6.4 Hoeffding Trees and Very Fast Decision Trees

Hoeffding Trees were also investigated as another family of decision-tree algorithms designed for streaming environments.

The main idea is that a Hoeffding Tree can make decisions about tree splitting using statistical guarantees without requiring the entire dataset to be stored.

This is relevant to data streams because the amount of incoming data can potentially be very large or unbounded.

Very Fast Decision Trees (VFDT) are based on the same general idea of using the Hoeffding bound to incrementally construct a decision tree from streaming data.

These approaches are therefore different from simply applying a conventional Decision Tree to a static dataset.

---

## 7. River

River is a Python library designed for machine learning on streaming data.

The library provides algorithms and tools for incremental learning, allowing models to process observations one at a time.

This makes River relevant to the project because the intended problem is not simply conventional fraud classification on a fixed dataset. The project is specifically concerned with processing transaction data as a stream.

The general interaction can be represented as:

Transaction  
↓  
River Model  
↓  
Prediction  
↓  
True Label  
↓  
Model Update

River is therefore being investigated as the main software framework for implementing the online learning component of the project.

---

## 8. Initial Algorithm Considerations

Several approaches were considered during the first stage of research.

The main criteria are:

- Ability to process streaming data
- Ability to learn incrementally
- Ability to handle changes in data distribution
- Suitability for binary classification
- Availability of an implementation in the chosen framework
- Computational requirements
- Suitability for the project's experimental setup

At this point, no final algorithm is recorded as the definitive algorithm for the project.

The candidate approaches require further investigation and experimental comparison before making the final selection.

---

## 9. Key Understanding After Week 1

The main understanding obtained during this week is that the project is not simply a conventional credit card fraud classification problem.

There are several related requirements:

**Fraud Detection**

The model needs to classify a transaction as fraudulent or non-fraudulent.

**Streaming Data**

Transactions are considered observations arriving continuously over time.

**Online Learning**

The model should be capable of updating incrementally as new observations and labels become available.

**Concept Drift**

The relationship between transaction characteristics and fraud may change over time, meaning that a model should be able to adapt to changing patterns.

These four concepts are closely connected and form the main foundation of the project.

---


## 10. References

- River — Online Machine Learning for Python  
  https://riverml.xyz/

- Lu, J., Liu, A., Dong, F., Gu, F., Gama, J., & Zhang, G. (2020). *Learning under Concept Drift: A Review.*  
  https://arxiv.org/abs/2004.05785

- Gomes, H. M., et al. (2017). *Adaptive random forests for evolving data stream classification.* Machine Learning.

- Lucas, Y., & Jurgovsky, J. (2020). *Credit Card Fraud Detection using Machine Learning: A Survey.*  
  https://arxiv.org/abs/2010.06479