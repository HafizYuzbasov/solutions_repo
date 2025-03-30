# Problem 1

# Equivalent Resistance Using Graph Theory

## Task 1: Simplified Algorithm Description

### Introduction

Calculating the equivalent resistance of a circuit is fundamental in electrical engineering. While traditional methods involve iteratively applying series and parallel resistor rules, these approaches can become cumbersome for complex circuits with many components. Graph theory offers a more systematic and algorithmic approach to solving this problem.

In this approach:

- **Nodes** represent junctions in the circuit.
- **Edges** represent resistors, with the resistance values as the weights of the edges.

This document describes the algorithm for calculating the equivalent resistance of a circuit using graph theory.

---

### Key Concepts for the Algorithm

#### Series Connection:

- **Series connection**: Resistors are connected end-to-end, and the total resistance is the sum of individual resistances.

  Formula for series resistors:

  $$
  R_{eq} = R_1 + R_2 + \cdots + R_n
  $$

  Example: For two resistors \( R_1 = 6 \, \Omega \) and \( R_2 = 3 \, \Omega \) in series:

  $$
  R_{eq} = R_1 + R_2 = 6 + 3 = 9 \, \Omega
  $$

#### Parallel Connection:

- **Parallel connection**: Resistors have both terminals connected to the same pair of nodes, and the total resistance is found using the parallel resistance formula.

  Formula for parallel resistors:

  $$
  \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \cdots + \frac{1}{R_n}
  $$

  Example: For two resistors \( R_1 = 6 \, \Omega \) and \( R_2 = 3 \, \Omega \) in parallel:

  $$
  \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} = \frac{1}{6} + \frac{1}{3} = \frac{1}{R_{eq}} = \frac{1}{2}
  $$

  Thus, the equivalent resistance is:

  $$
  R_{eq} = 2 \, \Omega
  $$

---

### Algorithm Description

The algorithm simplifies the circuit by **iteratively reducing the graph**. This reduction involves identifying series and parallel connections and simplifying them step by step until only one node remains, representing the total equivalent resistance.

#### Step 1: Represent the Circuit as a Graph

- **Nodes**: Each junction in the circuit is represented by a node in the graph.
- **Edges**: Each resistor is represented as an edge between two nodes, with the resistance as the weight of the edge.

Example:

- Two resistors \( R_1 = 6 \, \Omega \) and \( R_2 = 3 \, \Omega \) in series:
  - \( R_1 \) is connected to node 1, and \( R_2 \) is connected between node 2 and node 3.
- The graph representation has three nodes (1, 2, and 3) and two edges representing \( R_1 \) and \( R_2 \).

#### Step 2: Detect Series and Parallel Connections

We will iteratively reduce the graph by simplifying the series and parallel connections.

##### Series Connections:

- If two resistors are in series (i.e., connected end-to-end), combine them by adding their resistance values.

  For two resistors \( R_1 \) and \( R_2 \) in series, the equivalent resistance is:

  $$
  R_{eq} = R_1 + R_2
  $$

  This process is repeated until no more simple series connections are left.

##### Parallel Connections:

- If two resistors are in parallel (i.e., connected between the same two nodes), combine them using the parallel formula.

  For two resistors \( R_1 \) and \( R_2 \) in parallel, the equivalent resistance is:

  $$
  \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
  $$

  This process is repeated until no more simple parallel connections are left.

#### Step 3: Iterative Graph Reduction

After identifying and simplifying the series and parallel connections, the graph is reduced step-by-step:

1. **Identify series connections**: Traverse the graph and check for resistors that are connected in series. Once identified, combine them by adding their resistance values.
2. **Identify parallel connections**: Similarly, check for resistors that are connected in parallel. Combine them using the parallel resistance formula.
3. **Repeat the process**: After each reduction (whether series or parallel), the graph is updated. New series or parallel connections may emerge from the simplification, so the process is repeated until the graph is reduced to a single equivalent resistance.

#### Step 4: Final Simplification

- The algorithm continues simplifying the circuit until only **one node** remains, and the resistance of this node is the equivalent resistance of the entire circuit.

---

### Pseudocode for the Algorithm

