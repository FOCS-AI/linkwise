# linkwise

### Topology-Driven Edge Predictions with Graph Machine Learning for Optical Network Growth: 
Graph representation learning on real-world optical core networks outperforms edge prediction heuristics by 10 times, achieving up to 93.4% accuracy on BT(UK), COST(EU), and CORONET(USA) by learning from 10% training data.

### Code

**Packages:**
- numpy
- pandas
- folium
- networkx
- node2vec
- scikit-learn
- matplotlib
- seaborn
- torch

**Heuristics**
- Implements various link prediction methods on the COST266 and Coronet CONUS 60 graphs.
- Imports and utility functions like distance calculation and graph creation
- Initialization of the COST266 and Coronet CONUS 60 graphs with node attributes
- Link prediction methods:
- -  Jaccard Coefficient
- - Adamic Adar Index
- - Preferential Attachment
- - Resource Allocation Index
- - Common Neighbors
- - Triadic Closure
- -  Random
- - Katz Index
- - Rooted PageRank
- Functions to run predictions and evaluate accuracy
- Sample runs on the graphs with different random seeds
- Run the cells to initialize the graphs and functions
- seeds_to_test - Random seeds
- percentages_to_test - Percentage of edges to remove
- Output shows the accuracy of different prediction methods when a percentage of edges are removed from the graphs.


### Dataset
- COST has been taken from SNDLib http://sndlib.zib.de/home.action
- CORONET has been taken from https://github.com/XuYZh/Network-Pruning-and-Growth---Probabilistic-Optimization
- Raw dataset files have been added for users in case they need them.
- We process these topologies as graphs and manually hardcoded them into our code to be available in the Networkx format suitable for our analysis
- We also have processed and saved Networkx into multiple formats for the user.

### Please Note: 
- _Data about BT's infrastructure is not available due to privacy concerns. Users can utilise the COST or CORONET topologies provided in the code for analysis._
- Random seeds can generate different results at each run; irrespective of the minor changes, the performance gains for our model compared to heuristics remain 10x.
