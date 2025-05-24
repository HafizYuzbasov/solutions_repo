# Problem 1


---

# Circuits

## Problem 1

### **Equivalent Resistance Using Graph Theory**

---

### Motivation

Calculating equivalent resistance is a fundamental problem in circuit analysis. Traditional methods involve applying series and parallel rules manually, which can become tedious for complex circuits. Graph theory provides an elegant alternative: by modeling the circuit as a weighted graph, we can systematically simplify it using algorithms.

* **Nodes (Vertices)** represent junctions in the circuit.
* **Edges** represent resistors with weights equal to their resistance values.

This approach is not only theoretically rich but also enables automated analysis for complex systems.

---

### Task: Advanced Solution – Full Implementation

---

## 🧮 Theoretical Foundation

### Equivalent Resistance:

For a graph $G = (V, E)$:

* **Series Rule**:

  * Resistors in a chain (single path between nodes) add up:
  * $R_{eq} = R_1 + R_2 + \dots$

* **Parallel Rule**:

  * Resistors in parallel (multiple paths between nodes) combine via reciprocals:
  * $\frac{1}{R_{eq}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots$

---

## 📝 Pseudocode

```
Algorithm CalculateEquivalentResistance(graph, source, target):
    1. While graph has more than 2 nodes:
        a. For each node with exactly 2 neighbors:
            - If only 1 path between nodes: Combine series resistors.
        b. For each pair of nodes with multiple parallel edges:
            - Combine parallel resistors.
    2. If only source and target nodes remain:
        - Return resistance between source and target.

    Note:
    - Detect cycles for parallel paths.
    - Detect chains for series paths.
```

---

## 🚀 Python Implementation

```python
import networkx as nx

def combine_series(G):
    changed = False
    for node in list(G.nodes):
        neighbors = list(G.neighbors(node))
        if len(neighbors) == 2 and node not in ['source', 'target']:
            u, v = neighbors
            R1 = G.edges[node, u]['resistance']
            R2 = G.edges[node, v]['resistance']
            G.add_edge(u, v, resistance=R1 + R2)
            G.remove_node(node)
            changed = True
    return changed

def combine_parallel(G):
    changed = False
    for u, v in list(G.edges):
        parallel_edges = [e for e in G.edges(u, data=True) if e[0] == u and e[1] == v]
        if len(parallel_edges) > 1:
            inv_sum = sum(1 / e[2]['resistance'] for e in parallel_edges)
            R_eq = 1 / inv_sum
            G.remove_edges_from([(u, v) for e in parallel_edges])
            G.add_edge(u, v, resistance=R_eq)
            changed = True
    return changed

def simplify_circuit(G):
    while True:
        if not combine_series(G) and not combine_parallel(G):
            break
    return G

# Example Circuit: Nested Series & Parallel
G = nx.Graph()
G.add_edge('source', 'A', resistance=4)
G.add_edge('A', 'B', resistance=6)
G.add_edge('A', 'B', resistance=3)  # Parallel path
G.add_edge('B', 'target', resistance=2)

G = simplify_circuit(G)
final_R = G.edges['source', 'target']['resistance']
print(f"Equivalent Resistance: {final_R:.2f} Ohms")
```

---

## 🧪 Test Examples

### Example 1: Series Circuit

* 3 resistors in series: $R_1 = 4 \, \Omega, R_2 = 5 \, \Omega, R_3 = 6 \, \Omega$
* $R_{eq} = 4 + 5 + 6 = 15 \, \Omega$

### Example 2: Parallel Circuit

* 2 resistors in parallel: $R_1 = 4 \, \Omega, R_2 = 6 \, \Omega$
* $R_{eq} = \frac{1}{\frac{1}{4} + \frac{1}{6}} = 2.4 \, \Omega$

### Example 3: Complex Circuit

* Nested parallel + series:
* The above example graph: $R_{eq} = 4 + (1 / (1/6 + 1/3)) + 2 = 4 + 2 + 2 = 8 \, \Omega$

---

## 📊 Efficiency Analysis

| Step               | Complexity           |
| ------------------ | -------------------- |
| Series Detection   | $O(n)$ per iteration |
| Parallel Detection | $O(m)$ per iteration |
| Iterations         | Up to $O(n)$ total   |

Overall complexity is $O(n^2)$ in the worst case.

---

## 🔬 Future Extensions

* Handle **nonlinear elements** (e.g., diodes, transistors).
* Solve using **Laplacian matrices** for mesh analysis.
* Support **voltage/current sources** via node voltage methods.

---

If you’d like, I can **package this into a neat notebook** or add **visualization of the graph**! Let me know! 🎓⚡


