# Density Based Approach

Group points based on their density, Handles outliers, Can detect clusters with arbitrary shapes and densities

**DBScan:** Density Based Spatial Clustering of Applications with Noise

Dense Region = neighborhood of distance contains at least m points

Classify the points according to their density:

**Core points :** points in the interior of dense region.
**Border points :** points on the edge of dense region.
**Noise points :** points that are not border nor core.


- Resistant to Noise
- Can handle clusters of different shapes and sizes



### When DBSCAN Does NOT Work Well
- Varying densities
- High-dimensional data



- DBSCAN can find clusters of different shapes and sizes.
- DBSCAN doesn’t handle clusters of varying densities very well.
- Can be expensive for large data due to neighborhood calculations (distances)

