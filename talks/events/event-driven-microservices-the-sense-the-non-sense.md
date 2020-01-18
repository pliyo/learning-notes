# GOTO 2019 - Event Driven Microservice, the sense, the non-sense and a way forward by Allard Buijze

[Link to talk](https://www.youtube.com/watch?v=jrbWIS7BH70)

#

Be aware of Maslow's Hammer: `"If you have only a hammer, everything looks like a nail"`

#

- One of the benefits of events is that you can invert the dependency between services

# Patterns

`Event Notification`: It's a pattern where events are used just to tell you
that something happened.

`Event-carried state transfer`: An event has happened somewhere,
and the event contains all the data necessary to explain
what exactly has happened.

`Event-Sourcing`: Where everything becomes an event carried state transfer.

# Journey to Event Sourcing

Start with each service having store to store its state.

For replication we use events that carry all the information they need,
for example `orderCreated`, `itemAdded`, `itemRemoved`.

`Commands`: Route to single handler. Use consistent hashing. Provides confirmation/ result
`Events`: Distribute to all logical handlers. Consumers express ordering req's. No results
`Queries`: Route with load balancing sometimes scatter/gather. provides result.

- Event sourcing is about capturing the truth, the whole truth, and nothing but the truth.

- We don't store state anymore as state. You don't store as snapshop but all the events that led you to a state.

```
Ex: "return Shipment 399"
VS
"Order Created, ItemAdded (x2), ItemRemoved (x1), OrderConfirmed, OrderShipped
OrderCancelledByUser, ReturnShipment"
```

- To test for event sourcing think: If you throw away everything but your events, can you replicate the state of your application?

# Why use Event Sourcing?

- `Business reasons`: Auditing, compliance, transparency, data mining, analytics, value from data
- `Technical reasons`: Guaranteed completeness of raised events,
  single source of truth, concurrency / conflict resolution, facilitates debugging,
  replay into new read model (CQRS), easily cature intent,
  deal with complexity in models

# Real life examples

`SCENARIO`:
Application inserts events in Event Store
Application queries event from Event Store

Works well for processing changes on single entities.
Does not work well for generic queries.
EX: Give me all orders above 100 euros might force you to query all events.

Command query segregation works better

# Bounded Context:

- Explicitly define the context within which a model applies.
- Explicitly set boundaries in terms of team organisation,
  usage within specific parts of the application, and physical manifestations
  such as code bases and databases schemas.
- Keep the model strictly consistent within these bounds, but don´t be distracted
  or confused by issues otherside.
- In a bounded context certain words have a certain meaning.
- In Event Sourcing, even little detail becomes an event that belongs to a bounded context.
- Because we don't wnat to have the same language between two context, you can think of an anti-corruption layer. Also to filter out the messages that are not important to your bounded context.

# Recap

- Consider commands and queries as explicitly as you consider events.
- Microservices are a journey
