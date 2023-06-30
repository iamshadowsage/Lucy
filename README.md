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

Main goal of this Project is to Implement a working voice assistant in Tamil Language , as current assistants lack fluency and accuracy in a conversation.<br>

And i also wanna implement an ml algorithm that would increase the accuracy of the model when mimicking Human Conversation Pattern.<br>

In this Project , I took the first part which is "Speech To Text Engine", i wanna implement this without any external frameworks and mainly only with C++ as optimization of algorithms Plays a crucial part in this project .<br>

The Proposed Speech Recognition System Consists of, <br>

1.Feature Extraction.<br>
2.Feature Mapping.<br>
3.Ngram Model for Prediction of Letters and Words.<br>


<h3>1.Feature Extraction</h3>

Firstly i have extracted the features of all audio files that contain specific tamil letter.<br>
I have Extracted features such as freuqency, amplitude, Energy, Spectral Centroid. <br>
I recorded the tamil letters in 16khz myself.<br>
For Feature Extraction Process ,<b> MFCC</b> And <b>PLP</b> Algorithms are used,<br>

MFCC - Mel Frequency Cepstral Coefficients<br>
PLP - Perceptual Linear Prediction<br>

Most Speech Recognition Systems use MFCC as their goto approach for feature extraction.<br>
While MFCC is for most environments , it is not suited for noisy environments .<br>

So to Recognize words even in a noisy environment , I have Used PLP along with MFCC.<br>
For PLP , Dataset is recorded from noisy environments.<br>

<h4>Currently The Project Has been done upto this part.</h4>

Pending Works , 

<h3>2.Feature Mapping</h3>

As we have already Extracted the features of letters in tamil,<br>
I'm thinking of using a Deep Neural Network to Map The Extracted Features to the Tamil Letters.<br>
Particularly , <b>LSTM</b> (Long Short Term Memory)<br>

Input : Realtime audio
Output : Recognized Letters

<h3>3.NGram Model</h3><br>

To Increase the Accuracy  , I have planned to use an NGram model.<br>
For a sentence, suppose if you have the sentence "எங்கு போகிறாய் நீ?" (Where are you going?). <br>
To predict the next word, you can use the Ngram model to calculate the probability of each possible word that can follow the previous words.<br>
The word with the highest probability is then chosen as the prediction for the next word.<br>

To get maximum accuracy ,<b> Kneser-ney Smoothing</b> Algorithm will be used.<br>

Before Knowing Kneser-Ney Smoothing ,  lets understand what bigram is,<br>
A bigram refers to a sequence of two consecutive words or tokens in a given text. <br>
It is a higher-level linguistic unit compared to a unigram and can capture some contextual information by considering the relationship between adjacent words.
And the same goes for N numbers.<br>

The Kneser-Ney smoothing algorithm works as follows:<br>

Count the number of times each word appears in the training corpus to compute the unigram probabilities.<br>

Compute the bigram probabilities as follows:<br>
for each word, count the number of times it appears as the second word in a bigram. <br>
Divide this count by the number of times the first word appears in the corpus to get the conditional probability of the second word given the first word.<br>

Compute the trigram probabilities as follows:<br>
for each bigram, count the number of times it appears as the second word in a trigram. <br>
Divide this count by the number of times the first two words appear as a bigram to get the conditional probability of the third word given the first two words.<br>

Smooth the bigram and trigram probabilities using the Kneser-Ney method. <br>
The basic idea of Kneser-Ney smoothing is to use the probability of a word being a novel continuation of a bigram to discount its probability. <br>
This probability is estimated using the number of distinct words that follow the bigram in the training corpus.<br>
The smoothed probability of a word given the previous words is then a weighted combination of the unigram, bigram, and trigram probabilities.<br>

