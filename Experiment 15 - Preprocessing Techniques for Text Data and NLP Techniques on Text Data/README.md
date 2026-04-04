# 🧠 Experiment 15 — NLP Techniques on Text Data in Python

---

## 🎓 Student Details

| Field | Details |
|---|---|
| **Name** | Tanmay Agarwal |
| **PRN** | 25070123158 |
| **Batch** | EnTC A3 |
| **Date** | 03/04/2026 |
| **Subject** | Data Analytics / Python Lab |

---

## 🎯 Aim of the Experiment

To study and implement fundamental **Natural Language Processing (NLP)** techniques on text data in Python using the **NLTK (Natural Language Toolkit)** library, including:

1. **Word Tokenization** — splitting text into individual words
2. **Sentence Tokenization** — splitting text into individual sentences
3. **Stop Word Removal** — filtering out common, uninformative words
4. **Stemming** — reducing words to their root/base form using the Porter Stemmer
5. **Lemmatization** — converting words to their dictionary base form using WordNet
6. **Part-of-Speech (POS) Tagging** — identifying grammatical roles of each word
7. **Word Frequency Distribution** — counting and ranking word occurrences

---

## 📘 Introduction

**Natural Language Processing (NLP)** is a branch of Artificial Intelligence that deals with the interaction between computers and human language. It enables machines to read, understand, interpret, and generate text in a meaningful way. NLP powers a wide range of modern applications — from search engines and chatbots to sentiment analysis, machine translation, and voice assistants.

Raw text data, however, is inherently unstructured. Before any machine learning model can process language, the text must go through a series of **preprocessing steps** that clean, normalize, and structure it into a form that algorithms can work with.

This experiment introduces the most essential NLP preprocessing pipeline using Python's **NLTK** library. Each technique builds on the previous one — raw text is first broken into tokens, noise words are removed, words are reduced to their root forms, grammatical roles are identified, and finally, word frequencies are computed. Together, these steps form the backbone of any text analytics or NLP application.

---

## 📦 Libraries & Packages Used

### 🔵 NLTK — Natural Language Toolkit

NLTK is one of the oldest and most widely used Python libraries for NLP. It provides a comprehensive suite of tools for text processing — tokenization, stemming, lemmatization, POS tagging, parsing, and more. It also ships with over 50 corpora and lexical databases (like WordNet and stopwords lists).

**Installation:**
```bash
pip install nltk
```

**NLTK Data Downloads required in this experiment:**

```python
import nltk
nltk.download('punkt')                        # Tokenizer models
nltk.download('punkt_tab')                    # Updated tokenizer data
nltk.download('stopwords')                    # Stopword lists for English
nltk.download('wordnet')                      # WordNet lexical database for Lemmatization
nltk.download('averaged_perceptron_tagger')   # POS Tagger model
nltk.download('averaged_perceptron_tagger_eng') # English-specific POS Tagger
```

### 🔵 Modules Used from NLTK

| Module | Import Path | Purpose |
|---|---|---|
| `word_tokenize` | `nltk.tokenize` | Splits text into individual word tokens |
| `sent_tokenize` | `nltk.tokenize` | Splits text into individual sentence tokens |
| `stopwords` | `nltk.corpus` | Provides a list of common English stop words |
| `PorterStemmer` | `nltk.stem` | Applies the Porter Stemming algorithm |
| `WordNetLemmatizer` | `nltk.stem` | Applies WordNet-based Lemmatization |
| `pos_tag` | `nltk` | Tags each token with its Part-of-Speech label |
| `FreqDist` | `nltk.probability` | Computes word frequency distributions |

---

## 🔧 NLP Techniques — Detailed Theory & Implementation

---

### 1. 📝 Word Tokenization

#### What is it?

Tokenization is the process of breaking a string of text into smaller units called **tokens**. In **word tokenization**, each word and punctuation mark becomes a separate token. This is the very first step in any NLP pipeline — without tokens, no further processing is possible.

