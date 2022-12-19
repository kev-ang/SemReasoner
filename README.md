# SemReasoner
Knowledge graphs have become an important technology for integrating data from heterogeneous sources powering intelligent applications. Integrating data from various sources often results in incomplete knowledge that needs to be enriched based on custom inference rules. Handling a large number of facts requires a scalable storage layer, and this storage layer must be seamlessly integrated into the reasoning algorithms to guarantee efficient evaluation of rules and query answering over the knowledge graph. To this end, we present SemReasoner, a comprehensive, scalable, high-performance knowledge graph store, and rule-based reasoner. SemReasoner includes a deductive reasoning engine and fully supports document store functionality for JSON documents. SemReasoner's modular architecture is easy to extend and integrate into existing IT landscapes and applications. Besides, we classify different existing engines according to a set of characteristics. Finally, we evaluate SemReasoner and competing engines using the OpenRuleBench test cases. Our results show that SemReasoner outperforms existing engines.

## Repository content
This repository currently contains:
- a documentation
- a tutorial to program with SemReasoner
- Javadoc for the APIs SemReasoner provides

## Playing around with SemReasoner
A single SemReasoner instance with a simple demo interface is available [here](http://95.217.61.50:8100/). It allows to provide JSON documents, rules, and a query. When submitting the data, a single reasoning core is initialized, the rules and the query are executed and the result returned. The data is not persisted in this simple demo version.

## Evaluation Results

### No Materialization

#### Join 1
| Engine | a no bindings | b1 no bindings | b2 no bindings || a 1st argument bound | b1 1st argument bound | b2 1st argument bound || a 2nd argument bound | b1 2nd argument bound | b2 2nd argument bound |
|--------|---------------|----------------|----------------||----------------------|-----------------------|-----------------------||----------------------|-----------------------|-----------------------|
| Jena | timeout | timeout | 51,134 || timeout | timeout | timeout || timeout | timeout | timeout |
| SemReasoner (Memory) | 232.33 (30.89) | 220.67 (10.69) | 220.67 (10.69) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |
| SemReasoner (Persistent) | 299.33 (8.08) | 289.67 (9.07) | 286.67 (5.77) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |
| Stardog | exception | 409.67 (13.28) | 249.00 (2.65) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |


#### Datalog Recursion
| Engine | Cyc | No Cyc |
|--------|-----|--------|
| Jena | timeout | timeout |
| SemReasoner (Memory) | 7,941.33 (341.90) | 7,085.22 (134.69) |
| SemReasoner (Persistent) | 6,592.67 (300.34) | 6,084.67 (327.65) |
| Stardog | 62.67 (3.21) | 40.00 (2.00) |

### Materialization

#### Join 1
| Engine | Materialization | a no bindings | b1 no bindings | b2 no bindings || a 1st argument bound | b1 1st argument bound | b2 1st argument bound || a 2nd argument bound | b1 2nd argument bound | b2 2nd argument bound |
|--------|-----------------|---------------|----------------|----------------||----------------------|-----------------------|-----------------------||----------------------|-----------------------|-----------------------|
| RDFox | 143,565.67 (2,452.67) | 32.00 (0.00) | 28.00 (0.00) | 27.67 (0.58) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |
| SemReasoner | 118,427.00 (2,493.72) | 526.00 (51.12) | 199.33 (9.29) | 248.33 (11.37) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |
| VLog | 518,676.22 (369.55) | 129.33 (20.50) | 115.33 (1.53) | 117.67 (1.53) || (coming soon) | (coming soon) | (coming soon) || (coming soon) | (coming soon) | (coming soon) |


#### Datalog Recursion
| Engine | Materialization | Cyc | Materialization | No Cyc |
|--------|-----------------|-----|-----------------|--------|
| RDFox | 9,521.33 (476.92) | 7 (0.00) | 8,329.67 (156.07) | 7.00 (0.00) |
| SemReasoner | 1,653.33 (1,638.28) | 56.67 (1.15) | 1,128.67 (57.14) | 54.33 (1.15) |
| VLog | 24,245.67 (78.68) | 29.00 (1.00) | 21,467.00 (54.11) | 28.33 (1.15) |


#### Negation
#### Datalog Recursion
| Engine | Materialization | Query Response |
|--------|-----------------|----------------|
| RDFox | 6,751.67 (10.69) | 0.33 (0.58) |
| SemReasoner | 11,637.67 (278.32) | 0.67 (0.58) |
| VLog | 9,135.00 (7.94) | 0.00 (0.00) |
