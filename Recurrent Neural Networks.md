---

created: <% tp.file.creation_date() %>

---
tags:: #MachineLearning #DataScience 

# Recurrent Neural Networks

Unlike traditional neural networks, Recurrent Neural Networks have loops within allowing information to persist.

![[RNN-rolled.png|200]]
In the above diagram, a chunk of a neural network, $A$ , looks at some input $x_t$ and outputs a value $h_t$. A loop allows information to be passed from one step of the network to the next. In many ways there are similar to normal neural networks, but think of them as multiple copies of the same network each passing a message to a successor. Consider unrolling the loop:

![[RNN-unrolled.png]]

## The Problem of Long-Term Dependencies

One of the appeals of RNNs is the idea that they might be able to connect previous information with the present. where the gap between relevant information and the place its needed is small, then RNN's can learn to use past information. As the gap grows however, RNN's become unable to learn to connect information. In theory this should not be a problem, but in practice it seems to be. Here is a paper discussing the issue [[SeppHochreiter1991ThesisAdvisorSchmidhuber.pdf]].

To solve these issues we use [[LSTM]] networks.

