Unsupervised Whistle Classification

by: Ayam Babu, with guidance from Tristan Kleyn, Prof. Janik, and Dr. Konovalov
##

This project is part of the Dolphin Acoustics VIP, looking to explore models that could be used to cluster dolphin whistles without knowing how different whistles look like. The project is focusing on classifying signature whistles, which can be used to identify individual dolphins. In the first semester, I worked on designing and experimenting with unsupervised methods to form a baseline classifier. In the second semester, I experimented with changing different parts of the first semester models to observe how they impact the results. I have explained my work from the last two semesters in more detail below:

#### First semester: ####

Together with Tristan, we came up with a list of algorithms that we felt would be relevant to dolphin whistle classification. These algorithms fell into two main categories: dimensionality reduction and clustering. What do these terms mean?

Dimensionality reduction: Take whistle time series data (in the form of the frequency and time data of wav files), and compress them by directly or indirectly filtering out the parts of the file that would affect the classifications the least (in other words, features that don't help differentiate which cluster a whistle should belong to). This has the added double benefit of giving the clustering algorithm a lower workload, as compressed whistles take significantly less time to classify than the whistles in their whole form. There were plenty of dimensionality reduction methods to experiment with: Principal Components Analysis (PCA), t-distributed Stochastic Neighbor Embedding (t-SNE), Uniform Manifold Approximation and Projection (UMAP), Isometric Mapping (ISOMAP).

Clustering: Take whistles (compressed or not) that seem similar to each other and bundle them together. There are plenty of clustering methods to use, but most of them require a set number of clusters for the algorithm to classify the whistles into. This is meant to be an unknown for most situations, so we had to use one of these algorithms: Gaussian Mixture (GM), Density-Based Spatial Clustering of Applications with Noise (DBSCAN).

The general process was to take a dimensionality reduction algorithm to compress the whistle, then take a clustering algorithm to bundle the compressed whistles together. The algorithms were evaluated using the Normalized Mutual Information score (or NMI) from 0-1 (the higher the better); ARTWarp's NMI by reference was 0.88. The best algorithm pairs that I experimented with hit roughly 0.86, but with a speed of <15 seconds, often less than 10, compared to ARTWarp's 10 days for 1800 whistles.


#### Second semester: ####

Though the results looked promising from the first semester, there were some flaws in the algorithms and certain algorithms that I overlooked. 
