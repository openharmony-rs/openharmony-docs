# off

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## off('sppRead')

```TypeScript
function off(type: 'sppRead', clientSocket: number, callback?: Callback<ArrayBuffer>): void
```

Unsubscribe the event reported when data is read from the socket.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'sppRead' | Yes | Type of the spp read event to listen for. |
| clientSocket | number | Yes | Client socket ID, which is obtained by sppAccept or sppConnect. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | No | Callback used to listen for the spp read event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameter. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let clientNumber = 1; // clientNumber is obtained by sppAccept or sppConnect.
try {
    socket.off('sppRead', clientNumber);
} catch (err) {
    console.error('errCode: ' + (err as BusinessError).code + ', errMessage: ' + (err as BusinessError).message);
}
```