```plaintext
Algorithm: Calculate Equivalent Resistance Using Graph Theory

Input: Graph G with nodes representing junctions and edges representing resistors
Output: Equivalent resistance of the entire circuit

1. Initialize the graph G with nodes and resistors (edges with weights).
2. While the graph contains more than one node:
   a. Detect and simplify **series connections**:
      - For each pair of nodes connected by resistors in series:
        - Combine the resistances by adding their weights.
        - Remove the original nodes and replace them with a new node that has the combined resistance.
   b. Detect and simplify **parallel connections**:
      - For each set of nodes connected by resistors in parallel:
        - Combine the resistances using the parallel formula.
        - Remove the original resistors and replace them with a new equivalent resistor.
3. Once the graph is reduced to a single node, return the equivalent resistance of that node.

```

# Step-by-Step Solution for Task 2: Equivalent Resistance Calculation Using Graph Theory

## Key Concepts:

### Series Resistors:

- The equivalent resistance of two resistors \( R_1 \) and \( R_2 \) in series is simply the sum:

  $$
  R_{eq} = R_1 + R_2
  $$

### Parallel Resistors:

- The equivalent resistance of two resistors \( R_1 \) and \( R_2 \) in parallel is given by:

  $$
  \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
  $$

### Graph Representation:

- **Nodes** represent junctions in the circuit.
- **Edges** represent resistors with **weights** equal to their resistance values.

The circuit is represented as an undirected graph, where the resistors are edges with weights, and the junctions are the nodes.

## Simplification Process:

1. **Series Resistor Simplification:**

   - If two resistors are in series, their resistances add up. For nodes \( A \), \( B \), and \( C \), where \( A \) is connected to \( B \) and \( B \) is connected to \( C \), replace the two resistors (edges) with one equivalent resistor whose resistance is the sum of the two.

   $$
   R_{eq} = R_1 + R_2
   $$

   After the simplification, remove the two original resistors and add a new one between \( A \) and \( C \).

2. **Parallel Resistor Simplification:**

   - If two resistors are in parallel, their combined resistance is given by the formula:

   $$
   \frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2}
   $$

   For nodes \( A \), \( B \), and \( C \), where \( A \) is connected to \( B \), and \( B \) is connected to \( C \), replace the two resistors (edges) with one equivalent resistor using the formula above. Remove the two original resistors and add a new one between \( A \) and \( C \).

## Step-by-Step Process:

### 1. **Graph Creation:**

- First, a graph is created using the `networkx` library where:
  - **Nodes** represent junctions in the circuit.
  - **Edges** represent the resistors, with each edge having a weight representing the resistance value.

Example:

- Resistor \( R_1 = 6 \) ohms between nodes 1 and 2.
- Resistor \( R_2 = 3 \) ohms between nodes 2 and 3.
- Resistor \( R_3 = 4 \) ohms between nodes 3 and 4.
- Resistor \( R_4 = 5 \) ohms between nodes 2 and 5.
- Resistor \( R_5 = 2 \) ohms between nodes 4 and 6.

### 2. **Series Resistor Detection:**

- Identify two resistors that are connected in series by looking for nodes that have exactly two neighbors.
- Apply the series simplification formula to these pairs and replace them with a single equivalent resistor.

Example:

- If \( R_1 \) and \( R_2 \) are in series, their equivalent resistance will be:
  $$
  R_{eq} = R_1 + R_2
  $$

After simplification, update the graph with a new edge that represents the equivalent resistance.

### 3. **Parallel Resistor Detection:**

- Identify two resistors that are connected in parallel by looking for nodes that have two neighbors with the same connecting node.
- Apply the parallel simplification formula to these pairs and replace them with a single equivalent resistor.

Example:

- If \( R_2 \) and \( R_3 \) are in parallel, their equivalent resistance will be:
  $$
  \frac{1}{R_{eq}} = \frac{1}{R_2} + \frac{1}{R_3}
  $$

After simplification, update the graph with a new edge that represents the equivalent resistance.

### 4. **Repeat Simplification:**

- Continue the simplification process until only one edge remains in the graph.
- The remaining edge represents the **equivalent resistance** of the entire circuit.

### 5. **Final Result:**

- The final equivalent resistance is the weight of the last remaining edge in the graph, which is the simplified result of the entire circuit.

## Example Circuit:

### Graph Representation:

Nodes: \( 1, 2, 3, 4, 5, 6 \)  
Edges:

- \( (1, 2, R_1 = 6 \, \Omega) \)
- \( (2, 3, R_2 = 3 \, \Omega) \)
- \( (3, 4, R_3 = 4 \, \Omega) \)
- \( (2, 5, R_4 = 5 \, \Omega) \)
- \( (4, 6, R_5 = 2 \, \Omega) \)