NLTK's `word_tokenize()` uses the **Punkt** tokenizer, which is a pre-trained, language-aware tokenizer. It correctly handles contractions (`don't` → `do`, `n't`), punctuation, and multi-word expressions better than a simple `.split()` on spaces.

#### Code from the Notebook:

```python
from nltk.tokenize import word_tokenize

text = "Natural Language Processing is interesting"

tokens = word_tokenize(text)
print(tokens)
```

#### Output:
```
['Natural', 'Language', 'Processing', 'is', 'interesting']
```

#### Working Logic:

1. Pass the raw string to `word_tokenize(text)`.
2. The Punkt tokenizer scans the string character by character.
3. It splits on spaces and punctuation boundaries, using trained rules to handle edge cases.
4. The result is a Python **list of string tokens**, one element per word or punctuation mark.

#### Why not just use `.split()`?

`text.split()` splits only on whitespace and produces incorrect results for contractions and punctuation. For example, `"don't go."` split by space gives `["don't", "go."]`, whereas `word_tokenize` gives `["do", "n't", "go", "."]` — which is linguistically more accurate.

---

### 2. 📄 Sentence Tokenization

#### What is it?

**Sentence Tokenization** (also called sentence segmentation) splits a block of text into individual sentences. This is important when processing multi-sentence documents, where each sentence needs to be analyzed independently — for example, in summarization, translation, or sentiment analysis at the sentence level.

NLTK's `sent_tokenize()` uses the Punkt sentence boundary detector, which is trained to recognize periods that end sentences (vs. abbreviations like "Dr." or "e.g.").

#### Code from the Notebook:

```python
from nltk.tokenize import sent_tokenize

text = "Python is easy. It is widely used in data science."

sentences = sent_tokenize(text)
print(sentences)
```

#### Output:
```
['Python is easy.', 'It is widely used in data science.']
```

#### Working Logic:

1. Pass the multi-sentence string to `sent_tokenize(text)`.
2. The Punkt model identifies sentence-ending punctuation (`.`, `!`, `?`).
3. It uses contextual rules to distinguish sentence-ending periods from abbreviation periods.
4. Returns a Python **list of sentence strings**, preserving the punctuation within each sentence.

---

### 3. 🚫 Stop Word Removal

#### What is it?

**Stop words** are extremely common words in a language that carry very little semantic meaning — words like *is*, *the*, *in*, *and*, *it*, *a*, *of*. In most NLP tasks (like text classification, search, or topic modeling), these words create noise and bloat the feature space without adding any useful information.

NLTK provides a pre-compiled list of **179 English stop words** that can be used to filter them out from tokenized text.

#### Code from the Notebook:

```python
from nltk.corpus import stopwords

stop_words = set(stopwords.words('english'))
words = word_tokenize(text)
filtered_words = [w for w in words if w.lower() not in stop_words]
print(filtered_words)
```

#### Input (`text` = `"Python is easy. It is widely used in data science."`):

```
['Python', 'is', 'easy', '.', 'It', 'is', 'widely', 'used', 'in', 'data', 'science', '.']
```

#### Output (after stop word removal):
```
['Python', 'easy', '.', 'widely', 'used', 'data', 'science', '.']
```

Removed: `is`, `It`, `in` — all recognized stop words.

#### Working Logic:

1. Load the English stop words corpus: `stopwords.words('english')`.
2. Convert the list to a `set` for O(1) lookup speed.
3. Tokenize the text into individual words using `word_tokenize()`.
4. Use a **list comprehension** to keep only those words whose lowercase form is **not** in the stop words set.
5. The result contains only content-bearing words (nouns, verbs, adjectives, etc.).

> 💡 **Note:** Punctuation marks like `.` are not stop words — they require separate handling if needed (e.g., filtering by checking `w.isalpha()`).

---

### 4. ✂️ Stemming

#### What is it?

**Stemming** is a text normalization technique that reduces words to their root or base form by chopping off word suffixes using heuristic rules. The resulting "stem" may not be a valid English word — the goal is to group together different inflected forms of the same root.

