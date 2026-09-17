# sppListen

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## sppListen

```TypeScript
function sppListen(name: string, option: SppOption, callback: AsyncCallback<number>): void
```

Creates a Bluetooth server listening socket.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [sppListen](arkts-connectivity-bluetoothmanager-spplisten-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates the service name. |
| option | [SppOption](arkts-connectivity-bluetooth-sppoption-i.md) | Yes | Indicates the listen parameters [SppOption](arkts-connectivity-bluetooth-sppoption-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return a server socket ID. |

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

let sppOption : bluetooth.SppOption = {uuid: '00001810-0000-1000-8000-00805F9B34FB', secure: false, type: 0};
bluetooth.sppListen('server1', sppOption, serverSocket);
```
