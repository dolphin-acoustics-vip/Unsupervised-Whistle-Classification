Classifying whistles solely using clustering algorithms

by: Ayam Babu, with guidance from Tristan Kleyn, Professor Vincent Janik, Dr. Olexandr Konovalov, and credits to Joel Beckles for the idea.
##

This experiment is built on top of work done in the first semester (refer to "main/Ayam Unsupervised Whistle Classification S1 2023-24.ipynb").

In the first semester of the project, I used both dimensionality reduction and clustering algorithms. Dimensionality reduction algorithms would compress the whistle, then the clustering algorithm would bundle them together. The problem with dimensionality reduction algorithms, however, is that they tend to warp certain structural characteristics of the whistles that could otherwise be important. It may also be possible that a dimensionality reduction algorithm will not be necessary at all, and therefore I got quite curious and decided to test whether a method that only uses clustering algorithms would give results just as good.

The results showed that the Gaussian Mixture clustering algorithm performed quite similarly with or without dimensionality reduction (0.83 without DR, 0.86 with DR). This means that further investigation would be required as to how a Gaussian Mixture algorithm works and if it has its own built in dimensionality reduction step. DBSCAN and Hierarchical DBSCAN by themselves performed dismally compared to their pairing with a dimensionality reduction algorithm (0.57 without DR, 0.86 with DR) showing that dimensionality reduction plays a bigger role for these algorithms.
