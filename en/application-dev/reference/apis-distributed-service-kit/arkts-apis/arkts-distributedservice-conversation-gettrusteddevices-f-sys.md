# getTrustedDevices (System API)

## Modules to Import

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
```

## getTrustedDevices

```TypeScript
function getTrustedDevices(): DeviceNodeInfo[]
```

Obtains the list of historical trusted devices. Typical use scenarios include querying available target devices before sending data across devices.

**Since:** 26.1.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC and ohos.permission.sec.ACCESS_UDID

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [DeviceNodeInfo](arkts-distributedservice-conversation-devicenodeinfo-i-sys.md)[] | Device node information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. The application does not have the required permission to access distributed data. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. |

**Examples**

```TypeScript
import { conversation } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let devices: conversation.DeviceNodeInfo[] = conversation.getTrustedDevices();
  console.info(`getTrustedDevices success, count: ${devices.length}`);
  for (let device of devices) {
    console.info(`device name: ${device.deviceName}, networkId: ${device.networkId}`);
  }
} catch (err) {
  const e: BusinessError = err as BusinessError;
  console.error(`getTrustedDevices errCode: ${e.code}, errMessage: ${e.message}`);
}
```
