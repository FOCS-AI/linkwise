# linkwise

### Topology-Driven Edge Predictions with Graph Machine Learning for Optical Network Growth: 
Graph representation learning on real-world optical core networks outperforms edge prediction heuristics by 10 times, achieving up to 93.4% accuracy on BT(UK), COST(EU), and CORONET(USA) by learning from 10% training data.

### Dataset
- COST266: A European network topology with 37 nodes and 57 links. Nodes represent cities, and edges represent fiber links between cities.
- CORONET CONUS-60: A US backbone network topology with 60 nodes and 75 links.
- BT: UK's core backbone optical network with 106 nodes and 180 edges

![image](https://github.com/FOCS-AI/linkwise/assets/8778046/01e0a30f-f2af-4cc3-9d07-b3af4b628536)


### Linkwise: Node2Vec and Logistic Regression
We implement a link prediction pipeline using graph embeddings and logistic regression on network topologies - BT, COST and CORONET.

### Model Evaluation using Test Accuracy 
![image](https://github.com/FOCS-AI/linkwise/assets/8778046/6d4302ec-c098-499a-9072-4af3efd42d44)


### Comparison with Heuristics
| Topology | Baseline (t = 0.5) | Accuracy (t = 0.5)              | Baseline (t = 0.1) | Accuracy (t = 0.1)             |
|----------|--------------------|---------------------------------|--------------------|--------------------------------|
| COST     | 0.0714 (Pagerank)  | **0.94 ± 0.01**                 | 0.0784 (Adamic Adar) | **0.88 ± 0.04**              |
| BT       | 0.1222 (Adamic Adar) | **0.93 ± 0.01**               | 0.0432 (Jaccard)  | **0.93 ± 0.01**               |
| CORONET  | 0.0256 (Jaccard)   | **0.88 ± 0.05**                 | 0.0423 (Random)   | **0.89 ± 0.00**               |



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

### Python Packages (Python 3.10.12)
- numpy
- pandas
- folium
- networkx
- node2vec
- scikit-learn
- matplotlib
- seaborn
- torch

### Data Sources and Formats:
- COST has been taken from SNDLib http://sndlib.zib.de/home.action
- CORONET has been taken from https://github.com/XuYZh/Network-Pruning-and-Growth---Probabilistic-Optimization
- Raw dataset files have been added for users in case they need them.
- We process these topologies as graphs and manually hardcoded them into our code to be available in the Networkx format suitable for our analysis
- We also have processed and saved Networkx into multiple formats for the user.

### Please Note: 
- _Data about BT's infrastructure is not available due to privacy concerns. Users can utilise the COST or CORONET topologies provided in the code for analysis._
- _Random seeds can generate different results at each run; irrespective of the minor changes, the performance gains for our model compared to heuristics remain 10x.

### References
- S. Orlowski, R. Wessäly, M. Pióro, A. Tomaszewski, "Sndlib 1.0—Survivable Network Design Library," Networks, vol. 55, no. 3, pp. 276--286, 2010.
- Y.-Z. Xu, D. Saad, "Network Pruning and Growth: Probabilistic Optimization," Physical Review Research, vol. 5, no. 3, 033087, 2023.
- A. Grover, J. Leskovec, "node2vec: Scalable Feature Learning for Networks," in Proceedings of the 22nd ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 2016, pp. 855--864.
- R. Matzner, D. Semrau, R. Luo, G. Zervas, P. Bayvel, "Making Intelligent Topology Design Choices: Understanding Structural & Physical Property Performance Implications in Optical Networks," Journal of Optical Communications and Networking, vol. 13, no. 8, pp. D53--D67, 2021.
- M. Zhang, "Graph Neural Networks: Link Prediction," in Graph Neural Networks: Foundations, Frontiers, and Applications, L. Wu, P. Cui, J. Pei, L. Zhao, Eds. Springer Singapore, 2022, pp. 195--223.
- P. Wright, R. Davey, A. Lord, "Cost Model Comparison of ZR/ZR+ Modules Against Traditional WDM Transponders for 400G IP/WDM Core Networks," in 2020 European Conference on Optical Communications (ECOC), IEEE, 2020, pp. 1--4.

