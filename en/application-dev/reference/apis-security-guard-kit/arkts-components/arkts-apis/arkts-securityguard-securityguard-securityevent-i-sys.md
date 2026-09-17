# SecurityEvent (System API)

Provides the SecurityEvent type, including the event id, version info, report content.

@typedef SecurityEvent

**Since:** 12

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

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## eventId

```TypeScript
eventId: number
```

The event id

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## timestamp

```TypeScript
timestamp?: string
```

The event timestamp, format is YYYYMMDDHHMMSS.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## version

```TypeScript
version: string
```

The version of a security event. Different versions indicate different data formats.

**Type:** string

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.
