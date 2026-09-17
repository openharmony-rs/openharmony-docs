# getDnsAscii

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDnsAscii

```TypeScript
function getDnsAscii(host: string, flag?: ConversionProcess): string
```

Converts the host name from Unicode to ASCII and controls the conversion behavior through the optional conversion process parameter (**conversionProcess**).

> **NOTE:** 
> 
> If **conversionProcess** is set to **NO_CONFIGURATION**, only the domain names corresponding to the Unicode
> characters that have been officially allocated can be converted.

> When **conversionProcess** is set to **ALLOW_UNASSIGNED**, domain names that contain Unicode characters that have
> not been assigned meanings can be converted.

> If **conversionProcess** is set to **USE_STD3_ASCII_RULES**, the generated ASCII domain name is forcibly checked
> based on the STD-3 ASCII rule (RFC 1123 standard) during the conversion.

> Digits and English letters in the input parameters are not transcoded.

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to be converted. The length of each label (separated by dots) cannot exceed 63 bytes. |
| flag | [ConversionProcess](arkts-network-connection-conversionprocess-e.md) | No | Conversion flow parameter. The default value is **NO_CONFIGURATION**. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Conversion result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { connection } from '@kit.NetworkKit';

let result = connection.getDnsAscii("www.example.com," connection.ConversionProcess.NO_CONFIGURATION);
console.info(result);  // Expected result: www.xn--fsq092h.com
let result = connection.getDnsAscii("www.example.com", connection.ConversionProcess.NO_CONFIGURATION);
console.info(result);  // Expected result: www.example.com
```
