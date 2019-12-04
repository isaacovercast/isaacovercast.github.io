---
layout: single
classes: wide
permalink: /research/eco-evolutionary-simulations/
title: "Eco-evolutionary Simulations"
---

Biodiversity is structured hierarchically across spatial, temporal, and
taxonomic scales. It is therefore important to integrate across multiple
axes of biodiversity data when constructing models and performing inference.
My core research interest is to investigate the feedbacks among axes of
biodiversity data that accumulate across these different scales. I primarily
develop individual-based, mechanistic models, and apply statistical analysis
with a focus on emerging machine learning methods.

Take this example of real data from a community of spiders from La Reunion. Here
on the left is a typical species abundance distribution (SAD) and on the right
is the species genetic diversity distribution (SGD) which is constructed in an
identical fashion, gathering COI data at the community-scale, calculating
nucleotide diversity (pi) and ordering pi from greatest to least:
![Empirical SAD and SGD](/assets/images/gimmeSAD-Abundance-Genetic-data.png)

The core insight here is that the SAD and SGD record the history of the
community on different timescales! My modeling approach seeks to simultaneously
exploit the information from both of these axes of data.

## gimmeSAD: A joint neutral model of community abundance and genetic diversity
As a first approximation, collaborators and I developed a joint model of
abundance and genetic diversity in ecological communities. This model is called
[gimmeSAD](https://github.com/isaacovercast/gimmeSAD) and it is published in
[Journal of Biogeography](https://onlinelibrary.wiley.com/doi/abs/10.1111/jbi.13541)
![Forward-time Community Assembly Model](/assets/images/gimmeSAD-Assembly-Model.png)
![Simulated 2D-SGD and SAD](/assets/images/gimmeSAD-Simulations.png)

![gimmeSAD Empirical Results](/assets/images/gimmeSAD-Empirical.png)

## MESS: Massive Eco-evolutionary Synthesis Simulations

![MESS Non-neutral Dynamics](/assets/images/MESS-Non-Neutral-Dynamics.png)
![MESS Empirical Results](/assets/images/MESS-Results.png)
