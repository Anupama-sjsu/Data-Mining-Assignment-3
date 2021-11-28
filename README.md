# Data-Mining-Assignment-3
## Approximate Nearest Neighbor Search

Approximate Nearest Neighbor techniques speed up the search by preprocessing the data into an efficient index and are often tackled using these phases:

- **Vector Transformation** — applied on vectors before they are indexed, amongst them, there is dimensionality reduction and vector rotation.

- **Vector Encoding** — applied on vectors in order to construct the actual index for search, amongst these, there are data structure-based techniques like Trees, LSH, and Quantization a technique to encode the vector to a much more compact form.

- **None Exhaustive Search Component** — applied on vectors in order to avoid exhaustive search, amongst these techniques there are Inverted Files and Neighborhood Graphs.

The following methods are implemented as a part of Approximate Nearest Neighbor Search:

**- Vector Encoding Using LSH** : They construct a hash table as their data structure by mapping points that are nearby into the same bucket. In LSH, in order to construct the index, we apply multiple hash functions to map data points into buckets so that data points near each other are located in the same buckets with high probability, while data points far from each other are likely to fall into different buckets.

**- Vector Encoding Using Quantization - Product Quantization:** Quantization is a technique to reduce dataset size (from linear) by defining a function (quantizer) that encodes our data into a compact approximated representation. we can reduce the size of the dataset by replacing every vector with a leaner approximated representation of the vectors (using quantizer) in the encoding phase.One way to achieve a leaner approximated representation is to give similar vectors to the same representation. This can be done by clustering similar vectors and represent each of those in the same manner (the centroid representation), the most popular way to do so is using k-means. 

**- Vector Encoding Using Trees:** Tree-based algorithms are one of the most common strategies when it comes to ANN. This constructs forests- a collection of trees, as their data structure by splitting the dataset into subsets. One of the most prominent solutions out there is Annoy, which uses trees to enable Spotify’ music recommendations. In Annoy, in order to construct the index we create a forest and tree is constructed in the following way, we pick two points at random and split the space into two by their hyperplane, we keep splitting into the subspaces recursively until the points associated with a node is small enough. 
- _number_of_trees_ — the number of binary trees we build, a larger value will give more accurate results, but larger indexes.
- _search_k_ — the number of binary trees we search for each point, a larger value will give more accurate results, but will take a longer time to return.

**- Exhaustive Search:** 
**- Hierarchical Navigable Small World**


**Picking The Right Approximate Nearest Neighbours Algorithm**

Evaluating which algorithms should be used and when is deeply depends on the use case and can be affected by these metrics:
- Speed- Index creation and Index construction.
- Hardware and Resources- Disk size, RAM size, and whether we have GPU.
- Accuracy Requirements.
- Access Patterns — Number of queries, batch or not, and whether we should update the index.




_LSH Pros_
Data characteristics such as data distribution are not needed to generate these random hash functions.
The accuracy of the approximate search can be tuned without rebuilding the data structure.
Good theoretical guarantees of sub-linear query time.
_LSH Cons_
In practice, the algorithm MIGHT runs slower than a linear scan.
No support for GPU processing.
Require a lot of RAM.

_Hierarchical Navigable Small World Graphs Pros_
We can tune the parameters to change the accuracy/speed tradeoff.
Support batch queries.
The NSW algorithm has polylogarithmic time complexity and can outperform rival algorithms on many real-world datasets.
_Hierarchical Navigable Small World Graphs Cons_
The exact nearest neighbor might be across the boundary to one of the neighboring cells.
Cant incrementally add points to it.
Require quite a lot of RAM.


