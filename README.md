# WordEmbedding
Word Embeddings with GoogleNews Word2Vec

Overview

This project utilizes the pre-trained GoogleNews Word2Vec model to perform various Natural Language Processing (NLP) tasks, such as finding word similarities, performing word analogies, and obtaining word vectors.

Requirements

Before running the code, ensure you have the following installed:

Python (>=3.7)

Gensim

NumPy

To install the necessary dependencies, run:

pip install gensim numpy

Downloading the GoogleNews Word2Vec Model

The pre-trained GoogleNews-vectors-negative300.bin file contains 3 million word vectors, each represented as a 300-dimensional vector. Due to its large size (~1.5GB), it is not included in this repository. You can download it from:

GoogleNews Word2Vec

Alternative: Pre-trained Word2Vec models

After downloading, place the GoogleNews-vectors-negative300.bin file in your project directory.

Loading the Model

Use the following code to load the model:

from gensim.models import KeyedVectors

# Load pre-trained Word2Vec model
word_vectors = KeyedVectors.load_word2vec_format(
    'GoogleNews-vectors-negative300.bin', binary=True
)

Using Word Embeddings

Once loaded, you can perform various operations:

1. Get Word Vector

vector = word_vectors['king']
print(vector.shape)  # Output: (300,)

2. Find Similar Words

print(word_vectors.most_similar('king'))

3. Compare Word Similarity

similarity = word_vectors.similarity('king', 'queen')
print(similarity)  # Output: 0.78 (high similarity)

4. Perform Word Analogies (Word Math)

result = word_vectors.most_similar(positive=['king', 'woman'], negative=['man'])
print(result)  # Expected output: [('queen', 0.78), ...]

Notes

The GoogleNews Word2Vec model is trained on 100 billion words from news articles.

It uses the Skip-gram approach with 300-dimensional embeddings.

The model does not handle out-of-vocabulary (OOV) words.

License

This project uses the GoogleNews Word2Vec model, which is subject to Google’s terms of use.