For example: `Playing → play`, `Running → run`, `Studies → studi` (note: not a real word, but a valid stem).

NLTK implements the **Porter Stemmer** algorithm — one of the oldest and most widely used stemming algorithms, developed by Martin Porter in 1980. It applies a sequence of 5 rule-based reduction passes.

#### Code from the Notebook:

```python
from nltk.stem import PorterStemmer

stemmer = PorterStemmer()

words = ["Playing", "studies", "Running", "gone", "watched", "coding"]
stemmed_words = [stemmer.stem(word) for word in words]
print(stemmed_words)
```

#### Output:
```
['play', 'studi', 'run', 'gone', 'watch', 'code']
```

#### Working Logic:

1. Create a `PorterStemmer` instance.
2. Call `stemmer.stem(word)` on each word — this applies a series of suffix-stripping rules.
3. The stemmer removes suffixes like `-ing`, `-ed`, `-s`, `-es`, `-er` based on its ruleset.
4. The result is a list of stems — some are real words (`play`, `run`), some are truncated forms (`studi`).

#### Stemming Results Breakdown:

| Original Word | Stem | Note |
|---|---|---|
| Playing | play | `-ing` removed |
| studies | studi | `-ies` → `-i` rule |
| Running | run | `-ning` removed (double consonant rule) |
| gone | gone | Irregular — not changed |
| watched | watch | `-ed` removed |
| coding | code | `-ing` removed, `e` restored |

#### ⚠️ Limitation of Stemming:
Stemming can produce non-words (`studi`) and may incorrectly stem words that look similar but have different roots. This is why **Lemmatization** is preferred for tasks requiring linguistic accuracy.

---

### 5. 📖 Lemmatization

#### What is it?

**Lemmatization** is a more sophisticated form of word normalization than stemming. Instead of blindly chopping off suffixes, lemmatization uses a **lexical database** (WordNet) to find the true dictionary base form of a word, called its **lemma**.

For example: `studies → study`, `better → good`, `running → running` (as a noun), `running → run` (as a verb).

The key difference is that lemmatization is **context-aware** and always produces a valid English word.

#### Code from the Notebook:

```python
from nltk.stem import WordNetLemmatizer

lemmatizer = WordNetLemmatizer()

print(lemmatizer.lemmatize("writing"))   # writing
print(lemmatizer.lemmatize("studies"))   # study
print(lemmatizer.lemmatize("coding"))    # coding
print(lemmatizer.lemmatize("best"))      # best
```

#### Output:
```
writing
study
coding
best
```

#### Working Logic:

1. Create a `WordNetLemmatizer` instance.
2. Call `lemmatizer.lemmatize(word)` — by default, it treats the word as a **noun**.
3. WordNet is queried to find the base lemma of the word.
4. If a lemma is found in WordNet's noun database, it is returned. Otherwise, the word is returned unchanged.

#### Lemmatization Results Breakdown:

| Word | Lemma | Reason |
|---|---|---|
| writing | writing | Default is noun — "writing" is already a noun lemma |
| studies | study | Noun lemma of "studies" is "study" |
| coding | coding | No noun lemma found — returned as-is |
| best | best | Default is noun — no change (would return "good" for adjective POS) |

#### 🆚 Stemming vs. Lemmatization:

| Feature | Stemming | Lemmatization |
|---|---|---|
| Method | Rule-based suffix stripping | Lexical database lookup (WordNet) |
| Output | May not be a real word | Always a valid dictionary word |
| Speed | Fast | Slower (needs DB lookup) |
| Accuracy | Lower | Higher |
| Context-aware | No | Yes (with POS tag input) |
| Example: `studies` | `studi` | `study` |
| Best for | Search engines, IR | Chatbots, language models, NLU |

---

### 6. 🏷️ Part-of-Speech (POS) Tagging

#### What is it?

