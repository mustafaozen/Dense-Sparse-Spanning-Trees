# Dense-Sparse-Spanning-Trees-Genetic-Algorithm
This repository provides source codes for Method 2 of the following paper:
M. Ozen, G. Lesaja, and H. Wang, "Globally optimal dense and sparse spanning trees, and their applications", Statistics, Optimization & Information Computing, 8(2), pp. 328-345, 2020.

Finding dense spanning trees(DST) and sparse spanning trees(SST) of a given graph reduces to a discrete optimization problem which is very hard to solve for large graphs with hundreds of vertices and edges. The previously proposed heuristic methods are not efficient, especially for large graphs. In the aforementioned paper, we reduced the problem of finding DSTs and SSTs into an optimization problem and solved it using GA. The proposed approach employs the degree conditions as the new criteria to find DSTs and SSTs for any connected, directed or undirected, weighted or unweighted, large or small graphs efficiently. Furthermore, it can be applied recursively to sub-trees or spanning trees with additional constraints to further investigate the graphical properties of the graph and/or network. Several applications of the method to different networks such as cancer cell gene network, brain network, social networks, and so on, are presented in the paper.

To find DSTs and SSTs approximately, the provided source code employs genetic algorithm(GA) which is one of well-known metaheuristics methods as well as Kruskal's algorithm that further boosts the method by reducing the search space.

# The folder includes the following Matlab functions:

1. main.m: the main file that controls every step of finding dense and sparse spanning trees from a given graph using proposed Method 2.
2. GAoptimization.m: runs Matlab's GA based on user-specified settings.
3. createConstraints.m: creates the constraint for GA (See Method 2 in the paper).
4. MST.m: finds the initial minimum spanning tree using Kruskal's algorithm.
5. cycle_check.m: used in MST.m file to check if an added edge creates a cycle.
6. wiener_index.m: calculates the Wiener index (an objective function).
7. sumPowDegrees: calculates the summation of the power of vertex degrees (another objective function).
8. plotInitialGraph.m: plots the given initial graph.
9. plotOptimalTree.m: plots one of the found trees. 


# To run the code, the instructions are as follows:
    
1. You need to have a list of edges of the initial graph. This can be a 2-column matrix if the edges are not weighted or 3-column matrix where the 3rd column is being weights of the edges. The datasets for the applications used in the paper are given under the "ApplicationDatasets" folder.

2. Specify the objective function. In the code, Weiner Index and Sum of power(p) of degrees are included. Any desired objective function can be implemented and embedded in this code. To change the objective function, go to line 46 in the GAoptimization.m file.

3. Specify objective function settings: a) "wantDense = true" if you want to search for a dense spanning tree. b) "wantDense = false" if you want to search for a sparse spanning tree. c) "isObjFunctMinimized = true" if the desired tree is found by minimizing the objective function. d) "isObjFunctMinimized = false" if the desired tree is found by maximizing the objective function.

Note: The dense(sparse) spanning trees can minimize(maximize) some objective functions while they may maximize(minimize) some other objective functions. Therefore, the type of optimization should be specified. DSTs minimize the Weiner index whereas SSTs maximize the Weiner index. The opposite is true for the sum of power(p) of degrees for p > 1.

4. Genetic algorithm settings: a) Set the "populationSize" to a number. A high population size increases the chance of finding better dense/sparse spanning trees while it increases the time complexity. Also, for large graphs, it is suggested to use a high population size (eg. 5e5, etc.). b) Set "useParallel = true" if you want to run the code in parallel mode. Running in parallel mode will speed up the code as all cores of the computer are used.

Note: You should have the Matlab's Parallel Computing Toolbox installed in your system to run in parallel.

# Test Case(by default):
By default the codes come with the following settings:
1. The dataset is the randomly generated graph ("ToyNetEdges") containing both densest(star) and sparsest(path) trees.

2. The objective function: Wiener Index (minimize for DSTs and maximize for SSTs)

3. Objective function settings: a) wantDense = true; b) isObjFunctMinimized = true;

4. Genetic algorithm settings: a) populationSize = 1e4; b) useParallel = false;

To test the code, go and run the main.m file which has the above default settings. The comments in the code lines will provide further details if any changes needed. The output of the test run are a figure for the globally optimal dense spnning tree, a figure for the toy network, and the objective function value (that is the Wiener index by default) of the dense spanning tree on the command window. 

For theoretical details, please refer to the published paper.
