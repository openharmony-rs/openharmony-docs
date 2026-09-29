# GenericEventData

```TypeScript
export interface GenericEventData<T>
```

Describes the generic data carried by the emitted event.

**Since:** 12

<!--Device-emitter-export interface GenericEventData<T>--><!--Device-emitter-export interface GenericEventData<T>-End-->

**System capability:** SystemCapability.Notification.Emitter

## Modules to Import

```TypeScript
import { emitter } from '@kit.BasicServicesKit';
```

## data

```TypeScript
data?: T
```

Data carried by the emitted event. **T** represents a generic type, which can be customized based on service requirements.

**Type:** T

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GenericEventData-data?: T--><!--Device-GenericEventData-data?: T-End-->

**System capability:** SystemCapability.Notification.Emitter
