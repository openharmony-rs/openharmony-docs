# Querier (System API)

Definition callback of receiving the query data.

@interface Querier

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## onComplete

```TypeScript
onComplete: () => void
```

Triggered when data is complete.

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

## onError

```TypeScript
onError: (message: string) => void
```

Triggered when error.

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| message | string | Yes |  |

## onQuery

```TypeScript
onQuery: (events: Array<SecurityEvent>) => void
```

Triggered when data is returned.

**Since:** 12

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| events | Array&lt;[SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md)&gt; | Yes |  |
