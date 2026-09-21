# on

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## on('sppRead')

```TypeScript
function on(type: 'sppRead', clientSocket: number, callback: Callback<ArrayBuffer>): void
```

Subscribe the event reported when data is read from the socket.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sppRead' | Yes | Type of the spp read event to listen for. |
| clientSocket | number | Yes | Client socket ID, which is obtained by sppAccept or sppConnect. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to listen for the spp read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| 2901054 | IO error. |
| 2900099 | Operation failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = 1; // clientNumber is obtained by sppAccept or sppConnect.
let dataRead = (dataBuffer: ArrayBuffer) => {
    let data = new Uint8Array(dataBuffer);
    console.info('bluetooth data length is: ' + data.byteLength);
}
try {
    socket.on('sppRead', clientNumber, dataRead);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
