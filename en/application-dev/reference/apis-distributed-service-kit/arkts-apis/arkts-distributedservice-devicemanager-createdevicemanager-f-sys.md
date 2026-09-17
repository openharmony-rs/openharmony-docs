# createDeviceManager (System API)

## Modules to Import

```TypeScript
import { deviceManager } from '@kit.DistributedServiceKit';
```

## createDeviceManager

```TypeScript
function createDeviceManager(bundleName: string, callback: AsyncCallback<DeviceManager>): void
```

Creates a **DeviceManager** instance.

**Since:** 7

**Deprecated since:** 11

**Substitutes:** [createDeviceManager](arkts-distributedservice-distributeddevicemanager-createdevicemanager-f.md)

**System capability:** SystemCapability.DistributedHardware.DeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. The value is a string of 1 to 255 characters. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[DeviceManager](arkts-distributedservice-distributeddevicemanager-devicemanager-i.md)&gt; | Yes | Callback used to return the **DeviceManager** instance created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';
import { BusinessError } from '@ohos.base';

let dmInstance: deviceManager.DeviceManager | null = null;
try {
  deviceManager.createDeviceManager("ohos.samples.jshelloworld", (err: BusinessError, data: deviceManager.DeviceManager) => {
    if (err) { 
      console.error("createDeviceManager errCode:" + err.code + ",errMessage:" + err.message);
      return;
    }
    console.info("createDeviceManager success");
    dmInstance = data;
  });
} catch(err) {
  let e: BusinessError = err as BusinessError;
  console.error("createDeviceManager errCode:" + e.code + ",errMessage:" + e.message);
}
```
