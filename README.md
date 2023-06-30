# Lucy
University Mini Project

As a Part of my university miniproject , I chose to do a virtual voice assistant , 
From now on i will refer her as Lucy.
I went through a lot of time to discover the working principle of a voice assistant and its functions.

let's know how it works , 

Normally a Voice Assistant consists of,

1.Speech To Text Engine (STT)<br>
2.NLP Processor<br>
3.Text To Speech (TTS)<br>

Main goal of this Project is to Implement a working voice assistant in Tamil Language , as current assistants lack fluency and accuracy in a conversation.

And i also wanna implement an ml algorithm that would increase the accuracy of the model when mimicking Human Conversation Pattern.

In this Project , I took the first part which is "Speech To Text Engine", i wanna implement this without any external frameworks and mainly only with C++ as optimization of algorithms Plays a crucial part in this project .

The Proposed Speech Recognition System Consists of, 

1.Feature Extraction.<br>
2.Feature Mapping.<br>
3.Ngram Model for Prediction of Letters and Words.<br>



#1.Feature Extraction

Firstly i have extracted the features of all audio files that contain specific tamil letter.
I have Extracted features such as freuqency, amplitude, Energy, Spectral Centroid. 
I recorded the tamil letters in 16khz myself.
For Feature Extraction Process , MFCC And PLP Algorithms are used,

MFCC - Mel Frequency Cepstral Coefficients
PLP - Perceptual Linear Prediction

Most Speech Recognition Systems use MFCC as their goto approach for feature extraction.
While MFCC is for most environments , it is not suited for noisy environments .

So to Recognize words even in a noisy environment , I have Used PLP along with MFCC.
For PLP , Dataset is recorded from noisy environments.

#Currently The Project Has been done upto this part.

Pending Works , 

#2.Feature Mapping

As we have already Extracted the features of letters in tamil,
I'm thinking of using a Deep Neural Network to Map The Extracted Features to the Tamil Letters.
Particularly , LSTM (Long Short Term Memory)

Input : Realtime audio
Output : Recognized Letters

#3.NGram Model

To Increase the Accuracy  , I have planned to use an NGram model.
For a sentence, suppose if you have the sentence "எங்கு போகிறாய் நீ?" (Where are you going?). 
To predict the next word, you can use the Ngram model to calculate the probability of each possible word that can follow the previous words.
The word with the highest probability is then chosen as the prediction for the next word.

To get maximum accuracy , Kneser-ney Smoothing Algorithm will be used.

Before Knowing Kneser-Ney Smoothing ,  lets understand what bigram is,
A bigram refers to a sequence of two consecutive words or tokens in a given text. 
It is a higher-level linguistic unit compared to a unigram and can capture some contextual information by considering the relationship between adjacent words.
and the same goes for N numbers.

The Kneser-Ney smoothing algorithm works as follows:

Count the number of times each word appears in the training corpus to compute the unigram probabilities.
Compute the bigram probabilities as follows:
for each word, count the number of times it appears as the second word in a bigram. 
Divide this count by the number of times the first word appears in the corpus to get the conditional probability of the second word given the first word.

Compute the trigram probabilities as follows:
for each bigram, count the number of times it appears as the second word in a trigram. 
Divide this count by the number of times the first two words appear as a bigram to get the conditional probability of the third word given the first two words.

Smooth the bigram and trigram probabilities using the Kneser-Ney method. 
The basic idea of Kneser-Ney smoothing is to use the probability of a word being a novel continuation of a bigram to discount its probability. 
This probability is estimated using the number of distinct words that follow the bigram in the training corpus.
The smoothed probability of a word given the previous words is then a weighted combination of the unigram, bigram, and trigram probabilities.

