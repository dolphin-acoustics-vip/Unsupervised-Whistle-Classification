Classifying whistles solely using clustering algorithms

by: Ayam Babu, with guidance from Tristan Kleyn, Professor Vincent Janik, Dr. Olexandr Konovalov, and credits to Joel Beckles for the idea.
##

This experiment is built on top of work done in the first semester (refer to "main/Ayam Unsupervised Whistle Classification S1 2023-24.ipynb").

In the first semester of the project, I used both dimensionality reduction and clustering algorithms. Dimensionality reduction algorithms would compress the whistle, then the clustering algorithm would bundle them together. The problem with dimensionality reduction algorithms, however, is that they tend to warp certain structural characteristics of the whistles that could otherwise be important. It may also be possible that a dimensionality reduction algorithm will not be necessary at all, and therefore I got quite curious and decided to test whether a method that only uses clustering algorithms would give results just as good.

