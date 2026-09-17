# stopSecurityEventCollector (System API)

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## stopSecurityEventCollector

```TypeScript
function stopSecurityEventCollector(rule: CollectorRule): void
```

stop the collector.

**Since:** 12

**Required permissions:** ohos.permission.QUERY_SECURITY_EVENT

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rule | [CollectorRule](arkts-securityguard-securityguard-collectorrule-i-sys.md) | Yes | rule of collect security event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | check permission fail. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | non-system application uses the system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
