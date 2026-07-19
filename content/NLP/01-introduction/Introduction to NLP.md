---
title: Introduction to Natural Language Processing (NLP)
description: Comprehensive notes covering the foundations, history, pipeline, challenges, and applications of Natural Language Processing.
tags:
  - NLP
  - Artificial Intelligence
  - Machine Learning
  - Deep Learning
  - Linguistics
draft: false
---

# Introduction to Natural Language Processing (NLP)

> **Natural Language Processing (NLP)** is a branch of Artificial Intelligence (AI) that enables computers to understand, interpret, generate, and interact with human language.

NLP combines concepts from:

- Artificial Intelligence
- Machine Learning
- Deep Learning
- Computational Linguistics
- Statistics
- Information Theory
- Cognitive Science

The ultimate goal is to bridge the communication gap between humans and machines.

---

# What is Natural Language?

A **natural language** is any language developed naturally by humans over time.

Examples include:

- English
- Tamil
- Sinhala
- French
- Japanese
- Arabic

Natural languages differ from formal languages (such as programming languages) because they contain:

- Ambiguity
- Context
- Idioms
- Slang
- Cultural references
- Multiple meanings

Example:

> I saw a man with a telescope.

Possible interpretations:

1. I used a telescope.
2. The man had the telescope.

Humans understand the intended meaning using context.

Computers require algorithms to infer it.

---

# Why NLP is Important

Every day humans generate enormous amounts of text.

Sources include:

- Emails
- Books
- Websites
- News
- Medical records
- Research papers
- Chat applications
- Social media
- Voice assistants

Over **80% of enterprise data is unstructured text**, making NLP essential for extracting useful information.

Applications include:

- Search engines
- Recommendation systems
- Chatbots
- Virtual assistants
- Machine translation
- Healthcare
- Finance
- Education
- Robotics

---

# Goals of NLP

The primary objectives include:

- Understanding language
- Generating language
- Extracting knowledge
- Translating languages
- Answering questions
- Summarizing documents
- Conversational AI
- Speech understanding
- Information retrieval

---

# NLP vs Computational Linguistics

| NLP | Computational Linguistics |
|------|---------------------------|
| Engineering-oriented | Science-oriented |
| Builds intelligent systems | Studies language mathematically |
| Uses AI and ML | Uses linguistic theories |
| Practical applications | Language understanding |

---

# NLP vs Text Mining

| NLP | Text Mining |
|------|-------------|
| Understands language | Extracts useful patterns |
| Grammar-aware | Data-driven |
| Focuses on semantics | Focuses on analytics |

---

# Evolution of NLP

## Rule-Based Era (1950–1990)

Characteristics

- Handwritten grammar rules
- Dictionaries
- Expert systems
- Symbolic AI

Example

```
IF word == "cat"
THEN animal = True
```

Advantages

- Explainable
- Predictable

Disadvantages

- Difficult to scale
- Poor generalization

---

## Statistical NLP (1990–2012)

Introduced probability.

Examples

- Hidden Markov Models (HMM)
- Conditional Random Fields (CRF)
- Maximum Entropy Models
- Naive Bayes

Instead of rules,

```
P(tag | word)
```

was estimated from data.

Advantages

- Better accuracy
- Learns from data

Limitations

- Heavy feature engineering
- Limited context

---

## Deep Learning Era (2013–2018)

Neural networks replaced handcrafted features.

Models include

- Feedforward Networks
- CNN
- RNN
- LSTM
- GRU

Advantages

- Learns features automatically
- Better contextual understanding

---

## Transformer Era (2018–Present)

The Transformer architecture revolutionized NLP.

Popular models:

- BERT
- GPT
- RoBERTa
- T5
- BART
- LLaMA
- Qwen
- Gemma
- DeepSeek
- Mistral

Advantages

- Parallel computation
- Long-range dependency modeling
- Self-attention mechanism
- Massive pretraining

---

# NLP Pipeline

```
Raw Text
    │
    ▼
Cleaning
    │
    ▼
Tokenization
    │
    ▼
Normalization
    │
    ▼
Stopword Removal
    │
    ▼
Stemming / Lemmatization
    │
    ▼
POS Tagging
    │
    ▼
Parsing
    │
    ▼
NER
    │
    ▼
Relation Extraction
    │
    ▼
Knowledge Representation
    │
    ▼
Application
```

