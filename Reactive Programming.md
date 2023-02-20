---
tag: [[Programming]]
---
# Reactive Programming and ReactiveX

So what is reactive programming ? It is a way to write event driven code. The name comes from the fact that a reactive code is composed of entities that react to events being emitted by sources. These entities apply transformations on these events, and return other events as a result. So these entities - named _operators_ - can be chained together, to create computation graphs.

Reactive computation graphs are always directed. They flow in only one way. Some graphs are _Directed Acyclic Graphs_ - DAG - like this one:

![[graph_dag.png|{width=50%}]]



