# InnerEvent

```TypeScript
export interface InnerEvent
```

Describes an event to subscribe to or emit. The **EventPriority** settings do not take effect under event subscription.

**Since:** 7

<!--Device-emitter-export interface InnerEvent--><!--Device-emitter-export interface InnerEvent-End-->

**System capability:** SystemCapability.Notification.Emitter

## Modules to Import

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## eventId

```TypeScript
eventId: number
```

Event ID.

**Type:** number

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-InnerEvent-eventId: long--><!--Device-InnerEvent-eventId: long-End-->

**System capability:** SystemCapability.Notification.Emitter

## priority

```TypeScript
priority?: EventPriority
```

Event priority. The default value is **EventPriority.LOW**.

**Type:** [EventPriority](arkts-basicservices-emitter-eventpriority-e.md)

**Since:** 7

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-InnerEvent-priority?: EventPriority--><!--Device-InnerEvent-priority?: EventPriority-End-->

**System capability:** SystemCapability.Notification.Emitter
