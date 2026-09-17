# sppAccept

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppAccept

```TypeScript
function sppAccept(serverSocket: number, callback: AsyncCallback<number>): void
```

Waits for a remote device to connect.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sppAccept](arkts-connectivity-bluetoothmanager-sppaccept-f.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serverSocket | number | Yes | Indicates the server socket ID, returned by [sppListen](arkts-connectivity-bluetooth-spplisten-f.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return a client socket ID. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
let serverNumber = -1;
function serverSocket(code : BusinessError, number : number) {
  console.info(`bluetooth error code: ${code.code}`);
  if (code.code == 0) {
    console.info(`bluetooth serverSocket Number: ${number}`);
    serverNumber = number;
  }
}
let clientNumber = -1;
function acceptClientSocket(code : BusinessError, number : number) {
  console.info(`bluetooth error code: ${code.code}`);
  if (code.code == 0) {
    console.info(`bluetooth clientSocket Number: ${number}`);
    // The obtained clientNumber is used as the socket ID for subsequent read/write operations on the server.
    clientNumber = number;
  }
}
bluetooth.sppAccept(serverNumber, acceptClientSocket);
```
