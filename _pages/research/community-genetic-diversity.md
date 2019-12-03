---
layout: single
classes: wide
permalink: /research/community-genetic-diversity/
title: "Community Genetic Diversity"
---

Communities assemble in a geographic and environmental context. But to what
degree do shared geographic and environmetal contexts dicatate the community
structures we observe today? As part of my research program I seek to
understand how community genetic diversity is structured across spatial
scales and environmental gradients.

## Characterizing environmental conditions
My initial investigations are driven by a collaboration focusing on Coral
Triangle decapod communities. We first characterized local environmental
conditions by collapsing marine environmental variables into PC space, which
is illustrated in the following figure.

![Characterizing environmental PC space](/assets/images/Env_PC_Space.png)

The inset shows the total environmental space of the region collapsed into the
first two PCs, and also indicates the environmental space occupied by the ten
sampling locations of the observed decapod communities. The larger panel shows
the environmental PC space projected across the whole landscape, clipped to
the locations where corals are known to exists. Here we see that the
environmental space of the Coral Triangle is quite broad and that the space
occupied by the sampled communities covers a significant fraction of this
environmental space.

## Using machine learning to predict community structure across the landscape
Now, given that we know the distribution of genetic variation within the
observed decapod communities, we use this information, along with environmental
correlates, to predict the distribution of genetic variation of decapod
communities at unobserved locations across the landscape? To this end we
developed a machine learning inference procedure which we trained on the
observed data and generated the following map of projected community genetic
structure across the Coral Triangle.

![Predicting community genetic diversity structure across the landscape](/assets/images/PredictedGeneticStructure.png)

This map is a first step to identifying regions which may be either genetically
buffered or vulnerable to incipient climate change. Further work can be guided
by these results to improve the inference by targeting unsampled environmental
space.
