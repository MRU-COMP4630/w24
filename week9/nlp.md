---
marp: true
paginate: true
theme: marp-theme
math: true
---

<!-- 
_class: invert lead
_paginate: skip
 -->

# Natural Language Processing

COMP 4630 | Winter 2024
Charlotte Curtis

---

## Overview

- Text to tokens
- Tokens to embeddings
- Embeddings to predictions
- References and suggested reading:
    - [Scikit-learn book](https://librarysearch.mtroyal.ca/discovery/fulldisplay?context=L&vid=01MTROYAL_INST:02MTROYAL_INST&search_scope=MRULibrary&isFrbr=true&tab=MRULibraryResources&docid=alma9923265933604656): Chapter 16
    - [Deep Learning Book](https://www.deeplearningbook.org/): Chapter 12

---

## Tokenization
- Consider the sentence:

    > "The cat sat on the mat."

- This can be split up into individual words or **tokens**:

    > ["The", "cat", "sat", "on", "the", "mat", "."]

- :question: what other ways could we tokenize this sentence?
- :question: what about punctuation, capitalization, etc.?

---

## RNN + tokens: predict the next character
- Just like predicting the next day's weather or stock price, we can predict the next character in a sentence using an RNN
- Input tokens: `['T', 'h', 'e', ' ', 'c', 'a', 't', ' ', 's', 'a', 't', ' ', 'o', 'n', ' ', 't', 'h', 'e', ' ', 'm', 'a', 't', '.']`
- Numeric representation: `[20, 8, 5, 0, 3, 1, 20, 0, 19, 1, 20, 0, 15, 14, 0, 20, 8, 5, 0, 13, 1, 20, 2]`
- We could train an RNN model to predict the next character
- For more info check out [Andrej Karpathy's blog post](http://karpathy.github.io/2015/05/21/rnn-effectiveness/), one of the sources for the Scikit-learn chapter

---

## Repeatedly predicting the next character
- To predict whole sentences from a starting point, we can predict the next character and append it to the input, then predict again
- In practice this tends to get stuck in loops:
    Input: `"to be or not"`
    Output: `"to be or not to be or not to be or not..."`
- :question: how might we avoid this?
- :question: could we just predict the next whole word instead?

---

## In the beginning, there were $n$-grams
- A simple way to represent text is as a bag of $n$-grams
- unigram: single words (aka "Bag of Words"):
    > ["the", "cat", "sat", "on", "the", "mat"]
- bigram: pairs of words:
    > ["the cat", "cat sat", "sat on", "on the", "the mat"]
- trigram: triples of words:
    > ["the cat sat", "cat sat on", "sat on the", "on the mat"]

---

## Predictive text with $n$-grams
- Given a sequence of tokens, we can predict the probability of the $n$th token given the previous $n-1$ tokens:
    $$P(x_1, \ldots, x_\tau) = P(x_1, \ldots, x_{\tau-1}) \prod_{t=n}^{\tau} P(x_t | x_{t-n+1}, \ldots, x_{t-1})$$

- Each of these conditional probabilities can be estimated from the frequency of the $n$-grams in a **corpus**
- The most likely next word is the one with the highest probability
- :question: What are some limitations of this approach?

---

## $n$-grams challenges
- $n$-grams lose the meaning of words:
    - "The cat sat on the mat"
    - "The dog sat on the rug"
- Also subject to the **curse of dimensionality**
    - Vocabulary $\mathbb{V}$ with size $|\mathbb{V}|$ leads to $|\mathbb{V}|^n$ possible $n$-grams
    - Most $n$-grams will not be present in the corpus!
- Language models need to be able to **generalize**
- :question: How can we represent words in a way that captures their meaning?

---

## Side note: The curse of dimensionality
- Data is often represented as $n$ samples with $p$ features each
- As $p$ increases, the number of samples required to cover the space increases exponentially
- Also called $p \gg n$ problem
  ![h:300 center](figs/cursed.png)

<footer>Figure 5.9 from the Deep Learning Book</footer>

---

## Word embeddings

- Solution: represent individual words as vectors, or **embeddings**
- :question: How are these embeddings defined?

    <div class="columns">

    | Word | Embedding |
    |------|-----------|
    | cat  | `[0.2, 0.3, 0.5]` |
    | dog  | `[0.1, 0.4, 0.4]` |
    | mat  | `[0.5, 0.2, 0.2]` |
    | rug  | `[0.4, 0.1, 0.1]` |

    ![](figs/embedding_space.png)

    </div>

---

## Learning word embeddings
- Tomorrow we'll discuss the influential **Word2Vec** paper
- The concept was first presented successfully by [Bengio in 2001](https://proceedings.neurips.cc/paper_files/paper/2000/hash/728f206c2a01bf572b5940d7d9a8fa4c-Abstract.html)
  ![center h:350](figs/bengio.png)

---

## So we have embeddings, now what?

- We can use these embeddings as input to a neural network
- Applications:
    - **Sentiment analysis**: is a review/tweet/comment positive or negative?
    - **Named entity recognition**: who/what is mentioned in a text?
    - **Machine translation**: convert text from one language to another
    - **Predictive text**: what word comes next?
    - **Text generation**: create new text based on a given input

---

## Sentiment analysis
General pipeline:
- Standardize and tokenize the text
- Add an embedding layer (trainable or pre-trained)
- Add a recurrent layer, such as a GRU
- Add a dense layer with sigmoid activation

To [Colab](https://colab.research.google.com/drive/1zZj0s09NGrTj3QJZfTmeE2tINwWezshQ?usp=sharing)!

---

<!-- 
_class: invert lead
_paginate: skip
 -->

## Next up: Encoder/decoder models and attention mechanisms
