# apiAvailable

## Modules to Import

```TypeScript
import { deviceInfo } from '@kit.BasicServicesKit';
```

## apiAvailable

```TypeScript
function apiAvailable(version: string | number): boolean
```

Checks whether a specified API version is available on the current device. This API provides compatibility check across different OpenHarmony/Distribution OS versions. A suitable version check method is automatically selected based on the input format and supported API versions.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-deviceInfo-function apiAvailable(version: string | number): boolean--><!--Device-deviceInfo-function apiAvailable(version: string | number): boolean-End-->

**System capability:** SystemCapability.Startup.SystemInfo

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| version | string &#124; number | Yes | API version to be verified. Supports both integer and string formats. <br> The string uses the M.S.F format (for example, "26.0.0" and "5.0.1"), where 0&lt;=S&lt;=99 and 0&lt;=F&lt;=99: <br>&emsp;&emsp;For API 26.0.0 and later (version &gt;= 26.0.0), it represents the OpenHarmony and distribution OS API version. <br>&emsp;&emsp;For API earlier than 26.0.0 (version &lt; 26.0.0), it represents the distribution OS API version. <br> The integer format (for example, 13): <br>&emsp;&emsp;Represents the OpenHarmony SDK API version. (Only API earlier than 26 is supported.) |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Boolean value. The value **true** indicates that the current version number is later than or equal to the input parameter version number; **false** indicates that the current device's API version is lower than the input version number, or the input version number is in an invalid format, or the specified version does not exist. |

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
