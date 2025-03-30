- this is in the context of event streaming, specifically in kafka, but applies to any kind of streaming, and in fact, any kind of data passing.
- this describes a method for designing the information architecture of your system, even if your system's users are developers.

- Related: [Information Architecture (www.usability.gov)](https://www.usability.gov/what-and-why/information-architecture.html) + the general concept of IA.

- in Kafka,
  - topics are the unit of consumption of change
  - schemas (ie. event types) are the unit of change

- your system should have each thing that can change for different reasons as its own event type.
  - where a single logical change affects multiple domain entities, it should still be stored as a single event type. It's easier to split event types later than to re-combine them.

- your system should combine event types that are used for the same reasons into topics (and separate event types that are used for different reasons into topics)

... [see notes on client laptop]