**Part-of-Speech (POS) tagging** assigns a grammatical label to each word in a sentence — identifying whether each word is a noun, verb, adjective, adverb, pronoun, etc. POS tagging is a critical step in understanding the grammatical structure of text and is used in Named Entity Recognition, dependency parsing, and information extraction.

NLTK uses the **Averaged Perceptron Tagger**, a machine learning-based tagger trained on the Penn Treebank corpus. It assigns Penn Treebank POS tags (e.g., `NNP`, `VBZ`, `JJ`, `DT`) to each token.

#### Code from the Notebook:

```python
from nltk import pos_tag
from nltk.tokenize import word_tokenize

words = word_tokenize("Python is a powerful programming language")
pos_tags = pos_tag(words)
print(pos_tags)
```

#### Output:
```
[('Python', 'NNP'), ('is', 'VBZ'), ('a', 'DT'), ('powerful', 'JJ'), ('programming', 'NN'), ('language', 'NN')]
```

#### Output Interpretation:

| Token | POS Tag | Meaning |
|---|---|---|
| Python | NNP | Proper Noun, Singular |
| is | VBZ | Verb, 3rd person singular present |
| a | DT | Determiner |
| powerful | JJ | Adjective |
| programming | NN | Noun, Singular |
| language | NN | Noun, Singular |

#### Working Logic:

1. Tokenize the sentence into a list of words using `word_tokenize()`.
2. Pass the token list to `pos_tag(words)`.
3. The Averaged Perceptron Tagger processes each token in context, using surrounding words to determine the most likely POS tag.
4. Returns a list of `(token, tag)` tuples.

---

### 7. 📊 Word Frequency Distribution

#### What is it?

**Frequency Distribution** counts how many times each unique word appears in a given text. It is a fundamental operation in text analytics, used to identify the most common terms, build word clouds, compute TF-IDF scores, and understand topic distributions.

NLTK's `FreqDist` class creates a frequency distribution object from a list of tokens. It behaves like a Python dictionary but adds useful methods like `.most_common()`, `.plot()`, and `.tabulate()`.

#### Code from the Notebook:

```python
from nltk.probability import FreqDist

words = word_tokenize(text)
fd = FreqDist(words)
print(fd.most_common())
```

#### Input (`text` = `"Python is easy. It is widely used in data science."`):

#### Output:
```
[('is', 2), ('.', 2), ('Python', 1), ('easy', 1), ('It', 1), ('widely', 1), ('used', 1), ('in', 1), ('data', 1), ('science', 1)]
```

#### Working Logic:

1. Tokenize the text into words using `word_tokenize()`.
2. Pass the token list to `FreqDist(words)` — this creates a frequency dictionary internally.
3. Call `.most_common()` to get a list of `(word, count)` tuples sorted in descending order of frequency.
4. Words appearing more frequently appear first in the list.

#### Key `FreqDist` Methods:

| Method | Description |
|---|---|
| `fd.most_common(n)` | Returns the top `n` most frequent words |
| `fd.most_common()` | Returns all words sorted by frequency |
| `fd['word']` | Returns the count of a specific word |
| `fd.plot(n)` | Plots a frequency distribution bar chart |
| `fd.tabulate()` | Prints a tabulated view of frequencies |
| `fd.N()` | Total number of tokens |
| `fd.B()` | Number of unique word types (vocabulary size) |

---

## 📋 POS Tag Definitions Table

The following tags are from the **Penn Treebank POS Tagset**, used by NLTK's `pos_tag()` function:

