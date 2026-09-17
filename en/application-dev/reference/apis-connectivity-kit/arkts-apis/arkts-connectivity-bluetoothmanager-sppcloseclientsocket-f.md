# sppCloseClientSocket

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## sppCloseClientSocket

```TypeScript
function sppCloseClientSocket(socket: number): void
```

Disables an spp client socket and releases related resources.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [sppCloseClientSocket](arkts-connectivity-socket-sppcloseclientsocket-f.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socket | number | Yes | Indicates the client socket ID, returned by [sppAccept](arkts-connectivity-bluetoothmanager-sppaccept-f.md) or [sppConnect](arkts-connectivity-bluetoothmanager-sppconnect-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2900001 | Service stopped. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let clientNumber = -1;
function clientSocket(code: BusinessError, number: number) {
  if (code == null || code.code != 0) {
    return;
  }
  console.info(`bluetooth serverSocket Number: ${number}`);
  // The obtained clientNumber is used as the socket ID for subsequent read/write operations on the client.
  clientNumber = number;
}
try {
    bluetoothManager.sppCloseClientSocket(clientNumber);
} catch (err) {
    console.error(`errCode: ${err.code}, errMessage: ${err.message}`);
}
```
