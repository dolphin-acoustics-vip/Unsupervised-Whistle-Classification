Standardizing whistles with repeats

by: Ayam Babu, with guidance from Tristan Kleyn, Professor Vincent Janik, Dr. Olexandr Konovalov, and credits to Professor Janik for the idea.
##

This experiment is built on top of work done in the first semester (refer to "main/Ayam Unsupervised Whistle Classification S1 2023-24.ipynb").

In the first semester of the project, I fixed the number of samples of the whistle to 400 samples and would stretch the whistles time-wise to fit that range. This standardization technique performs well, but it did have some flaws. One flaw is that the length of the whistle can be an important detail to track, so instead Professor Janik suggested an alternative whistle standardization technique, using repeating whistles. The technique works by taking every whistle and repeating it (wholly or partially) until it is the same length as the longest whistle. This is considered to be a standard technique in other whistle classifiers, and so I was recommended to try it out.

With the classification algorithms I am using, the repeating whistles techniques doesn't pair that well. The best algorithms performed with an NMI score of 0.76, which is much lower than the standardization techniques that I was using earlier (NMI 0.86). My theory is that dimensionality reduction algorithms can't extrapolate length.


Further investigation will be required to discover why.
