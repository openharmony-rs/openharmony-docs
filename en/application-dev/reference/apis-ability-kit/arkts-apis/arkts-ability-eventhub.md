# EventHub(EventHub)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [EventHub](arkts-ability-eventhub-c.md) | EventHub is an event communication mechanism based on the publish-subscribe pattern. It decouples senders and subscribers through event names, supporting efficient data transfer and state synchronization between different service modules. It is primarily used for [data communication between UIAbility components and UI pages](../../../application-models/uiability-data-sync-with-ui.md). Different Context objects have different EventHub objects, and different EventHub objects cannot communicate directly with each other. Event subscription, unsubscription, and triggering all take place on a specific EventHub object. Since Worker and TaskPool implement [multithreaded concurrency](../../../arkts-utils/multi-thread-concurrency-overview.md#multithreaded-concurrency-models) through the actor model, where different virtual machine instances have exclusive memory, EventHub objects cannot be used for inter-thread data communication. |
