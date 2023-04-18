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
$idf(f, D)  = \log{ \left( \frac{N}{\textrm{count}(d \in D:t\in d)} \right)}$
