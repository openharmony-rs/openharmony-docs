# getMaxTransmitDataSize

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## getMaxTransmitDataSize

```TypeScript
function getMaxTransmitDataSize(clientSocket: number): number
```

Obtain the maximum data size that can be transmitted through this socket channel.

**Since:** 22

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clientSocket | number | Yes | Indicates the client socket ID, returned by [sppAccept](arkts-connectivity-socket-sppaccept-f.md) or [sppConnect](arkts-connectivity-socket-sppconnect-f.md). |

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum transmitted data size |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// clientNumber is obtained via sppAccept or sppConnect.
let clientSocket = 1; 
try {
    let result: number = socket.getMaxTransmitDataSize(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