| # | POS Tag | Full Name | Example Words |
|---|---|---|---|
| 01 | `NNP` | Proper Noun, Singular | London, Microsoft, Python |
| 02 | `NNPS` | Proper Noun, Plural | Vikings, Alps |
| 03 | `NN` | Noun, Singular or Mass | bicycle, air, language |
| 04 | `NNS` | Noun, Plural | bicycles, mountains, languages |
| 05 | `VB` | Verb, Base Form | write, take, go |
| 06 | `VBZ` | Verb, 3rd Person Singular Present | writes, takes, goes |
| 07 | `VBP` | Verb, Non-3rd Person Singular Present | write, take, go |
| 08 | `VBD` | Verb, Past Tense | wrote, took, went |
| 09 | `VBG` | Verb, Gerund / Present Participle | writing, taking, going |
| 10 | `VBN` | Verb, Past Participle | written, taken, gone |
| 11 | `JJ` | Adjective | green, large, powerful |
| 12 | `JJR` | Adjective, Comparative | greener, larger, faster |
| 13 | `JJS` | Adjective, Superlative | greenest, largest, fastest |
| 14 | `RB` | Adverb | quickly, extremely, easily |
| 15 | `RBR` | Adverb, Comparative | more quickly, faster |
| 16 | `RBS` | Adverb, Superlative | most quickly, fastest |
| 17 | `DT` | Determiner | the, a, an, this, every |
| 18 | `PRP` | Personal Pronoun | I, he, she, it, they |
| 19 | `PRP$` | Possessive Pronoun | my, his, her, its, their |
| 20 | `IN` | Preposition / Subordinating Conjunction | in, of, during, after, because |
| 21 | `CC` | Coordinating Conjunction | and, but, or, yet, so |
| 22 | `CD` | Cardinal Number | one, two, 2026, 100 |
| 23 | `MD` | Modal Auxiliary | can, should, will, must, could |
| 24 | `WP` | Wh-Pronoun | who, what, which |
| 25 | `WDT` | Wh-Determiner | which, that |
| 26 | `WRB` | Wh-Adverb | where, when, why, how |
| 27 | `EX` | Existential There | there (as in "there is") |
| 28 | `FW` | Foreign Word | et al., versus |
| 29 | `UH` | Interjection | oh, wow, hey, alas |
| 30 | `TO` | to (infinitive marker) | to (as in "to go") |
| 31 | `RP` | Particle | up, off, out (in phrasal verbs) |
| 32 | `SYM` | Symbol | %, $, &, +, = |
| 33 | `POS` | Possessive Ending | 's (as in "John's") |
| 34 | ```` | Opening Quotation Mark | `` |
| 35 | `''` | Closing Quotation Mark | '' |

---

## ⚙️ Algorithm — Step-by-Step Logic

### Step 1 — Setup & NLTK Data Download
1. Import `nltk`.
2. Download required corpora and models: `punkt`, `punkt_tab`, `stopwords`, `wordnet`, `averaged_perceptron_tagger`, `averaged_perceptron_tagger_eng`.

### Step 2 — Word Tokenization
1. Import `word_tokenize` from `nltk.tokenize`.
2. Define a sample text string.
3. Call `word_tokenize(text)` to split the text into individual word tokens.
4. Print the resulting list of tokens.

### Step 3 — Sentence Tokenization
1. Import `sent_tokenize` from `nltk.tokenize`.
2. Define a multi-sentence text string.
3. Call `sent_tokenize(text)` to split the text into individual sentences.
4. Print the resulting list of sentence strings.

### Step 4 — Stop Word Removal
1. Import `stopwords` from `nltk.corpus`.
2. Load the English stop word list: `stopwords.words('english')`.
3. Convert the list to a `set` for fast lookup.
4. Tokenize the text using `word_tokenize()`.
5. Filter the token list using a list comprehension — retain only tokens whose lowercase form is **not** in the stop words set.
6. Print the filtered word list.

### Step 5 — Stemming
1. Import `PorterStemmer` from `nltk.stem`.
2. Instantiate the stemmer: `stemmer = PorterStemmer()`.
3. Define a list of words with various inflections.
4. Apply `stemmer.stem(word)` to each word in the list using a list comprehension.
5. Print the list of stemmed words.

### Step 6 — Lemmatization
1. Import `WordNetLemmatizer` from `nltk.stem`.
2. Instantiate the lemmatizer: `lemmatizer = WordNetLemmatizer()`.
3. Call `lemmatizer.lemmatize(word)` on individual words.
4. Print each lemma to observe the difference from the original word and from stemming.

