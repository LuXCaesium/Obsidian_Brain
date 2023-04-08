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

Gates are a way to optionally let information through. They are composed of a sigmoid neural network layer and a pointwise multiplication function. The sigmoid layer, outputting numbers between 0 and 1 describes how much of each component should be let through.

A LSTM has three of these gates, to protect and control the cell state.

## Step-by-Step LSTM Walk Through

* The first step in our LSTM is to decide what information to throw away. This decision is made by a singmoid layer called the *forget gate layer*. It looks at $h_{t-1}$ and $x_t$, and outputs a number between 0 and 1 for each number in the cell state $C_{t-1}$. 

![[LSTM3-focus-f.png|1000]]

* The next step is to decide what information we're going to store in the cell state. This has two parts:
	* First, a sigmoid layer called *input gate layer* which decides which values we'll update.
	* A tanh layer creates a vector of new candidate values, $\tilde{C_t}$, that could be added to the state.

![[LSTM3-focus-i.png|1000]]

We now need to update the old cell state $C_{t-1}$ into the new cell state $C_t$.

We multiply the old state by $f_t$ forgetting what we decided earlier. Then we add $i_{t} \times \tilde{C_t}$. This is the new candidate values, scaled by how much we decided to update each state value.

![[LSTM3-focus-C.png|1000]]

Finally, we need to decide what we are going to output. This output will be based on our cell state, but will be filtered. First we run a sigmoid layer which decides what parts of the cell state we're going to output. Then, we put the cell state through **tanh** (pushing values between -1 and 1) and multiply it by the output of the sigmoid gate. 

![[LSTM3-focus-o.png]]

## Variants of Long Short Term Memory

