---
tag: [[Programming]]
---
## Reactive Programming and ReactiveX

So what is reactive programming ? It is a way to write event driven code. The name comes from the fact that a reactive code is composed of entities that react to events being emitted by sources. These entities apply transformations on these events, and return other events as a result. So these entities - named _operators_ - can be chained together, to create computation graphs.

Reactive computation graphs are always directed. They flow in only one way. Some graphs are _Directed Acyclic Graphs_ - DAG - like this one:

![[graph_dag.png | center | 200]]

On this diagram the nodes represent computations, and the edge the link between computations.

Some graphs may also be Cycle Graphs like this one:
![[graph_cycle.png|center|200]]
Cycle graphs are very common when writing a fully reactive application. Most of the time the major part of an application graph is acyclic, and a sub-part may have cycles.

[ReactiveX](http://reactivex.io/) is the most popular implementation of Reactive Programming libraries. One reason is that it was one of the firsts reactive libraries. It was initially developed by Microsoft for the .net platform. Since 2012 the code is open source, and has been ported to more than 20 programming languages.

The python implementation of ReactiveX is [RxPY](https://github.com/ReactiveX/RxPY). The library is available on pypi and can be installed with pip:

```python
pip3 install rx
```

## Observable, Observer, Operator

The foundation of ReactiveX is based on only a few key principles described in the [Observable Contract](http://reactivex.io/documentation/contract.html).

The base entity in ReactiveX is the **Observable**. An Observable is an entity that is a source of **items**. Item is the ReactiveX term for an event. One could consider and Observable to be a stream of events.

The second entity is the **Observer**. And Observer is the entity that **subscribes** to observers, so that it can process items as they are emitted. The subscription to an observable is explicit, meaning an observable does not emit items until an observer subscribes to it. When an observable is created, no data flows, it only flows when subscribed to.

We can then combine an Observer and an Observable to create an **Operator**. An operator subscribes to a source Observable, applies some transformations to the incoming items, an emits new items on another Observable.

## Marble Diagrams

Motto: A by example way to represent the behaviour of an operator.

Consider the *map* operator, taking items from a source observable, applying a transformation, and returning a sink observable with the transformation function applied to the source items. The marble diagram below explain this:

![[map_marble.png]]

There are three parts to this diagram:
- The top arrow represents the source observable: When being subscribed, this source observable emits the numbers 1 to 4
- The rectangle represents the computation done by the operator. In this example, one is subtracted to each received item.
- The bottom arrow represents the sink Observable. As a result of subtracting 1 to each item, it emits items 0 to 3.