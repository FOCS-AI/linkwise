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

### Linkwise: Node2Vec and Logistic Regression
- We implement a link prediction pipeline using graph embeddings and logistic regression on network topologies - COST266 and CORONET CONUS-60.

### Methodology
The pipeline follows these key steps:
- Construct the graph and compute geographical distance features between nodes.
- Generate Node2Vec embeddings for the nodes.
- Extract positive (connected) and negative (unconnected) edges from the graph.
- Split the edges into training and test sets.
- Train a logistic regression classifier with distance and embedding dot product features. 
- Evaluate classifier performance using AUC-ROC, precision, recall etc.
- Visualize results using plots.

**Key Functions:**
- `setup_cost266_graph()`: Creates the COST266 graph.
- `setup_coronet_conus60_graph()`: Creates the CORONET CONUS-60 graph. 
- `generate_node2vec_embeddings()`: Generates node embeddings.
- `train_classifier()`: Trains the classifier.
- `evaluate_classifier()`: Evaluates classifier performance.
- `visualise_metrics()`: Visualizes results.
- `run_pipeline()`: Runs the pipeline end-to-end.
- `main()` function runs the pipeline for different test set sizes.


### Heuristics
- Link prediction methods:
- - Jaccard Coefficient
- - Adamic Adar Index
- - Preferential Attachment
- - Resource Allocation Index
- - Common Neighbors
- - Triadic Closure
- - Random
- - Katz Index
- - Rooted PageRank
- Functions to run predictions and evaluate accuracy
- Sample runs on the graphs with different random seeds
- `seeds_to_test` - Random seeds
- `percentages_to_test` - Percentage of edges to remove
- Output: accuracy of different prediction methods when a percentage of edges are removed from the graphs.


### Dataset
- COST266: A European network topology with 37 nodes and 57 links. Nodes represent cities and edges represent fiber links between cities.
- CORONET CONUS-60: A US backbone network topology with 60 nodes and 150 links.

Notes:  
- COST has been taken from SNDLib http://sndlib.zib.de/home.action
- CORONET has been taken from https://github.com/XuYZh/Network-Pruning-and-Growth---Probabilistic-Optimization
- Raw dataset files have been added for users in case they need them.
- We process these topologies as graphs and manually hardcoded them into our code to be available in the Networkx format suitable for our analysis
- We also have processed and saved Networkx into multiple formats for the user.

### Please Note: 
- _Data about BT's infrastructure is not available due to privacy concerns. Users can utilise the COST or CORONET topologies provided in the code for analysis._
- Random seeds can generate different results at each run; irrespective of the minor changes, the performance gains for our model compared to heuristics remain 10x.
