# getDnsUnicode

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## getDnsUnicode

```TypeScript
function getDnsUnicode(host: string, flag?: ConversionProcess): string
```

Converts host names from ASCII to Unicode using the Punycode encoding mode and uses the optional conversionProcess parameter to control the conversion behavior.

**Since:** 23

**System capability:** SystemCapability.Communication.NetManager.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| host | string | Yes | Host name to be converted. |
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

let result = connection.getDnsUnicode("www.xn--fsq092h.com", connection.ConversionProcess.NO_CONFIGURATION);
console.info(result);  // Expected result: www.example.com
let result = connection.getDnsUnicode("www.example.com", connection.ConversionProcess.NO_CONFIGURATION);
console.info(result);  // Expected result: www.example.com
```
