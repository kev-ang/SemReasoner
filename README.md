# SemReasoner
Knowledge graphs have become an important technology for integrating data from heterogeneous sources powering intelligent applications. Integrating data from various sources often results in incomplete knowledge that needs to be enriched based on custom inference rules. Handling a large number of facts requires a scalable storage layer, and this storage layer must be seamlessly integrated into the reasoning algorithms to guarantee efficient evaluation of rules and query answering over the knowledge graph. To this end, we present SemReasoner, a comprehensive, scalable, high-performance knowledge graph store, and rule-based reasoner. SemReasoner includes a deductive reasoning engine and fully supports document store functionality for JSON documents. SemReasoner's modular architecture is easy to extend and integrate into existing IT landscapes and applications. Besides, we classify different existing engines according to a set of characteristics. Finally, we evaluate SemReasoner and competing engines using the OpenRuleBench test cases. Our results show that SemReasoner outperforms existing engines.

## Repository content
This repository currently contains:
- a documentation
- a tutorial to program with SemReasoner
- Javadoc for the APIs SemReasoner provides

## Playing around with SemReasoner
A single SemReasoner instance with a simple demo interface is available [here](http://95.217.61.50:8100/). It allows to provide JSON documents, rules, and a query. When submitting the data, a single reasoning core is initialized, the rules and the query are executed and the result returned. The data is not persisted in this simple demo version.
