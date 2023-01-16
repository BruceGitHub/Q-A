---
layout: post
title: ""
date: 2023-01-15
tags:
 - [es]
 - [event sourcing]
 - [domain model]
 - [typescript]
 - [functional]
 - [fp]
 - [decider]
 - [evolve]
published: true
---

# Use a concept of sealed interface or union type (limit set of implementation of interface)
So each state of our state-machine (concept) is an implementation 
```java
sealed public interface ShoppingCart {
  record EmptyShoppingCart() implements ShoppingCart {
  }

  record PendingShoppingCart(
    UUID id,
    UUID clientId,
    ProductItems productItems
  ) implements ShoppingCart {
  }

  record ConfirmedShoppingCart(
    UUID id,
    UUID clientId,
    ProductItems productItems,
    OffsetDateTime confirmedAt
  ) implements ShoppingCart {
  }

  record CanceledShoppingCart(
    UUID id,
    UUID clientId,
    ProductItems productItems,
    OffsetDateTime canceledAt
  ) implements ShoppingCart {
  }
}
```
# General overview 
- decide, that runs the command’s business logic on the current state returning event or sequence of events as a result,
- evolve, that applies the event on the state,
- getInitialState, which returns the default, not initialised state.

```ts
export const decider: Decider<
  ShoppingCart,
  ShoppingCartCommand,
  ShoppingCartEvent
> = {
  decide,
  evolve,
  getInitialState: () => {
    return {
      status: 'Empty',
    };
  },
};
```
![](https://thinkbeforecoding.com/public/FreshPaint-21-2014.01.04-10.55.10.png)

```f#
type Command
type Event
type State
initialState: State
decide: Command -> State -> Event list
evolve: State -> Event -> State
```

![](https://thinkbeforecoding.com/public/functional-event-sourcing-decider/diagram-8.svg)


- A Command type that represents all commands that can be submitted to the Decider
- An Event type that represents all events that can be produced by the Decider
- A State type that represents all possible states of the Decider (can just be the list of all events)
- An Initial State that is the state of the Decider before anything happens
- A decide function that takes a Command and a State and returns a list of Event
- An evolve function that takes a State and an Event and returns a new State
- An isTerminal function that takes a State and returns a boolean value

```f#
type Decider<'c,'e,'s> =
    { decide: 'c -> 's -> 'e list
      evolve: 's -> 'e -> 's
      initialState: 's
      isTerminal: 's -> bool }
```


# Reference 
- 2022 - https://event-driven.io/en/type_script_node_Js_event_sourcing/
- 2022 - https://event-driven.io/en/how_to_effectively_compose_your_business_logic/
- 2021 - https://thinkbeforecoding.com/post/2021/12/17/functional-event-sourcing-decider