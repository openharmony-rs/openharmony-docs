# registerMissionListener (System API)

## Modules to Import

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## registerMissionListener

```TypeScript
function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback<void>): void
```

Registers a mission status listener. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | Yes | Information about the device to listen for. |
| options | [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | Yes | Callback to register. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the listener is registered, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Implement a callback function.
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
}
function NotifySnapshot(deviceId: string, missionId: number): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: number): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}
try {
  // Call registerMissionListener.
  distributedMissionManager.registerMissionListener(
    { deviceId: "" },
    {
      notifyMissionsChanged: NotifyMissionsChanged,
      notifySnapshot: NotifySnapshot,
      notifyNetDisconnect: NotifyNetDisconnect
    },
    (error: BusinessError) => {
      if (error) {
        console.error(`Failed to register mission listener. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info('registerMissionListener finished');
    });
   } catch (error) {
  console.error(`Failed to register mission listener. Code: ${error.code}, message: ${error.message}`);
}
```


<a id="registermissionlistener-1"></a>

## registerMissionListener

```TypeScript
function registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback): Promise<void>
```

Registers a mission status listener. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [MissionDeviceInfo](arkts-ability-distributedmissionmanager-missiondeviceinfo-t-sys.md) | Yes | Information about the device to listen for. |
| options | [MissionCallback](arkts-ability-distributedmissionmanager-missioncallback-t-sys.md) | Yes | Callback to register. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Implement a callback function.
function NotifyMissionsChanged(deviceId: string): void {
  console.info('NotifyMissionsChanged deviceId ' + JSON.stringify(deviceId));
 }
function NotifySnapshot(deviceId: string, missionId: number): void {
  console.info('NotifySnapshot deviceId ' + JSON.stringify(deviceId));
  console.info('NotifySnapshot missionId ' + JSON.stringify(missionId));
}
function NotifyNetDisconnect(deviceId: string, state: number): void {
  console.info('NotifyNetDisconnect deviceId ' + JSON.stringify(deviceId));
  console.info('NotifyNetDisconnect state ' + JSON.stringify(state));
}
try {
    // Call registerMissionListener.
    distributedMissionManager.registerMissionListener(
      { deviceId: "" },
      {
        notifyMissionsChanged: NotifyMissionsChanged,
        notifySnapshot: NotifySnapshot,
        notifyNetDisconnect: NotifyNetDisconnect
      }).then(() => {
        console.info('registerMissionListener finished. ');
    }).catch((error: BusinessError) => {
        console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
    })
} catch (error) {
    console.error('registerMissionListener failed, cause: ' + JSON.stringify(error));
}
```
