# Inference for multiple heterogeneous networks with a common invariant subspace
Link: https://arxiv.org/abs/1906.10026

## Summary
- This paper presents a statistical model called COSIE for population of graphs. The paper makes the following assumptions for the data:
  1. All graphs are on common vertex set. That is, there is a one-to-one correspondence of each vertex across all graphs.
  2. All graphs are symmetric that is A = A^T.
  3. All graphs are binary.

- In short, the model represents each graph i as VR^iV^T where V matrix is {n x d} and R^i is {d x d}. n is the number of vertices in each graph and d << n.
V matrix represents a common structure matrix and R^i is a graph specific matrix that transforms V. 

- Presents a method for estimating the parameters for COSIE called multiple adjacency spectral embedding (MASE)
MASE is a two step estimation process.

  1. Compute eigenvalue decomposition for each individual graph into d dimensions.
  2. Concatenate all eigenvectors.
  3. Compute singular value decomposition of the concatedate eigenvectors.
  4. Above provides estimate of V
  5. Estimate R^i = V^TA^iV where A^i is the adjacency matrix

- Figure 4 shows that graphs that COSIE model can identify graphs that should be similar to each other.

- Figure 8 shows that COSIE model outperforms joint embedding (JE) and multiple random dot product graphs (MRDPG), but performs about the same is joint random dot product graphs (JRDPG).

### Implications
- The model allows the following downstream tasks:
  1. Classification or clustering of population of graphs. This is done by applying some algorithm (i.e. kNN, k-means) on the R^i matrices.
  2. Classification or clustering of vertices. This is done by applying some algorithm (i.e. kNN, k-means) on the V matrix.
  3. Hypothesis testing. One can test whether R^i is statistically different from R^j.
