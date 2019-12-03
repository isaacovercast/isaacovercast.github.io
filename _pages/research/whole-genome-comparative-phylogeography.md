---
layout: single
classes: wide
permalink: /research/whole-genome-comparative-phylogeography/
title: "Whole-Genome Comparative Phylogeography"
---

Phylogeography is the study of population genetic variation in a geographic
context. Sequence data contains a record of the history of a species and we
can use statistical tools to make inference about this history. For example,
we may be interested in past population size changes or whether and to what
extent populations are structured across the landscape.

Comparative phylogeography extends this idea to investigate whether multiple
co-distributed species have undergone similar population dynamics (e.g.
bottenecks, expansions, populations splits) given the fact that they were
historically subject to the same environmental conditions.

Comparative phylogeographic methods were first developed for single locus
datasets, typically several hundred basepairs of a single mitochondrial marker.
Given that single locus data can give a biased picture of population history,
methods have advanced through time to support multi-locus data, and even
SNP data representing thousands of independent loci across the genome,
typical of RADSeq experiments. Recently, collaborators and I have developed
a comparative phylogeographic method for whole-genome data. We call this method
[Phylogeograpic Temporal Analysis (PTA)](https://drive.google.com/drive/folders/1FBCY63dHIbldReDzD71Kc7947o_74NAi).

A few figures to demonstrate the core concepts:

### Can we distinguish shared population expansion times?

![2000 PTA mSFS plotted into PC space](/assets/images/PTA-mSFS-PCA.png)

This figure depicts 2000 independent mSFS (multi-site frequency spectra)
generated from simulations using identical parameters while only allowing
the time of co-expansion to vary. Each point is a simulation, and the color
of the point indicates the time of co-expansion. The position of each point
indicates how 'similar' the resulting mSFS is to all the other simulations,
after projecting the results into PC space.


![ML classifier confusion matrix of ~1000 simulations](/assets/images/PTA-ConfusionMatrix.png)



![ML regressor parameter estimation for various model parameters](/assets/images/PTA-CrossValidation.png)

This method is still under active development, so these are proof-of-concept
results to give an idea how it works.

PTA is the only comparative phylogeographic method that can make use of the
information in whole-genome sequences, while fully accounting for linkage. We
also designed it to have a simple, modern interface, a massively parallel
backend, and an automated machine learning inference procedure. PTA is the most
advanced comparative phylogeographic method developed to date, and we're just
getting started!
