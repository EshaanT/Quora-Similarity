# Quora-Similarity
Quora is filled with questions, and it is easy to find sets of questions in quora that are seeking the same thing but are worded differently. This project aims to find such pair of “duplicate” questions using a deep learning model.

# Dataset
I made use of the [Question Pairs Dataset](https://www.kaggle.com/quora/question-pairs-dataset)
The pre-process steps undertook were
* lower casing
* lemmatization
* removal of punctuations

(presence of stopword was beneficial for the model)

# Model

This project made use of the concept of [siamese network](https://medium.com/@enoshshr/learning-similarity-with-siamese-neural-networks-51c9ef534ae4).

The network consisted of Bi-LSTM followed by a couple of dense layers. Pair of questions were passed through this network (separately) and the pair of vectors so produced was then used to extract two features.
* Sum of differences of the vectors (Manhattan distance)
* Dot product of the vectors ( Loosely based on cosign similarity)

These were further fed to a couple of dense layers to produce a final probabilistic score of the pair of questions being duplicate or not.