### Step 7 — POS Tagging
1. Download `averaged_perceptron_tagger` and `averaged_perceptron_tagger_eng` from NLTK.
2. Import `pos_tag` from `nltk`.
3. Tokenize a new sentence using `word_tokenize()`.
4. Call `pos_tag(words)` on the token list.
5. Print the list of `(token, POS_tag)` tuples.
6. Interpret each tag using the Penn Treebank POS Tagset reference.

### Step 8 — Word Frequency Distribution
1. Import `FreqDist` from `nltk.probability`.
2. Tokenize the text using `word_tokenize()`.
3. Create a frequency distribution object: `fd = FreqDist(words)`.
4. Call `fd.most_common()` to get all words sorted by frequency.
5. Print the results — words with the highest counts appear first.

---

## 🗂️ Functions & Commands Reference Table

| Function / Command | Library / Module | Description |
|---|---|---|
| `nltk.download('package')` | `nltk` | Downloads a specific NLTK data package |
| `word_tokenize(text)` | `nltk.tokenize` | Splits text into individual word tokens |
| `sent_tokenize(text)` | `nltk.tokenize` | Splits text into individual sentence tokens |
| `stopwords.words('english')` | `nltk.corpus` | Returns a list of 179 English stop words |
| `set(stop_words)` | Python built-in | Converts list to set for O(1) lookup |
| `PorterStemmer()` | `nltk.stem` | Creates a Porter Stemmer instance |
| `stemmer.stem(word)` | `nltk.stem` | Applies Porter stemming rules to a word |
| `WordNetLemmatizer()` | `nltk.stem` | Creates a WordNet Lemmatizer instance |
| `lemmatizer.lemmatize(word)` | `nltk.stem` | Returns the lemma of a word (default: noun) |
| `lemmatizer.lemmatize(word, pos='v')` | `nltk.stem` | Lemmatizes treating the word as a verb |
| `pos_tag(tokens)` | `nltk` | Tags each token with a Penn Treebank POS label |
| `FreqDist(words)` | `nltk.probability` | Creates a word frequency distribution object |
| `fd.most_common(n)` | `nltk.probability` | Returns top `n` words by frequency |
| `fd.plot(n)` | `nltk.probability` | Plots a frequency distribution chart |

---

## 📊 Charts & Visualization

NLTK's `FreqDist` provides a built-in `.plot()` method for visualizing word frequencies:

```python
from nltk.probability import FreqDist
import matplotlib.pyplot as plt

words = word_tokenize("Python is easy. It is widely used in data science.")
fd = FreqDist(words)

# Plot top 10 most frequent words
fd.plot(10, title='Top 10 Word Frequencies', cumulative=False)
plt.show()
```

This generates a **bar chart** showing the most frequent words on the x-axis and their counts on the y-axis — useful for quick exploratory text analysis.

---

## 🛠️ Tools & Technologies Used

| Tool / Library | Purpose |
|---|---|
| **Python 3.x** | Core programming language |
| **NLTK** | NLP tokenization, stemming, lemmatization, POS tagging, frequency analysis |
| **Google Colab** | Cloud-based Jupyter Notebook execution environment |
| **Jupyter Notebook** | Interactive code and output presentation |

---

## 💡 Applications of NLP Techniques

The techniques covered in this experiment form the backbone of virtually every real-world NLP system:

- **Search Engines:** Tokenization breaks search queries into terms; stemming and lemmatization ensure that `"running"`, `"ran"`, and `"run"` all retrieve the same results. Stop word removal reduces the index size.

- **Sentiment Analysis:** After tokenization and stop word removal, the remaining content words are analyzed for positive/negative sentiment — powering product review analysis, social media monitoring, and customer feedback systems.

- **Chatbots & Virtual Assistants:** POS tagging helps chatbots understand the grammatical structure of user queries, enabling them to extract intent and entities correctly.

