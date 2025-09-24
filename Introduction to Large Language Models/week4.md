# Lec 7


### Word Representation
1)Representing Words as Discrete Symbols
- In traditional nlp, we regard words as discrete symbols.
- Such symbols for words are represented as one-hot vectors.

2) Use existing thesauri or Ontologies like Wordnet
- WordNet 3.0
 - A hierarchically organized lexical database.
 - Online thesaurus + aspects of dictionary
 - [Link](https://wordnet.princeton.edu/)
 - "Sense" in WordNet:
   - Using the synset(synonym set) , the set of near-synonyms, instantiates a sense or concept with a gloss.
## Drawbacks of Thesaurus based Approaches
- An important resource but missing nuance:
  - Example : Proficient is listed as synonym for "good" : only correct in some contexts:
- Missing new meanings of words.
- Subjective
- Requires human labour to create and adapt


### Distributional Semantics
- A word's meaning is given by the words that frequently appear close-by.
-  When a word `w` appears in a text, its context is the set of words that appear nearby(within a fixed-size window)


## Count-based methods

#### The Term-Context matrix (or, word-word matrix)
- Each cell: Number of times the row(target) word and the column (context) word co-occur in some context in the corpus.
  - Generally smaller contexts are used like paragraph or window of 10 words.
 
- Each word is a count vector in $N^v$ : a row below (V:size of vocabulary)
- Two words are similar in meaning if their context vectors are similar
- But raw word frequency is not a great measure of association between words

### TF-IDF
Term Frequency(tf) of a term $tf_{t,d}= count(t,d)$ ; No of times the word appears in the document


Document Frequency(df):
$df_t$ is the number of documents t occurs in.

Inverse Document Frequency(idf)

$idf_t$ = $log_{10} \frac {N} {df_t}$
N is the total number of documents in the collection.


tf-idf = $w_{t,d} = tf_{t,d} * idf_t$

### Drawbacks of Co-occurence matrix approach
- Quadratic space needed
- Relative position and order of words not considered.


For this , we could use SVD

### Low dimensional vectors
- Store only 'important' information in fixed, low-dimensional vector
### Drawbacks of SVD Based approach
- Computational cost scales quadratically for nxm matrix: $O(mn^2)$
- Hard to incorporate new words or documents
- Does not consider order of words.


### Word Embedding
- Dense Vector
- Helps in learning less parameters
- May generalize better
- Can capture synonyms better


## Represent the meaning of word: word2vec

(Prediction based approaches)

Two basic neural network models:
- Continuous bag of word(CBOW): Use a window of word to predict the middle word
- Skip-Gram(SG) : Use a word to prdict the surrounding words in the window

## Word2Vec
- Instead of counting how often each word w occurs near "apricot"
 - Train a classifier on a binary prediction task: Is w likely to show up near "apricot"

- Dont care abt task but will take the learned classifier weights as word embeddings.


## BIG IDEA:
- Self supervision:
 - A word c that occurs near apricot in the corpus acts as the gold "correct answer" for supervised learning
 - No need for human labels.


## Skip-Gram classifier (assuming a +- 2 word window)

Goal: Train a classifier, that, given a candidate(word,context) pair assigns each pair a probability

P(+ | w,c)

P(- | w,c) = 1- P(+ |w,c)


- Similarity is computed using dot product
 - Two vectors are similar if they have a high dot product.
 - Cosine is just a normalized dot product


- Similartity(w,c) $$propto$$ w * c


 ## Skip Gram Training Data
 - For each positive example, we will grab k negative examples, sampling by frequency

### Choosing negative examples
- $P_{\alpha} (w) = \frac { count(w)^{\alpha}}{ \sum_w' count(w')^{\alpha}}$


Setting $\alpha = 0.75$ gives better performance because it gives rare noise words slightly higher probability: for rare words : $P_{alpha} (w) > P(w)$

## Loss function for one w with $c_{pos} , c_{neg1} ... c_{negk}$


$$L_{CE} \;=\; - \log \left[\, P(+ \mid w, c_{pos}) \cdot \prod_{i=1}^k P(- \mid w, c_{neg_i}) \,\right].$$



Two sets of embeddings

- Skip-gram learns two sets of embeddings
 - Target embeddings matrix W
 - Context embedding matrix C


---



Pros and cons of Count-based and Prediction-based methods

Count-Based Methods:
**Pros**
- Fast training
- Efficient usage of statistics

**Cons**
- Primarily used to capture word similarity
- Disproportionate importance given to large counts


Prediction-based methods
**Pros**
- Generate improved performance on other tasks
- Can capture complex patterns beyond word similarity


**Cons**
- Scales with corpus size
- Inefficient usage of statistics


GloVe - Global Vectors

Crucial insight: Ratios of co-occurence probabilities can encode word meaning

Learn word vectors based on these counts

For the two words, i and j, assume their corresponding representation vectors are $w_i$ and $w_j$ respectively.

$w_i^t w_j$ = $log P(j | i) = log X_{ij} - log X_i$


$w_i^t w_j = log(X_{ij})  - \frac{log(X_i) }{2} - \frac{log(X_j) }{2}$

$log(X_{ij}) = w_i^t w_j  + \frac{log(X_i) }{2} + \frac{log(X_j) }{2}$

Prob: gives equal weightage to all co-occurences

Need to add a weighing function f(x)

f(x) =  $(\frac{x}{x_{max}})^ \alpha    if x<x_{max} ; 1 otherwise$

alpha is hyperparameter



### Advantages
- Fast training
- Scalable to huge corpora
- Good performance even with small corpus and small vectors
