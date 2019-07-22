# Topic-modeling

[Topic modeling](https://en.wikipedia.org/wiki/Topic_model) is a statistical model to discover semantic structures in text body. The "topics" produced by topic modeling techniques are clusters of similar words. A document typically concerns multiple topics in different proportions; thus, in a document that is 10% about cats and 90% about dogs, there would probably be about 9 times more dog words than cat words. In this example, I have created a Topic modeling for 2 wikipedia web pages using Latent Dirichlet allocation (LDA).

[Latent Dirichlet allocation (LDA)](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation) is a generative statistical model that allows sets of observations to be explained by unobserved groups that explain why some parts of the data are similar. For example, if observations are words collected into documents, it posits that each document is a mixture of a small number of topics and that each word's presence is attributable to one of the document's topics.

[Natural Language Toolkit (NLTK)](https://www.nltk.org/) provides text processing libraries for classification, tokenization, stemming, tagging, parsing, and semantic reasoning, wrappers for industrial-strength NLP libraries for Python.

---
### I Scraping web-pages for their content:

  1. Wikipedia [Lego](https://en.wikipedia.org/wiki/Lego)
  2. Wikipedia [Oil](https://en.wikipedia.org/wiki/Oil)

---
### II. Storing the content in text files:

```python
file = open('ParsedString3.txt','wb' )
for strings2 in soup1.stripped_strings:
    strings2 = str(strings2)
    file.write(strings2)
```
---
### III. Creating single document from combination of the 2 text documents obtained from scraping webpages:

```python
file1 = open("../ParsedString3.txt", 'r')
file2 = open("../ParsedString4.txt", 'r')

doc1 = file1.readlines()
doc2 = file2.readlines()

# compile sample documents into a list
doc_set = doc1 + doc2
```
---
### IV. Importing libraries:

```python
from nltk.tokenize import RegexpTokenizer
from stop_words import get_stop_words
from nltk.stem.porter import PorterStemmer
from gensim import corpora, models
import gensim
```
---
### V. Cleaning and tokenizing:

```python
raw = i.lower()
raw = raw.decode("utf8")
tokens = tokenizer.tokenize(raw)
```
where "i" is the element in the document list

---
### VI. Removing stop words from token:

Stop words are those words which appear in higher frequency is the entore document and doesn't prove to be of much importance is identifying the topics in document. These words are well defined in the library "stop_words". Some examples are: and, the, or, is, ., ,, ?.

---
### VII. Stemming tokens:

Stemming helps to reduce inflectional forms and sometimes derivationally related forms of a word to a common base form, thereby shortening the lookup, and normalizing sentences. Many variations of words carry the same meaning. For instance:
[Ref](https://nlp.stanford.edu/IR-book/html/htmledition/stemming-and-lemmatization-1.html)

---
### VIII. Bag-of-Words (BoW):

First, create a dictionary function, which assigns unique id to each token in document text and collects relevant statistics(*count*). Create a bag-of-words from this dictionary which results in a text matrix of occurance of word. The output includes those words which are present in the list [Ref](https://en.wikipedia.org/wiki/Bag-of-words_model)

---
### IX. LDA model:

Generate an LDA model with required specifications - corpus, number of topics model needs to be designed for, iinput dictionary and input corpus, number of words in each pass

---
### X. And the Topics are...

Call the lda model to identify either 1, 2, 3 or more topics from the given list of words.

```python
print(ldamodel.print_topics(num_topics=2, num_words=2))
```
> [(2, u'0.000*"u" + 0.000*"oil"'), (1, u'0.232*"u" + 0.036*"lego"')]

> Each generated topic is separated by a comma. Within each topic are the 2 most probable words to appear in that topic. 
