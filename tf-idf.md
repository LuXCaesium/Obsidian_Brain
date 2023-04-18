---

created: <% tp.file.creation_date() %>

---
tags:: #Statistics #NLP #MachineLearning #DataScience 

# TF_IDF (Term Frequency - Inverse Document Frequency)

TF-IDF is a measure used in the fields of information retrieval and machine learning, that can quantify the importance or relevance of string representations (words, phrases, etc) in a document amongst a collection of documents (corpus).

### TF (Term Frequency)
Term frequency works by looking at the frequency of a particular term you are concerned with relative to the document. There are several measures to define this:
- Number of time the word appears in a document (raw count).
- Term frequency adjusted for the length of the document. (raw count divided by n.o words in the document.)
- Logarithmically scaled frequency (e.g $log(1+\textrm{raw count})$)
- Boolean frequency (e.g 1 if the term occurs, or 0 if the term does not occur in the document).

### IDF (Inverse Document Frequency)

Inverse document frequency looks at how common (or uncommon) a word is amongst the corpus. IDF is calculated as follows
$idf(t, D)  = \log{ \left( \frac{N}{\textrm{count}(d \in D:t\in d)} \right)}$

Where
- t is the term we are looking to measure the commonness of.
- N is the number of documents d in the corpus D.
- Denominator is simply the number of documents in which term t appears in.

We need idf to correct for words like "of", "as" etc since they appear frequently in the English corpus. Thus taking the inverse of document frequency, we can minimise the weighting of frequent terms whilst making infrequent terms have higher impact.

### Summary
To summarise, the key intuition motivating TF-IDF is the importance of a term is inversely related to its frequency across documents. 
TF gives us information on how often a term appears in a document.
IDF gives us information about the relative rarity of a term in the collection of documents.
The higher the TF-IDF score the more important or relevant the term is.

$tfidf(t, d, D) = tf(t, d) . idf(t, D)$

## Where to use TF-IDF

### In Machine Learning & Natural Language Processing
When dealing with textual data or any natural language processing task, the data first needs to be converted into a vector of numerical data which can be processed. This is known as vectorization.

TF-IDF vectorisation involves calculating the TF-IDF score for every word in your corpus relative to that document and passing the output to a vector. 