# resumeDistributedHardware (System API)

## Modules to Import

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
```

## resumeDistributedHardware

```TypeScript
function resumeDistributedHardware(description: HardwareDescriptor): Promise<void>
```

Resumes the distributed hardware service on the controlled device. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.ACCESS_DISTRIBUTED_HARDWARE

**System capability:** SystemCapability.DistributedHardware.DistributedHardwareFWK

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| description | [HardwareDescriptor](arkts-distributedservice-hardwaremanager-hardwaredescriptor-i-sys.md) | Yes | Hardware information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Input parameter error. |
| 24200101 | The specified distributed hardware is not started. |
| 24200102 | The specified source device is not connected. |

**Examples**

```TypeScript
import { hardwareManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let description: hardwareManager.HardwareDescriptor = {
    type: 1,
    srcNetworkId: '1111'
  };
  hardwareManager.resumeDistributedHardware(description).then(() => {
    console.info('resume distributed hardware successfully');
  }).catch((error: BusinessError) => {
    console.error('resume distributed hardware failed, cause:' + error);
  })
  console.info('resume distributed hardware successfully');
} catch (error) {
  console.error('resume distributed hardware failed:' + error);
}
```
