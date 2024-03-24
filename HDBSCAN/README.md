Classifying whistles solely using clustering algorithms

by: Ayam Babu, with guidance from Tristan Kleyn, Professor Vincent Janik, Dr. Olexandr Konovalov, and credits to Professor Janik for the idea.
##

This experiment is built on top of work done in the first semester (refer to "main/Ayam Unsupervised Whistle Classification S1 2023-24.ipynb").

In the first semester of the project, I used DBSCAN and Gaussian Mixture as clustering algorithms. These algorithms perform well, as it stands, but it would be really interesting to see how another clustering algorithm performs. Hierarchical DBSCAN was chosen because it has the idea of clusters and sub-clusters, which would be incredibly using for species discrimination problems (telling one species from another by whistle), but it is mostly just another clustering algorithm for a signature whistle problem because it isn't necessary that there are sub-clusters within clusters.

The Hierarchical DBSCAN algorithm performs very well, around the same as Gaussian Mixture (NMI 0.86). From my speculation, this could either be a coincidence or could possibly mean that certain signature whistles are related to each other in a deeper level than we know. It is certainly worth asking Professor Janik about this theory. The only problem with Hierarchical DBSCAN is the fact that this implementation doesn't produce a hierarchical tree that could be examined and analyzed, which could be useful in observing relations between signature whistle clusters (if there are any). Besides this problem, the algorithm classifies dolphin whistles superbly well.
