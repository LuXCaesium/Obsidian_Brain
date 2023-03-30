---

created: <% tp.file.creation_date() %>

---
tags:: #MachineLearning #DataScience 

# Recurrent Neural Networks

Unlike traditional neural networks, Recurrent Neural Networks have loops within allowing information to persist.

![[RNN-rolled.png|200]]
In the above diagram, a chunk of a neural network, $A$ , looks at some input $x_t$ and outputs a value $h_t$. A loop allows information to be passed from one step of the network to the next. In many ways there are similar to normal neural networks, but think of them as multiple copies of the same network each passing a message to a successor. Consider unrolling the loop:

![[RNN-unrolled.png]]

