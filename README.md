Unsupervised Whistle Classification

by: Ayam Babu, with guidance from Tristan Kleyn, Prof. Vincent Janik, and Dr. Olexandr Konovalov
##

This project is part of the Dolphin Acoustics VIP, looking to explore models that could be used to cluster dolphin whistles without knowing how different whistles look like. The project is focusing on classifying signature whistles, which can be used to identify individual dolphins. In the first semester, I worked on designing and experimenting with unsupervised methods to form a baseline classifier. In the second semester, I experimented with changing different parts of the first semester models to observe how they impact the results. I have explained my work from the last two semesters in more detail below:



#### First semester (September - December 2023): ####

Together with Tristan, we came up with a list of algorithms that we felt would be relevant to dolphin whistle classification. These algorithms fell into two main categories: dimensionality reduction and clustering. What do these terms mean?

Dimensionality reduction: Take whistle time series data (in the form of the frequency and time data of wav files), and compress them by directly or indirectly filtering out the parts of the file that would affect the classifications the least (in other words, features that don't help differentiate which cluster a whistle should belong to). This has the added double benefit of giving the clustering algorithm a lower workload, as compressed whistles take significantly less time to classify than the whistles in their whole form. There were plenty of dimensionality reduction methods to experiment with: Principal Components Analysis (PCA), t-distributed Stochastic Neighbor Embedding (t-SNE), Uniform Manifold Approximation and Projection (UMAP), Isometric Mapping (ISOMAP).

Clustering: Take whistles (compressed or not) that seem similar to each other and bundle them together. There are plenty of clustering methods to use, but most of them require a set number of clusters for the algorithm to classify the whistles into. This is meant to be an unknown for most situations, so we had to use one of these algorithms: Gaussian Mixture (GM), Density-Based Spatial Clustering of Applications with Noise (DBSCAN).

The general process was to take a whistle, stretch it to a certain size, apply dimensionality reduction to compress the whistle, then take a clustering algorithm to bundle the compressed whistles together. The algorithms were evaluated using the Normalized Mutual Information score (or NMI) from 0-1 (the higher the better); ARTWarp's NMI by reference was 0.88. The best algorithm pairs that I experimented with hit roughly 0.86, but with a speed of <15 seconds, often less than 10, compared to ARTWarp's 10 days for 1800 whistles.



#### Second semester (January - May 2024): ####

Though the results looked promising from the first semester, there were some flaws in the algorithms and certain methods that I overlooked. The methods from the first semester, specifically the dimensionality reduction algorithm in the pair and fixing the size of the whistle, would change the structure of the whistle. According to Professor Janik, the structure of the whistle could hold some important information, so it may not be the best idea to stretch the whistle. He recommended me to instead repeat the whistles, until they hit the length of the longest whistle in the dataset. More details are in the README in the "Wrapping Whistle Preprocessing" folder.

Another concern, with respect to the structure of the whistle, was that the dimensionality reduction algorithm would affect a whistle's structural characteristics that may otherwise be important, such as up- and down- sweeps (large changes in frequency in a short amount of time in the whistle). Joel Beckles, a teammate, also suggested experimenting with skipping the dimensionality reduction algorithm and passing stretched whistles to the clustering algorithms directly. More details are in the README in the "Clustering Only" folder.

Finally, Professor Janik had a suggestion for a clustering method that I hadn't initially considered: Hierarchical DBSCAN. This clustering algorithm was paired with all of the dimensionality reduction algorithms, and the results were compared with the algorithm pairs tested in the first semester. More details are in the README in the "HDBSCAN" folder.


