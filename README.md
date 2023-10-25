# linkwise

### Topology-Driven Edge Predictions with Graph Machine Learning for Optical Network Growth: 
Graph representation learning on real-world optical core networks outperforms edge prediction heuristics by 10 times, achieving up to 93.4% accuracy on BT(UK), COST(EU), and CORONET(USA) by learning from 10% training data.

### Code



### Dataset
- COST has been taken from SNDLib http://sndlib.zib.de/home.action
- CORONET has been taken from https://github.com/XuYZh/Network-Pruning-and-Growth---Probabilistic-Optimization
- Raw dataset files have been added for users in case they need them.
- We process these topologies as graphs and manually hardcoded them into our code to be available in the Networkx format suitable for our analysis
- We also have processed and saved Networkx into multiple formats for the user.

### Please Note: 
- _Data about BT's infrastructure is not available due to privacy concerns. Users can utilise the COST or CORONET topologies provided in the code for analysis._
- Random seeds can generate different results at each run; irrespective of the minor changes, the performance gains for our model compared to heuristics remain 10x.
