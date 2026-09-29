# EventPriority

```TypeScript
export enum EventPriority
```

Enumerates the event priorities.

**Since:** 7

<!--Device-emitter-export enum EventPriority--><!--Device-emitter-export enum EventPriority-End-->

**System capability:** SystemCapability.Notification.Emitter

## IMMEDIATE

```TypeScript
IMMEDIATE = 0
```

The event will be emitted before high-priority events.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-EventPriority-IMMEDIATE = 0--><!--Device-EventPriority-IMMEDIATE = 0-End-->

**System capability:** SystemCapability.Notification.Emitter

## HIGH

```TypeScript
HIGH
```

The event will be emitted before low-priority events.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-EventPriority-HIGH--><!--Device-EventPriority-HIGH-End-->

**System capability:** SystemCapability.Notification.Emitter

## LOW

```TypeScript
LOW
```

The event will be emitted before idle-priority events. By default, an event is in LOW priority.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-EventPriority-LOW--><!--Device-EventPriority-LOW-End-->

**System capability:** SystemCapability.Notification.Emitter

## IDLE

```TypeScript
IDLE
```

The event will be emitted after all the other events.

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-EventPriority-IDLE--><!--Device-EventPriority-IDLE-End-->

**System capability:** SystemCapability.Notification.Emitter
