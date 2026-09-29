# Options

```TypeScript
export interface Options
```

Describes the event emit priority.

**Since:** 11

<!--Device-emitter-export interface Options--><!--Device-emitter-export interface Options-End-->

**System capability:** SystemCapability.Notification.Emitter

## Modules to Import

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## priority

```TypeScript
priority?: EventPriority
```

Event priority. The default value is **EventPriority.LOW**.

**Type:** [EventPriority](arkts-basicservices-emitter-eventpriority-e.md)

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-Options-priority?: EventPriority--><!--Device-Options-priority?: EventPriority-End-->

**System capability:** SystemCapability.Notification.Emitter