---

# Levels of Language Processing

Natural language contains multiple layers.

```
Pragmatics
Semantics
Syntax
Morphology
Phonology
```

Each level contributes unique information.

---

# Phonology

Studies speech sounds.

Example

```
Cat
```

Pronunciation

```
/kæt/
```

Applications

- Speech recognition
- Speech synthesis

---

# Morphology

Morphology studies the internal structure of words.

Example

```
unhappiness

un
happy
ness
```

Components

| Part | Meaning |
|-------|----------|
| un | Prefix |
| happy | Root |
| ness | Suffix |

---

Example in Tamil

```
படித்தவர்கள்

படி
த்
த
வர்
கள்
```

Morphological analysis is especially important for morphologically rich languages.

---

# Syntax

Syntax defines grammatical structure.

Example

Correct

```
The boy is playing.
```

Incorrect

```
Playing boy the is.
```

Syntax is often represented using parse trees.

---

# Semantics

Semantics focuses on meaning.

Example

```
The bank is closed.
```

Possible meanings

- Financial institution
- River bank

Context determines the correct interpretation.

---

# Pragmatics

Pragmatics studies meaning in context.

Example

```
Can you open the window?
```

Literal meaning

Question about ability.

Pragmatic meaning

A polite request.

---

# Common NLP Tasks

---

## Tokenization

Splits text into smaller units.

Sentence

```
NLP is amazing.
```

Tokens

```
["NLP","is","amazing","."]
```

---

## Sentence Segmentation

```
Hello.

How are you?

I am fine.
```

↓

```
Sentence 1
Sentence 2
Sentence 3
```

---

## Stopword Removal

Common words removed.

Example

```
This is an example sentence.
```

↓

```
example sentence
```

---

## Stemming

Cuts words using heuristic rules.

Examples

```
playing

played

plays
```

↓

```
play
```

Sometimes

```
studies

↓

studi
```

which is incorrect linguistically.

---

## Lemmatization

Produces dictionary words.

```
better

↓

good
```

```
running

↓

run
```

More accurate than stemming.

---

# Part-of-Speech Tagging

Assigns grammatical labels.

Example

```
The cat eats fish.
```

| Word | POS |
|------|------|
| The | DET |
| cat | NOUN |
| eats | VERB |
| fish | NOUN |

---

# Named Entity Recognition (NER)

Identifies entities.

Example

```
Apple hired John in California.
```

Entities

| Entity | Label |
|---------|--------|
| Apple | ORG |
| John | PERSON |
| California | LOCATION |

---

# Dependency Parsing

Finds grammatical relationships.

```
John eats apples.
```

```
eats
├── John
└── apples
```

---

# Constituency Parsing

Groups phrases.

```
[S
 [NP John]
 [VP eats apples]
]
```

---

# Coreference Resolution

Determine references.

```
Mary bought a car.

She loves it.
```

↓

```
She → Mary

it → car
```

---

# Relation Extraction

Extracts structured relationships.

Sentence

```
Steve Jobs founded Apple.
```

↓

```
(Steve Jobs,
 founded,
 Apple)
```

---

# Information Extraction

Combines

- NER
- Relation Extraction
- Event Extraction

Output

Structured knowledge.

---

# Sentiment Analysis

Determines opinions.

Sentence

```
The movie was fantastic.
```

↓

Positive

---

# Topic Modeling

Discovers hidden themes.

Document

```
football
goal
player
stadium
```

↓

Sports

---

# Machine Translation

Example

English

```
Good Morning
```

↓

Tamil

```
காலை வணக்கம்
```

---

# Text Summarization

Input

100-page report

↓

Output

1-page summary

Methods

- Extractive
- Abstractive

---

# Question Answering

Question

```
Who invented Python?
```

↓

```
Guido van Rossum
```

---

# Dialogue Systems

Examples

- ChatGPT
- Claude
- Gemini
- Siri
- Alexa

Tasks include

- Context tracking
- Intent understanding
- Response generation

---

# Word Representation

Early NLP

```
One-Hot Encoding
```

↓

Sparse vectors

Modern NLP

```
Word Embeddings
```

↓

Dense vectors

Examples

- Word2Vec
- GloVe
- FastText

