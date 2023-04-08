---

created: <% tp.file.creation_date() %>

---
tags:: #MachineLearning #DataScience 

# Long Short-Term Memory Network

A special type of [[ Recurrent Neural Networks]] capable of learning long-term dependencies, and are specifically designed to avoid the long-term dependency problem.

All RNN have the form of a chain of repeating modules. In standard RNN's, this repeating module will have a very simple structure, such as a single tanh layer.

![[LSTM3-SimpleRNN.png]]

LSTM's also have this chain like structure, but the repeating module has a different structure. Instead of having a single neural network layer, there are four, interacting in a very special way.

![[LSTM3-chain.png]]

In the diagram above, each line carries and entire vector, from the output of one node to the inputs of another. The pink circles are pointwise operation, whilst yellow boxes are learned neural network layers. Lines merging denote concatenation, whilst divergence denotes copying.

## The Core Idea Behind LSTMs

They key to the LSTMs are the cell state, this horizontal line running through the top of the diagram. It runs along the whole length of the chain, with only some minor changes along the way allowing for information to flow unchanged. The LSTM has the ability to add or remove information to the cell state, carefully regulated by structures called gates. 