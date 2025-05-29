# TRANSFORMER ATTRACTORS FOR ROBUST AND EFFICIENT END-TO-END NEURAL DIARIZATION

## ABSTRACT

* End-to-End Neural Diarization (EEND) models can diarize overlapping speech directly from audio without explicit segmentation or cluster.

* How EEND models work?
    - EEND models handles overlapping speech by treating it as a multi-label classification problem.
    - Audio is converted to acoustic features such as log-Mel Spectrograms.
    - An encoder neural network (usually a Bi-LSTM or Transformer) encodes the sequence.
    - An Attractor module learns a set of speaker attractors. Basically during training, the attractors learn to represent each speaker's unique characteristics.
    - These attractors are used to decode the frame-level speaker activity.
    - EEND model outputs a binary matric indicating whether each speaker is active at each time frame or not.
    - (An attractor is a vector representation that pulls together all the speech frames belonging to a particular speaker).

* Advantages of EEND models:
    - They handle overlapping speech well.
    - Jointly learns the speech segmentation, speaker embeddings and does clustering.
    - Doesn't require post processing as in traditional models.

* Disadvantages of EEND-EDA (Encoder Decoder Attractors):
    - The decoder here is usually an LSTM network which generate attractors (speaker-wise vectors that help identify who spoke when) one at a time. (after generating each attractor the decoder decides whether to generate another one or to stop)
    - They are inefficient due to multiple forward passes
    - Instability in predicting number of speakers
    - Generalization issues

* This paper solves this issue by using Transformer based attractor decoder which is more efficient for faster inference that suits real-time and low-resource scenarios. It also handles varying number of speakers.

* EEND-EDA models can't infer the number of speakers directly from a single pass. They assume a number of speakers and for each assumption, the model is ran once and the the result with lowest diarization loss is picked.

* How this is solved by transformer attractor is discussed below in consequent sections but in breif, transformer attractor decoder can produce variable number of attractors (speakers) in single forward pass.

* In addition the Transformer Attractor block which contains a Combiner block learn to generate conversational dependent embeddings (it learns from the encoded global embeddings itlself though).


## INTRODUCTION

* Traditional models use different models for Speech activity detection, speaker embeddings, clustering. Use of different models not only compounds the error but also increases the complexity with respect to deployment and maintenance.

* Whereas EEND system is one single neural network model which jointly handles all the tasks internally.

* Although, EEND models are designed to predict a relatively small number of speakers due to combinatorics of permutation invariant training.

* Then introduced EEND-EDA model, which uses
    - an LSTM based encoder-decoder architecture
    - which transforms sequence of frames into variable length sequence of speaker attractos
    - which are used to predict the speaker's speech activity

* Many approaches were proposed and tried out around injecting more context into the decoder. For example:
    - Bahdanau-style attention mechanism to prepare inputs for LSTM decoder
    - constructing inputs to LSTM decoder using a learned conversational summary vector


* This paper proposes to replace the Encoder-Decoder Attractors with Transformer based Attractors by introducing a Transformer Attractors (TA) block.

* TA block comprises of Combiner block and Transformer decoder block.

* The functionality of the Combiner block is to generate speaker embeddings that are personalized for each conversation by incorporating the learned conversation info into global embeddings.

* These conversationally dependent embeddings from Combiner block are then passed into Transformer decoder.

* This approach of EEND-TA is without any additional "bells and whistles", such as iterative refinement, intermediate attractors loss or self conditioning each of which could potentially boost the performance further.

## BACKGROUND
### EEND-EDA

* 