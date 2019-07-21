# Topic-modeling

Topic modeling is a statistical model to discover semantic structures in text body. The "topics" produced by topic modeling techniques are clusters of similar words. A document typically concerns multiple topics in different proportions; thus, in a document that is 10% about cats and 90% about dogs, there would probably be about 9 times more dog words than cat words. In this example, I have created a Topic modeling for 2 wikipedia web pages using Latent Dirichlet allocation (LDA). [ref](https://en.wikipedia.org/wiki/Topic_model)

Latent Dirichlet allocation (LDA) is a generative statistical model that allows sets of observations to be explained by unobserved groups that explain why some parts of the data are similar. For example, if observations are words collected into documents, it posits that each document is a mixture of a small number of topics and that each word's presence is attributable to one of the document's topics. [ref](https://en.wikipedia.org/wiki/Latent_Dirichlet_allocation)

I. Scraped 2 web-pages for their content:
  1. Wikipedia [Lego](https://en.wikipedia.org/wiki/Lego)
  2. Wikipedia [Oil](https://en.wikipedia.org/wiki/Oil)

II. Stored the content in text files
```python
file = open('ParsedString3.txt','wb' )
for strings2 in soup1.stripped_strings:
    strings2 = str(strings2)
    file.write(strings2)
```

III. Import libraries
```python
from nltk.tokenize import RegexpTokenizer
from stop_words import get_stop_words
from nltk.stem.porter import PorterStemmer
from gensim import corpora, models
import gensim
```
III. These text files are imported in our model

IV. Processed by removing stop words, tokenizing, creating corpus
V. This list is fed to LDA model for 2 topics and 2 words are displayed
