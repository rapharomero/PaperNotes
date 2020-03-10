# Subjectively interesting connecting trees

This paper describes an algorithm that finds the most Subjectively interesting pattern given a graph and a set of query nodes.
A pattern in a graph will typically be a subgraph.
In order to restrict the number of possible patterns, the authors restrict the;selves to four types of patterns: trees and forests for undirected graphs, branchings and arborescences for directed graphs.
The two latter are the directed analogues of trees and forests.

### Problem formulation
Given an undirected graph G and a query Q, a connecting tree is a spanning tree T of the graph such that all the vertices in Q are contained in the nodes of T.
The goal of this paper is to find the tree included in G that connects the nodes in Q and maximizes the Subjective Interestingness(SI).

### Definition of the Subjective Interestingness

The SI is defined as the ration of the Information Content(IC), and the Description Length(DL) of the tree (or pattern more generally) T.
The DL of the tree T is the length of the code needed to communicate the tree to the user. It depends on the number of vertices of the graph, the number of nodes in the query, as well as the number of nodes that will be contained in the tree.
The IC of T is defined as the negative log probability of the pattern under a certain probability distribution P (also called background distribution) defined using prior beliefs on the desired trees.

### Definition of the background distribution  
The background distributions are determined by solving the maximum entropy problem on the set of probabilities satisfying a certain number of constraints that encode the prior beliefs of the data miner on the patterns that should be found.
In the article, several possible prior beliefs presented, as well as  an efficient heuristic to determine the Lagrange multipliers associated with the MaxEnt problem.

### Algorithm to find the most SI patterns on a graph
Once the measure of SI is defined, the problem of finding the most SI arborescence on a graph can be casted into a minimum Steiner arborescence, which is NP Hard.
In the case where the background distribution is uniform, several heuristics exist and can be used to solve the problem.
For the other cases, fast heuristics are presented in the articles to solve the problem.
The algorithm to find the most SI arborescence on a graph can then be adapted for solving the problem for other types of patterns (trees, forests and branchings)).
