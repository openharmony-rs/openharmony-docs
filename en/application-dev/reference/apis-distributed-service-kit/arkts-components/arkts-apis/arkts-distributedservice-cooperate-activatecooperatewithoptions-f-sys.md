# activateCooperateWithOptions (System API)

## Modules to Import

```TypeScript
import { cooperate } from '@kit.DistributedServiceKit';
```

## activateCooperateWithOptions

```TypeScript
function activateCooperateWithOptions(targetNetworkId: string, inputDeviceId: number,
    cooperateOptions?: CooperateOptions
  ): Promise<void>
```

Starts screen hopping based on the specified options. This API uses a promise to return the result.

**Since:** 20

**Required permissions:** ohos.permission.COOPERATE_MANAGER

**System capability:** SystemCapability.Msdp.DeviceStatus.Cooperate

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetNetworkId | string | Yes | Descriptor of the target device for screen hopping. |
| inputDeviceId | number | Yes | ID of the input device that initiates screen hopping. |
| cooperateOptions | [CooperateOptions](arkts-distributedservice-cooperate-cooperateoptions-i-sys.md) | No | Screen hopping options, such as the exit position. If this parameter is not set, this API works in the same way as [activateCooperate](arkts-distributedservice-cooperate-activatecooperate-f-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [20900001](../errorcode-devicestatus.md#20900001-input-device-operation-failed) | Service exception. Possible causes:<br>1. A system error, such as null pointer, container-related exception, or IPC exception. <br>2. N-API invocation exception or invalid N-API status. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let targetNetworkId = "networkId";
let inputDeviceId = 0;
try {
  cooperate.activateCooperateWithOptions(targetNetworkId, inputDeviceId).then(() => {
    console.info(`activateCooperateWithOptions success.`);
  }, (error: BusinessError) => {
    console.error(`activateCooperateWithOptions, error: ${JSON.stringify(error, [`code`, `message`])}`);
  });
} catch (error) {
  console.error(`activateCooperateWithOptions, error: ${JSON.stringify(error, [`code`, `message`])}`);
}
```