```python
import networkx as nx
import matplotlib.pyplot as plt

# Function to plot the graph for visualization
def plot_graph(G, title="Circuit Graph"):
    pos = nx.spring_layout(G)  # Layout for better visualization
    plt.figure(figsize=(10, 8))
    node_size = [500 + 100 * G.degree(node) for node in G.nodes]
    node_color = ['lightgreen' if G.degree(node) == 1 else 'lightblue' for node in G.nodes]
    nx.draw(G, pos, with_labels=True, node_color=node_color, node_size=node_size, font_size=15, font_weight="bold", edge_color="gray")

    edge_labels = nx.get_edge_attributes(G, 'weight')
    nx.draw_networkx_edge_labels(G, pos, edge_labels=edge_labels, font_size=12)

    plt.title(title)
    plt.axis('off')  # Hide axes for a cleaner presentation
    plt.show()

# Function to find series resistors
def find_series_resistors(G):
    series_pairs = []
    for node in G.nodes:
        neighbors = list(G.neighbors(node))

        if len(neighbors) == 2:  # Exactly two neighbors for series connection
            if G[node][neighbors[0]]['weight'] and G[node][neighbors[1]]['weight']:
                series_pairs.append((node, neighbors[0], neighbors[1]))
    return series_pairs

# Function to find parallel resistors
def find_parallel_resistors(G):
    parallel_pairs = []
    for node in G.nodes:
        neighbors = list(G.neighbors(node))

        if len(neighbors) == 2:  # Exactly two neighbors for parallel connection
            if G[node][neighbors[0]]['weight'] and G[node][neighbors[1]]['weight']:
                parallel_pairs.append((node, neighbors[0], neighbors[1]))
    return parallel_pairs

# Function to simplify a series resistor
def simplify_series(G, series_pair):
    node1, node2, node3 = series_pair
    R1 = G[node2][node1]['weight']
    R2 = G[node3][node2]['weight']
    R_eq = R1 + R2  # Series combination

    # Remove the two resistors and add the equivalent one
    G.remove_edge(node2, node1)
    G.remove_edge(node3, node2)
    G.add_edge(node1, node3, weight=R_eq)
    return G

# Function to simplify a parallel resistor
def simplify_parallel(G, parallel_pair):
    node1, node2, node3 = parallel_pair
    R1 = G[node1][node2]['weight']
    R2 = G[node2][node3]['weight']
    R_eq = 1 / (1 / R1 + 1 / R2)  # Parallel combination

    # Remove the two resistors and add the equivalent one
    G.remove_edge(node1, node2)
    G.remove_edge(node2, node3)
    G.add_edge(node1, node3, weight=R_eq)
    return G

# Main function to calculate equivalent resistance
def calculate_equivalent_resistance(G):
    # Initial graph plot
    plot_graph(G, title="Initial Circuit Graph")

    step = 1
    # Keep simplifying the graph until only one edge remains
    while len(G.edges) > 1:
        # Simplify series connections
        series_pairs = find_series_resistors(G)
        if series_pairs:
            print(f"Step {step}: Simplifying series pairs: {series_pairs}")
        for series_pair in series_pairs:
            G = simplify_series(G, series_pair)

        # Plot after simplifying series resistors
        plot_graph(G, title=f"After Step {step}: Simplified Series Resistors")

        # Simplify parallel connections
        parallel_pairs = find_parallel_resistors(G)
        if parallel_pairs:
            print(f"Step {step}: Simplifying parallel pairs: {parallel_pairs}")
        for parallel_pair in parallel_pairs:
            G = simplify_parallel(G, parallel_pair)

        # Plot after simplifying parallel resistors
        plot_graph(G, title=f"After Step {step}: Simplified Parallel Resistors")

        step += 1

    # The final equivalent resistance is the only edge left in the graph
    final_resistance = None
    for edge in G.edges(data=True):
        final_resistance = edge[2]['weight']

    return final_resistance

# Example usage: Create a circuit graph
G = nx.Graph()

# Adding resistors (edges) to the circuit
# Resistor values: R1 = 6 ohms, R2 = 3 ohms, R3 = 4 ohms, R4 = 5 ohms, R5 = 2 ohms
G.add_edge(1, 2, weight=6)  # R1
G.add_edge(2, 3, weight=3)  # R2
G.add_edge(3, 4, weight=4)  # R3
G.add_edge(2, 5, weight=5)  # R4
G.add_edge(4, 6, weight=2)  # R5

# Call the function to calculate the equivalent resistance
equivalent_resistance = calculate_equivalent_resistance(G)
print(f"The equivalent resistance of the circuit is: {equivalent_resistance} ohms")

```

![alt text](image.png)
