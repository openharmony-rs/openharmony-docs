# cleanSandboxAppConfig

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## cleanSandboxAppConfig

```TypeScript
function cleanSandboxAppConfig(): Promise<void>
```

Clears the sandbox application configuration. After the API is successfully called, the sandbox application configuration is cleared and the default state is restored. This API uses a promise to return the result.

This API clears the sandbox application configuration and restores the default state to prevent residual configurations from affecting subsequent use. This API can be called only in non-sandbox applications.

**Since:** 11

**System capability:** SystemCapability.Security.DataLossPrevention

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported because car not support DLP feature.<br>**Applicable version:** 26.1.0 and later |
| [19100001](../errorcode-dlp.md#19100001-invalid-parameter) | Invalid parameter value. |
| [19100007](../errorcode-dlp.md#19100007-access-denied-for-a-dlp-sandbox-application) | No permission to call this API, which is available only for non-DLP sandbox applications. |
| [19100011](../errorcode-dlp.md#19100011-system-service-abnormal) | The system ability works abnormally. |
| [19100018](../errorcode-dlp.md#19100018-application-unauthorized) | The application is not authorized. |

**Examples**

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';

dlpPermission.cleanSandboxAppConfig().then(() => { // Clear sandbox application configuration.
  console.info('cleanSandboxAppConfig success');
}).catch((error: BusinessError)=> {
  console.error(JSON.stringify(error));
});
```
