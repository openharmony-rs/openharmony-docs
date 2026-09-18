# apiAvailable

## Modules to Import

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';
```

## apiAvailable

```TypeScript
function apiAvailable(version: string | number): boolean
```

Checks whether a specified API version is available on the current device. This API provides compatibility check for OpenHarmony and its distribution OS API versions. A suitable version check method is automatically selected based on the input format and supported API versions.

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Startup.SystemInfo

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| version | string &#124; number | Yes | API version to be verified. Supports both integer and string formats.   - The string uses the M.S.F format (for example, "26.0.0" and "5.0.1"): for API 26.0.0 and   later (version &gt;= 26.0.0), it represents the OpenHarmony and distribution OS API version.   - For API earlier than 26.0.0 (version &lt; 26.0.0), it represents the distribution OS API version.   - The integer format (for example, 13) represents the OpenHarmony SDK API version. (Only API earlier   than 26 is supported.) M&gt;=26,0&lt;=S&lt;=99,0&lt;=F&lt;=99. A compilation error occurs when an invalid literal is passed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value. If **true** is returned, the API version of the device is the version specified in the input parameter or a later version. If **false** is returned, the API version is earlier than the version specified in the input parameter, the version format is invalid, or the version does not exist. |

**Examples**

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';

// For OpenHarmony base and distribution APIs of API version 26.0.0 or later
if (deviceInfo.apiAvailable("26.0.0")) {
   // Method that requires version isolation
}


// For distribution OS-specific APIs, that is, APIs marked with since M.S.F(N)
if (deviceInfo.apiAvailable("5.0.1")) {
   // Method that requires version isolation
}


// For OpenHarmony base public APIs, that is, APIs marked with since N
if (deviceInfo.apiAvailable(13)) {
   // Method that requires version isolation
}
```
