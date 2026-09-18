# EventPriority

Enumerates the event priorities.

**Since:** 7

**System capability:** SystemCapability.Notification.Emitter

## IMMEDIATE

```TypeScript
IMMEDIATE = 0
```

The event will be emitted before high-priority events.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.Emitter

## HIGH

```TypeScript
HIGH
```

The event will be emitted before low-priority events.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.Emitter

## LOW

```TypeScript
LOW
```

The event will be emitted before idle-priority events. By default, an event is in LOW priority.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.Emitter

## IDLE

```TypeScript
IDLE
```

The event will be emitted after all the other events.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Notification.Emitter
