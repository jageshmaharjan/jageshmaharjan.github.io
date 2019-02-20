---
title: "DeepSpeech by Baidu Inc."
date: 2019-02-19
tags: [machine learning, deep learning, ctc, rnn, lstm, language model]
header:
   image: "/images/deepspeech/deepspeech.jpg"
excerpt: "machine learning, deep learning, ctc, rnn, lstm, language model"
---

[DeepSpeech](https://arxiv.org/pdf/1412.5567.pdf) came all the way in 2014 from Baidu Inc. published by my senior 
friend Awni Hannun and et. al. who came from YCombinator and graduated from Standford University, San Franscio. He is currently 
working at Facebook AI Research (FAIR).

After the release of DeepSpeech or DeepSpeech 1, the next year DeepSpeech 2 was released (2015).
DeepSpeech takes an audio feature as an input and output the audio transcript.
Today's discussion is based on DeepSpeech 2, however there is Deepspeech 3 and other
state-of-the art for ASR.

The network consist of five layer, the input features are fed into three fully
connected layers, followed by a bidirectional LSTM layer, and lastly to the fully connected layer.
The hidden layer at the fully connected layers uses the ReLU activation. The LSTM 
uses tanh activation.

The output from this layer will be the matrix of probabilities over time.
At each time step of 20 mili seconds, the network yields and output of each characters from the
 alphabet, which is the likelihood of the character being said in the audio.
CTC loss function allow us maximize the likelihood of the probability of the 
character be correct.

Since the paper do not mention anything about the hyperparameters so implementing
 is tedious to get the result based on the paper. Hence, we refer to the open
 source implementation of the [DeepSpeech by Mozilla](https://discourse.mozilla.org/c/deep-speech).

Thanks to Mozilla for making it open source and providing it in GitHub.    