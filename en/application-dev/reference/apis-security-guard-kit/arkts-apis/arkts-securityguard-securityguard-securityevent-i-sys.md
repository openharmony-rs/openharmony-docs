# SecurityEvent (System API)

```TypeScript
interface SecurityEvent
```

Provides the SecurityEvent type, including the event id, version info, report content.

@typedef SecurityEvent

**Since:** 12

<!--Device-securityGuard-interface SecurityEvent--><!--Device-securityGuard-interface SecurityEvent-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## content

```TypeScript
content: string
```

The report content

**Type:** string

**Since:** 12

<!--Device-SecurityEvent-content: string--><!--Device-SecurityEvent-content: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## eventId

```TypeScript
eventId: number
```

The event id

**Type:** number

**Since:** 12

<!--Device-SecurityEvent-eventId: number--><!--Device-SecurityEvent-eventId: number-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp?: string
```

The event timestamp, format is YYYYMMDDHHMMSS.

**Type:** string

**Since:** 12

<!--Device-SecurityEvent-timestamp?: string--><!--Device-SecurityEvent-timestamp?: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## version

```TypeScript
version: string
```

The version of a security event. Different versions indicate different data formats.

**Type:** string

**Since:** 12

<!--Device-SecurityEvent-version: string--><!--Device-SecurityEvent-version: string-End-->

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
