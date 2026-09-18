# getAVScreenCaptureConfigurableParameters (System API)

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## getAVScreenCaptureConfigurableParameters

```TypeScript
function getAVScreenCaptureConfigurableParameters(sessionId: number): Promise<string>
```

get Configurations which user can changes from AVScreenCapture server

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sessionId | number | Yes | The AVScreenCapture server session ID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns a configurable configuration item string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [5400109](../errorcode-media.md#5400109-session-id-does-not-exist) | Sessions not exist. Return by promise. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) |  |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { media } from '@kit.MediaKit';

let sessionId: number = 0; // Use the ID of the session that starts the process.

try {
  let privacyResult: string = await media.getAVScreenCaptureConfigurableParameters(sessionId);
} catch (error: BusinessError) {
  console.error(`getAVScreenCaptureConfigurableParameters error, error message: ${error.message}`);
}
```
