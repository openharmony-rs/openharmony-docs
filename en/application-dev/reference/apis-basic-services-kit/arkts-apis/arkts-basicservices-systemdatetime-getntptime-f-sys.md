# getNtpTime (System API)

## Modules to Import

```TypeScript
import { systemDateTime } from '@kit.BasicServicesKit';
```

## getNtpTime

```TypeScript
function getNtpTime(): number
```

Obtains the actual time calculated based on the last updated NTP time. This API returns the result synchronously.

**Since:** 14

**System capability:** SystemCapability.MiscServices.Time

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Unix epoch time (ms) calculated based on the last updated NTP time. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [13000002](../errorcode-time.md#13000002-ntp-time-not-updated) | updateNtpTime() is not called successfully. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let time: number = systemDateTime.getNtpTime();
} catch(e) {
  let error = e as BusinessError;
  console.error(`Failed to get ntp time. message: ${error.message}, code: ${error.code}`);
}
```