---

# Contextual Embeddings

Unlike Word2Vec,

BERT represents the same word differently depending on context.

Example

```
river bank
```

↓

Embedding A

```
financial bank
```

↓

Embedding B

---

# Transformer Architecture

Main components

```
Input
 │
 ▼
Embedding
 │
 ▼
Positional Encoding
 │
 ▼
Multi-Head Attention
 │
 ▼
Feed Forward Network
 │
 ▼
Output
```

Transformers use **self-attention** instead of recurrence.

---

# Large Language Models (LLMs)

LLMs are Transformer-based models trained on massive text corpora.

Examples

- GPT
- LLaMA
- Gemma
- Mistral
- DeepSeek
- Qwen

Capabilities

- Text generation
- Translation
- Coding
- Summarization
- Reasoning
- Dialogue

---

# Challenges in NLP

## Ambiguity

```
I saw her duck.
```

Meaning?

- Bird
- Action

---

## Polysemy

```
Bank
```

Multiple meanings.

---

## Synonymy

```
Big

Large

Huge
```

Same concept.

---

## Sarcasm

```
Great!

Another meeting.
```

Literal sentiment differs from intended sentiment.

---

## Low-Resource Languages

Examples

- Tamil
- Sinhala
- Nepali

Challenges

- Small datasets
- Limited pretrained models
- Few benchmarks

---

## Code-Mixing

Example

```
நான் office போறேன்.
```

Mix of Tamil and English.

---

# NLP Applications

Healthcare

- Clinical note analysis
- Disease prediction

Finance

- Fraud detection
- News analysis

Education

- Automatic grading
- Intelligent tutoring

Law

- Legal document retrieval

Retail

- Product recommendations

Agriculture

- Crop advisory

Robotics

- Voice commands

Social Media

- Hate speech detection
- Spam detection

Cybersecurity

- Phishing detection

Scientific Research

- Literature mining

---

# Popular NLP Libraries

Python

- NLTK
- spaCy
- Gensim
- Transformers
- Sentence Transformers
- Flair
- AllenNLP
- Stanza
- Haystack
- LangChain
- LlamaIndex

---

# Evaluation Metrics

Classification

- Accuracy
- Precision
- Recall
- F1-score

Language Generation

- BLEU
- ROUGE
- METEOR
- BERTScore

Embeddings

- Cosine Similarity

Question Answering

- Exact Match
- F1

---

# Current Research Trends

- Large Language Models
- Retrieval-Augmented Generation (RAG)
- Agentic AI
- Multimodal AI
- Vision-Language Models
- Knowledge Graphs
- Graph Neural Networks
- Efficient Fine-Tuning (LoRA, QLoRA)
- Long Context Models
- Synthetic Data Generation
- Reinforcement Learning from Human Feedback (RLHF)
- AI Safety
- Explainable NLP

---

# Summary

Natural Language Processing has evolved dramatically:

```
Rule-Based Systems
        ↓
Statistical NLP
        ↓
Machine Learning
        ↓
Deep Learning
        ↓
Transformer Models
        ↓
Large Language Models
```

Modern NLP powers technologies such as search engines, chatbots, machine translation, virtual assistants, document understanding, question answering, and intelligent agents. As transformer architectures and foundation models continue to advance, NLP is moving toward systems capable of deeper reasoning, multilingual understanding, and seamless human-computer interaction.

---

# Recommended Reading

## Books

- Speech and Language Processing — Jurafsky & Martin
- Foundations of Statistical Natural Language Processing
- Natural Language Processing with Transformers

## Papers

- Attention Is All You Need (2017)
- BERT: Pre-training of Deep Bidirectional Transformers (2018)
- GPT-3: Language Models are Few-Shot Learners (2020)
- LoRA: Low-Rank Adaptation of Large Language Models (2021)
- LLaMA: Open and Efficient Foundation Language Models (2023)

---

# Next Topics

- Text Preprocessing
- Regular Expressions
- Tokenization Techniques
- Stemming & Lemmatization
- Part-of-Speech Tagging
- Named Entity Recognition
- Word Embeddings
- Attention Mechanism
- Transformer Architecture
- BERT
- GPT
- Retrieval-Augmented Generation (RAG)
- Vector Databases
- Knowledge Graphs
- Agentic AI