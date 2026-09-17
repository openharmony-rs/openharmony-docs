# off (System API)

## Modules to Import

```TypeScript
import { securityGuard } from '@kit.SecurityGuardKit';
```

## off('securityEventOccur')

```TypeScript
function off(type: 'securityEventOccur', securityEventInfo: SecurityEventInfo, callback?: Callback<SecurityEvent>): void
```

Unsubscribe the security event.

**Since:** 12

**Required permissions:** ohos.permission.QUERY_SECURITY_EVENT

**System capability:** SystemCapability.Security.SecurityGuard

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'securityEventOccur' | Yes |  |
| securityEventInfo | [SecurityEventInfo](arkts-securityguard-securityguard-securityeventinfo-i-sys.md) | Yes | Indicates the subscribed event information. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SecurityEvent](arkts-securityguard-securityguard-securityevent-i-sys.md)&gt; | No | Indicates the listener when the security event occurs. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | check permission fail. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | non-system application uses the system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3. Parameter verification failed. |
