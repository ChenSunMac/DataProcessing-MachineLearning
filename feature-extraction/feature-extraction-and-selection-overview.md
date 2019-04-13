# Feature Extraction & Selection Overview

Feature extraction combines original features into a new set of features by transformation or projection.

Transformation can produce new features have interpretable meaning to the data, Projection is to find the most significant set of new features, which is similar to use a lower dimensional subspace than the original set of features.


Given a dataset $X: N \times D$ matrix

We can extract or transform new feqtures $F$ to describe the variation, distances, proximity etc where $|F| < D$

**Linear Methods:**
- Unsupervised (no class label information, e.g. PCA, ICA)
- Supervised (with class label information, LDA)


**Nonlinear Methods:**
- Global (preserves glopbal properties, e.g. MDS, Isomap, Kernel PCA)
- Local (preserves properties within local neighborhood, e.g. LLE)

