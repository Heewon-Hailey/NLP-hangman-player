# Language model in hangman

## About the project

This work implements automatic players for Hangman game. The players have several different automatic strategies based on character-level n-gram language models. The players aim to make the fewest mistakes.

<br>

## Background 

The Hangman game is a simple game whereby one person thinks of a word, which they keep secret from their opponent, who tries to guess the word one character at a time. The game ends when the opponent makes more than a fixed number of incorrect guesses, or they figure out the secret word before then (in which case they win).

<br>

## Datasets

NLTK's Brown corpus is used from `nltk.corpus.brown` to generate a dataset that contains unique words comprised of alphabetic characters only. The words are lowercased, then randomly shuffle before spliting them into two datasets for train and test. 1,000 words are assigned into a test set meanwhile the remaining words (39,234 in this case) are split into train set. 

<br>

## Implemented algorithms 

* **Random model** randomly chooses a character from a-z excluding already guessed characters. 

* **Unigram language model** returns a character which are the most frequently observed over the training set. Again, it excludes already guessed characters. 

* **Conditional unigram language model** uses the clue from the length of the secret word to select a character with the highest frequency. It has a different frequency unigram model for each length. It handles unseen conditions (word lengths) by behaving like **Unigram language model**. Again, it excludes already guessed characters. 

* **Bigram language model** uses the order of characters in the secret word. It considers the left context charater of each blank position. If the left context is unknown, it behaves like **Unigram language model**. Over all alphabets, it computes total sum of the probability distribution for the blanks to return a character with the highest probability. Again, it excludes already guessed characters. 

* **Effective model** is designed by myself considering multiple concepts that includes interpolation, add-k smoothing, n-grams, and bidirectional techniques. It applies add-k smoothing and interpolation to handle unseen events in test dataset; k value (0.01). In bidirectional methods, unigram , bigram and trigram are used with different importance weights; gamma values(0.1 : 0.2 : 0.7). It eventually sums up the probabilities of each alphabet per each blank. Then, it chooses a character with the highest probability. Again, it excludes already guessed characters. 
 
  To evaluate its performance, different training/test splits are attempted.

<br>

## Version
Python 3.7.11<br>
Numpy 1.19.5<br>
NLTK 3.6.7<br>

<br>

---
H _ V E :question: :a::exclamation: <br>
F U N 😉

