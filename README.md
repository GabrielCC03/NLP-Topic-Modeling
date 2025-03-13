# NLP-Topic-Modeling

## Project Overview
This project applies advanced unsupervised machine learning techniques to perform topic modeling on a dataset of news headlines. The goal is to automatically discover meaningful topics within a large corpus of news headlines to facilitate easy categorization and further analysis.
** Dataset:** https://www.kaggle.com/datasets/therohk/million-headlines

## Techniques Implemented

- **Preprocessing:**
  - Tokenization, stemming, and lemmatization to clean and standardize text data.
![StemLemma](https://github.com/user-attachments/assets/aa1905a4-2192-4eee-8168-364630b13891)

- **Word Embeddings (Word2Vec) with K-means Clustering:**
  - Generated embeddings for each headline.
  - Clustered these embeddings using K-means to identify distinct groups of related topics.

- **Latent Dirichlet Allocation (LDA):**
  - Implemented LDA for probabilistic topic modeling.
  - Determined optimal number of topics through coherence scores to balance specificity and generalization.
![LDA - Coherence Score](https://github.com/user-attachments/assets/ef7ee0e2-9555-4a2a-a916-e7305894c363)
<img width="1188" alt="LDAvis" src="https://github.com/user-attachments/assets/6bffa6f0-9ed5-44b0-8a45-980910718acf" />


- **Top2Vec, AGNES, and TF-IDF Hybrid Approach:**
  - Combined Top2vec for embedding generation, AGNES for hierarchical clustering, and tf-idf for keyword importance.
<img width="527" alt="Top2vec PCA" src="https://github.com/user-attachments/assets/5e607cc3-c7c3-4fbe-8082-7a1f9578722a" />

I used top2vec, which finds topics within documents and generates jointly embedded topic, document, and word vectors. Top2vec uses the hdbscan algorithm for clustering and was not deterministic, so using a 5% shuf�led version of the dataset, it would return around 94 topics each time. In practice, this number of topics is still too much, which means the topics need to be more general.

  - Thus, I used Agglomerative Nesting (AGNES) to reduce the number of topics to 13, the number of topics with a higher coherence score using LDA, by merging their representative keywords
<img width="550" alt="AGNES" src="https://github.com/user-attachments/assets/f965c44d-56df-4672-83ab-71c0161c3a93" />


## Approach for Dynamic Classification
- Developed a solution to dynamically classify new incoming headlines:
  - Each topic cluster was embedded into a unique \"signature\" vector.
  - Classified new headlines by comparing their embeddings to these signature vectors using cosine similarity.
![Multicolor corporate marketing and business strategy chart graphic](https://github.com/user-attachments/assets/71948112-408e-484b-93e4-d2bd5b37db7c)
- This method supports efficient, scalable, and real-time classification of news headlines.

## Challenges & Solutions
- **Optimal Number of Topics:**
  - Utilized coherence scores and qualitative analysis to determine the ideal balance, avoiding overly specific or overly broad topics.

- **Evaluating Model Quality:**
  - Combined quantitative coherence metrics and manual evaluations to verify topic interpretability and coherence.

## Project Results
- Successfully identified meaningful and interpretable news topics.
- Demonstrated robustness in modeling, capable of accurately categorizing new, unseen headlines.
- Presented a methodologically sound process for preprocessing, embedding generation, clustering, and evaluation.
