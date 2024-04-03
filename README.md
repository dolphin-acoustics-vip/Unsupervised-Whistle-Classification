Unsupervised Whistle Classification

by: Ayam Babu, with guidance from Tristan Kleyn, Prof. Vincent Janik, and Dr. Olexandr Konovalov
##

This project is part of the Dolphin Acoustics VIP, looking to explore models that could be used to cluster dolphin whistles without prior knowledge about the whistles. The project is focusing on classifying signature whistles, which can be used to identify individual dolphins. In the first semester, I worked on designing and experimenting with different methods to form a baseline classifier. In the second semester, I experimented with changing parts of the first semester models to observe how they impact the results. I have explained my work from the last two semesters in more detail below:

</br>

#### First semester (September - December 2023): ####
Filename: "main/Ayam Unsupervised Whistle Classification S1 2023-24.ipynb"

Together with Tristan, we came up with a list of algorithms that we felt would be relevant to dolphin whistle classification. These algorithms fell into two main categories: dimensionality reduction and clustering. What do these terms mean?

Dimensionality reduction: Take whistle time series data (in the form of the frequency and time data of wav files), and compress them into a smaller form (think fingerprinting). This has the added benefit of giving the clustering algorithm a lower workload, as compressed whistles take significantly less time to classify than the whistles in their whole form. I experimented with these dimensionality reduction methods: Principal Components Analysis (PCA), t-distributed Stochastic Neighbor Embedding (t-SNE), Uniform Manifold Approximation and Projection (UMAP), and Isometric Mapping (ISOMAP).

Clustering: Take whistles (compressed or not) that seem similar to each other and bundle them together. There are plenty of clustering methods to use, but most of them require one to also a set number of clusters for the algorithm to classify the whistles into. This is meant to be an unknown for most of our situations, but we ultimately experimented with a few clustering algorithms: Gaussian Mixture (GM), Density-Based Spatial Clustering of Applications with Noise (DBSCAN).

The general process was to take each whistle, stretch them to a certain size, apply dimensionality reduction to compress the whistles, then take a clustering algorithm to bundle the compressed whistles together. The algorithms were evaluated using the Normalized Mutual Information score (or NMI) from 0-1 (the higher the better); ARTWarp's NMI by reference was 0.88. The best algorithms that I experimented with hit roughly NMI 0.86, but with a speed of <15 seconds, often less than 10, compared to ARTWarp's 10 days for 1800 whistles.

</br>

#### Second semester (January - May 2024): ####
Directories: "main/Clustering Only", "main/HDBSCAN", "main/Wrapping Whistle Preprocessing"

Though the results looked promising from the first semester, there were some flaws in the algorithms and certain methods that I overlooked. The methods from the first semester, specifically the dimensionality reduction algorithm in the pair and fixing the size of the whistle, would change the structure of the whistle. According to Professor Janik, the structure of the whistle could hold some important information, so it may not be the best idea to stretch the whistle. He recommended me to instead repeat the whistles, until they hit the length of the longest whistle in the dataset. More details are in the README in the "Wrapping Whistle Preprocessing" folder.

Another concern, with respect to the structure of the whistle, was that the dimensionality reduction algorithm would affect a whistle's structural characteristics that may otherwise be important, such as up- and down- sweeps (large changes in frequency in a short amount of time in the whistle). Joel Beckles, a teammate, also suggested experimenting with skipping the dimensionality reduction algorithm and passing stretched whistles to the clustering algorithms directly. More details are in the README in the "Clustering Only" folder.

Finally, Professor Janik had a suggestion for a clustering method that I hadn't initially considered: Hierarchical DBSCAN. This clustering algorithm was paired with all of the dimensionality reduction algorithms, and the results were compared with the algorithms tested in the first semester. More details are in the README in the "HDBSCAN" folder.


