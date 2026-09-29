# SystemEvent (System API)

```TypeScript
interface SystemEvent
```

Indicates the system event type and parameter related to the screenlock management service.

@typedef SystemEvent

**Since:** 9

<!--Device-screenLock-interface SystemEvent--><!--Device-screenLock-interface SystemEvent-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screenLock } from '@kit.BasicServicesKit';
```

## eventType

```TypeScript
eventType: EventType
```

Indicates the system event type related to the screenlock management service.

**Type:** [EventType](arkts-basicservices-screenlock-eventtype-t-sys.md)

**Since:** 9

<!--Device-SystemEvent-eventType: EventType--><!--Device-SystemEvent-eventType: EventType-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## params

```TypeScript
params: string
```

Identifies the customized extended parameter of an event.

**Type:** string

**Since:** 9

<!--Device-SystemEvent-params: string--><!--Device-SystemEvent-params: string-End-->

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.