- **Text Classification & Spam Detection:** Frequency distributions and bag-of-words models built from tokenized, filtered, and stemmed text are the foundation of email spam classifiers and topic categorizers.

- **Machine Translation:** Lemmatization and POS tagging are essential preprocessing steps in rule-based and statistical machine translation systems.

- **Information Retrieval & Summarization:** Stop word removal, stemming, and frequency analysis identify the most important terms in a document, enabling automatic summarization and keyword extraction.

- **Medical & Legal NLP:** POS tagging and lemmatization help extract clinically relevant entities (diagnoses, medications, dates) from medical records and legal documents.

---

## ✅ Conclusion

This experiment successfully implemented the fundamental NLP preprocessing pipeline in Python using the NLTK library. The following techniques were demonstrated and verified:

**Word Tokenization** correctly split a raw string into a list of individual word tokens using NLTK's Punkt tokenizer — producing `['Natural', 'Language', 'Processing', 'is', 'interesting']` from a simple sentence.

**Sentence Tokenization** intelligently split a multi-sentence paragraph into individual sentence strings, correctly identifying sentence boundaries even around punctuation.

**Stop Word Removal** used NLTK's English stop words corpus to filter out common uninformative words (`is`, `it`, `in`) from a tokenized list, retaining only meaningful content words.

**Stemming** with the Porter Stemmer reduced inflected words to their root forms — `Playing → play`, `Running → run`, `studies → studi` — demonstrating that stems may not always be valid English words.

**Lemmatization** with the WordNet Lemmatizer produced true dictionary base forms — `studies → study` — showing greater linguistic accuracy over stemming, at the cost of speed.

**POS Tagging** correctly identified the grammatical role of each token in a sentence — `Python` as `NNP` (Proper Noun), `powerful` as `JJ` (Adjective), `language` as `NN` (Noun) — using NLTK's Averaged Perceptron Tagger.

**Word Frequency Distribution** computed and ranked word occurrences in the text, revealing that `is` and `.` appeared twice (most frequent), while all other content words appeared once — a typical pattern in short sentences.

Together, these techniques form the essential preprocessing pipeline that powers modern NLP applications, from search engines and chatbots to sentiment analysis and machine translation.

---

## 📝 Extra Notes

> **⚠️ Why `lemmatizer.lemmatize("writing")` returns `"writing"` and not `"write"`?**
>
> By default, `WordNetLemmatizer.lemmatize()` treats every word as a **noun**. "Writing" as a noun is already in its base form (it's a gerund-noun). To get `"write"`, you must specify the POS as verb:
> ```python
> lemmatizer.lemmatize("writing", pos='v')  # Returns: write
> ```
> This is why combining POS tagging with lemmatization gives the most accurate results.

> **💡 Difference Between `punkt` and `punkt_tab`**
>
> `punkt` is the original NLTK Punkt tokenizer data. `punkt_tab` is a newer, tab-separated format of the same data required by NLTK versions ≥ 3.8. Both must be downloaded in modern environments like Google Colab to avoid `LookupError`.

> **🔍 Stop Words are Language-Specific**
>
> NLTK provides stop word lists for many languages: English, French, German, Spanish, Hindi, and more. To use a different language: `stopwords.words('french')`. You can also define your own custom stop words by extending the default set with additional domain-specific terms.

> **📌 NLP Pipeline Summary**

```
Raw Text
   ↓
[Sentence Tokenization]   →  Split into sentences
   ↓
[Word Tokenization]        →  Split into tokens
   ↓
[Stop Word Removal]        →  Remove noise words
   ↓
[Stemming / Lemmatization] →  Normalize word forms
   ↓
[POS Tagging]              →  Identify grammatical roles
   ↓
[Frequency Distribution]   →  Count & rank tokens
   ↓
Ready for Model Input ✅
```

---

*README generated for academic and GitHub documentation purposes — Experiment 15, EnTC A3 Batch.*
