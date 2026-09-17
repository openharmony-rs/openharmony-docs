# sppCloseClientSocket

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppCloseClientSocket

```TypeScript
function sppCloseClientSocket(socket: number): void
```

Disables an spp client socket and releases related resources.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sppCloseClientSocket](arkts-connectivity-bluetoothmanager-sppcloseclientsocket-f.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socket | number | Yes | Indicates the client socket ID, returned by [sppAccept](arkts-connectivity-bluetooth-sppaccept-f.md) or [sppConnect](arkts-connectivity-bluetooth-sppconnect-f.md). |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let clientNumber = -1;
function clientSocket(code : BusinessError, number : number) {
  if (code == null || code.code != 0) {
    return;
  }
  console.info(`bluetooth serverSocket Number: ${number}`);
  // The obtained clientNumber is used as the socket ID for subsequent read/write operations on the client.
  clientNumber = number;
}
bluetooth.sppCloseClientSocket(clientNumber);
```
