---

created: <% tp.file.creation_date() %>

---
tags:: #TimeSeries #MachineLearning #DataScience 

# The Wavelet Transform

A major disadvantage of the Fourier Transform is it captures *global* frequency information, meaning that frequencies that persist over an entire signal. The Wavelet Transform aims to solve this by decomposing a function into a set of wavelets.

## What is a Wavelet
A Wavelet is a wave-like oscillation that is localised in time. Wavelets have two basic properties: scale and location. *Scale* (or dilation) refers to how stretched or squished a wavelet is. This property is related to frequency as defined for waves. *Location* defines where the wavelet is positioned in time (or space).

