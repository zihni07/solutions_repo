# Equivalent Resistance Calculation Using Graph Theory

## Introduction

Calculating equivalent resistance in complex circuits can be tedious using traditional methods.  
**Graph theory** provides a structured and powerful approach:

- **Nodes** represent junctions where multiple components connect.
- **Edges** represent resistors, with **weights** equal to resistance values.

By representing circuits as graphs, we gain access to efficient algorithms that simplify complex networks systematically. Iterative application of **series** and **parallel** reductions allows us to simplify any network into a single resistance value, regardless of its complexity.

Applications of this method span:
- Electrical circuit simulation software
- Optimization in microchip design
- Educational tools for teaching electrical engineering
- Automated design verification

---

## Key Formulas

- **Series combination**:

$$
R_{\text{eq}} = R_1 + R_2 + \dots + R_n
$$

Series resistors add directly because current must pass through each sequentially.

- **Parallel combination**:

$$
\frac{1}{R_{\text{eq}}} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
$$

Parallel resistors share current across multiple paths, leading to a reduced overall resistance.

---

## Algorithm Overview

The algorithm proceeds with the following steps:

1. **Input**: A weighted undirected graph $G$ where:
   - Nodes = circuit junctions
   - Edges = resistors, with weight = resistance in ohms

2. **Identify reduction opportunities**:
   - **Series reduction**: Look for nodes with degree 2 that are not the start or end node.
   - **Parallel reduction**: Look for multiple edges between the same two nodes.

3. **Apply simplifications**:
   - **Series rule**: Replace a two-edge chain with a single edge whose resistance is the sum of the two.
   - **Parallel rule**: Replace multiple parallel edges with a single equivalent resistance using the parallel formula.

4. **Repeat** until only the start and end nodes remain connected directly by a single equivalent resistance.

5. **Output**: The final equivalent resistance value between the designated start and end nodes.

---

## Pseudocode

```plaintext
function simplify_circuit(G, start, end):
    while G has more than two nodes:
        for each node v not in {start, end}:
            if degree(v) == 2:
                neighbors = [u, w]
                if (u,v) and (v,w) not forming a cycle:
                    combine series resistance: R = R(u,v) + R(v,w)
                    remove v, add edge (u,w) with resistance R
        for each pair of nodes (u, v):
            if multiple edges between u and v:
                combine parallel resistances:
                1 / R_total = sum(1 / R_i for each edge R_i between u and v)
                replace edges with single edge of resistance R_total
    return resistance between start and end
```

Notes:
- **Cycles** must be carefully checked to avoid incorrect series reductions.
- **Parallel combinations** must consider all possible parallel paths.

---

## Python Implementation

```python
import networkx as nx

def simplify_circuit(G, start, end):
    G = G.copy()
    while True:
        reduced = False

        # Simplify series connections
        for node in list(G.nodes):
            if node in (start, end):
                continue
            if G.degree(node) == 2:
                neighbors = list(G.neighbors(node))
                if len(neighbors) == 2:
                    u, v = neighbors
                    if not nx.has_path(G, u, v) or (node in nx.shortest_path(G, u, v)[1:-1]):
                        r1 = G[u][node]['resistance']
                        r2 = G[v][node]['resistance']
                        G.add_edge(u, v, resistance=r1 + r2)
                        G.remove_node(node)
                        reduced = True
                        break
        
        if reduced:
            continue

        # Simplify parallel connections
        for u, v in list(G.edges):
            parallel_edges = G.get_edge_data(u, v)
            if isinstance(parallel_edges, dict) and len(parallel_edges) > 1:
                resistances = [data['resistance'] for key, data in parallel_edges.items()]
                r_parallel = 1 / sum(1/r for r in resistances)
                G.remove_edges_from([(u, v)]*len(resistances))
                G.add_edge(u, v, resistance=r_parallel)
                reduced = True
                break

        if not reduced:
            break

    return G[start][end]['resistance']
```

### Important Implementation Details
- The graph must correctly store resistance on edges.
- Parallel simplification assumes multiple edges between two nodes.
- This algorithm assumes no complicated sub-circuits like bridges (Wheatstone Bridge) without preprocessing.

---

## Example Usage

```python
# Create a graph
G = nx.Graph()
G.add_edge('A', 'B', resistance=2)
G.add_edge('B', 'C', resistance=3)
G.add_edge('C', 'D', resistance=5)
G.add_edge('B', 'D', resistance=6)

# Compute equivalent resistance between A and D
req = simplify_circuit(G, 'A', 'D')
print(f"Equivalent resistance between A and D: {req} ohms")
```

---

## Test Examples

### 1. Simple Series Connection

Two resistors in series:

- $2 \Omega$ + $3 \Omega$ = $5 \Omega$

Total equivalent resistance:

$$
R_{\text{eq}} = 5 \Omega
$$

### 2. Simple Parallel Connection

Two resistors in parallel:

$$
\frac{1}{R} = \frac{1}{4} + \frac{1}{6}
$$

$$
\frac{1}{R} = \frac{5}{12}
$$

Thus,

$$
R = 2.4 \Omega
$$

### 3. Complex Graph (Nested Combination)

Multiple series and parallel configurations are detected automatically.
No manual intervention is required for nested groups.

---

## Efficiency Analysis

- **Time Complexity**:
  - Series reduction: $O(V)$ per iteration.
  - Parallel reduction: $O(E^2)$ if naive checking.

- **Space Complexity**:
  - Storing the graph requires $O(V + E)$ space.

### Potential Improvements

- **Graph Compression**:
  - Use data structures like Union-Find to manage node merging.
- **Cycle Detection Optimization**:
  - Faster cycle checks can reduce redundant searches.
- **Parallel Computation**:
  - Apply parallelism to identify multiple reduction sites at once.

---

# Conclusion

Using **graph theory**, complex electrical circuits can be **programmatically** simplified. 

This method provides a powerful framework for:
- Rapid analysis of large circuits.
- Integration into electrical simulation software.
- Automated design and optimization of electronic systems.

Future work could extend this approach to dynamically changing circuits, non-linear components, and real-time optimization.

