# isConnected

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## isConnected

```TypeScript
function isConnected(clientSocket: number): boolean
```

Check whether the current socket connection has been established.

**Since:** 22

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| clientSocket | number | Yes | Indicates client socket. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Indicates whether or not it is connected. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// clientNumber is obtained via sppAccept or sppConnect.
let clientSocket = 1; 
try {
    let result: boolean = socket.isConnected(clientSocket);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
