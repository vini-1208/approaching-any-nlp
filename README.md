# Approaching any NLP problem

There is no doubt that Natural Language Processing/NLP has tremendous potential to create disruptive technologies improving business as well as everyday challenges. Downstream tasks such as Text classification, Sentiment analysis, Parts of Speech (POS)Taggers, Named Entity Recognitions (NER), Semantic Parsing, Natural Language Understanding are some of the most active research areas that continue to evolve in their algorithmic approach.  

The aim of this documentation is to give an overview of steps required to approach almost any NLP problem. It may also be used as a checklist to ensure all the standard steps are carried out for problem solving. The NLP methodology can be broken down into below major steps:
1. Text preprocessing
2. Feature Extraction
3. Data exploration
4. Identify type of problem: Unsupervised, Semi-supervised or Supervised
5. Building NLP models based on problem type
6. Design Evaluation metrics
7. Generate predictions and insights

Let us look at details within each of these steps:
1. Text preprocessing: 
     This is a mandatory step required before we begin with NLP modelling. The objective of this step is to create cleaner represensation of text data that can be further consumed into modelling framework. Below are basic preprocessing activities that can be carried out:
     
| Tasks        | Description           | List of Python packages  |
| ------------- |:-------------| :-----|
| tokenize     | Tokenize/ split text into words | built-in function split()/ nltk/ gensim |
| lowercase     | lowercase the text | built-in function lower() function |
| Expand contractions | Expand words such as I've, it'll to be expanded as I have, it will, etc      |    contractions, regex package |
|  Removal of trivial characters    | Removal of special characters, punctuations, numbers, non-ascii      | regex    |
| Removal of stopwords  |  Removal of stopwords such as will, is, the, a: that are frequently ocuring     | built-in split() function    |
| lemmatization  |  reducing words to dictionary forms/lemma     |    textblob/ gensim/ spacy |
| stemming  |  reducing words to its word stem      |    textblob/ gensim/ spacy|

Depending upon the problem at hand, one may choose to select one or more of the above steps. For example in certain use cases, stemming may make more sense than lemmatization

2. Feature Extraction:
 This involves process of creating features that can be used for modelling tasks. One may wish choose any or the below approaches depending on downstream task. Below steps are  in increasing order of complexity.

| Type        | Name           | Description             |
| :------------- |:-------------| :-----|
| Count Vectorizer     | Bag of words or  N-grams | Text/ documents can be split into bag of words or bi-grams/tri-grams representation. We could further create a Document-Term matrix with frequency counts for every occurence of terms in the document  |
| TF-IDF     | Create TF-IDF  on Document-Term matrix | Most commonly used approach which will assign TF-IDF scores in a way that assigns less weights to frequently occuring words and more to less frequent words  |
| Word embeddings (Neural network based) | word2vec      | Generates word vectors by incorporating contextual information based on neighboring words. Vectors may be created using Skip-gram or CBOW architectures that are based on neural network |
|  Word embeddings (Transformer based)    | words vectors built using transformers/ BERT architectures      | Generate word vectors based on attention mechanism in transformers/ BERT architectures. These representations are better in understanding meaning and semantics of words    |

3. Data exploration potential steps:
  - Create n-grams (uni, bi and tri-grams) distributions and plot them to understand frequently occuring word pairs
  - Build word clouds
  - Clustering of word vectors 
  - Cosine similarity between words to understand semantic similarity

4. Identify type of problem: Unsupervised, Semi-supervised or Supervised. This step will helpful in determining which algorithm to choose depending upon the nature of problem     
  - Supervised: if we have enough labelled data and wish to generate automated labelling framework, it becomes a supervised problem
  - Zero shot: we if do not have enough annotated data, we may try zero shot learning approach
  - Semi/self supervised: tasks such as Word2vec embeddings, language modelling are generally semi or self-surpervised problems.  We train the models on huge corpus of text instead of humanly annonated data
  - Unsupervised: Topic modelling, Clustering, etc are some of the tasks where we may not have labelled data

5. Building NLP models based on problem type identified

| Complexity level        | Name           | Type of problems             |
| :------------- |:-------------| :-----|
| Basic Probablistic models   | Linear regression, SVM, Naive Bayes | Supervised: text classification/ sentiment analysis  |
| Deep learning based     | LSTM/ RNNs based | Machine Translation, Language modelling |
| Transfer learning | Transformer/ BERT/ XLnet based      | Pre-trained models on language modelling can be fine tuned on downstream tasks|

6. Design Evaluation metrics: This is a crucial step in determining whether NLP modelling is helping achieve desired results. Metrics such as accuracy, F1, precision, Kappa score, Rouge metric, cosine simialrity are some of the commonly used evaulation techniques depending upon the NLP task
7. Generate predictions and insights: Final step post model evaluation is to generate predictions and insights in a way that can be consumed by end user. It could be in form of visualization dashboards, APIs or flat files
