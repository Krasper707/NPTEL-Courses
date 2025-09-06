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

