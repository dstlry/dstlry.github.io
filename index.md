## What is dstlr?

`dstlr` is a system for large-scale knowledge extraction using [Stanford CoreNLP](https://stanfordnlp.github.io/CoreNLP/), [Apache Spark](https://spark.apache.org/), and [neo4j](https://neo4j.com/). It takes a (potentially large) collection of unstructured text documents and horiztonally scales out CoreNLP via Spark to extract mentions of named entities, the relations between them, and links to an entity in an existing knowledge base. For relations of interest, we augment our extracted facts with corresponding ground-truth values from an existing knowledge base in order to reason about the quality of the text documents. From this, we generate a knowledge graph on which we can pose a number of queries via neo4j's Cypher query language to explore the text in a more structured manner.

We can discover a number of different scenarios relating facts asserted in documents to facts present in the knowledge base:
+ Supporting information - agreement between value in document and ground-truth from knowledge base
+ Inconsistent information - disagreement between value in document and ground-truth from knowledge base
+ Missing information - document contains information missing in knowledge base

In our system, we link mentions of entities to Wikidata entities.
