# @ohos.distributedMissionManager (Distributed Mission Management) (System API)
<!--Kit: Ability Kit-->
<!--Subsystem: DistributedAbilityManager-->
<!--Owner: @hobbycao-->
<!--Designer: @gsxiaowen-->
<!--Tester: @hanjiawei-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=1e357e1a9db0c5699e6a05a0f31a4e4d2907a0a5 translatedAt=2026-09-03T11:25:19.298Z pushedAt=2026-09-05T10:47:30.651Z -->

The distributedMissionManager module implements mission management across devices. You can use the APIs provided by this module to register or unregister a mission status listener, start or stop synchronizing a remote mission list, and continue a mission on a remote device by mission ID or bundle name.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> The APIs of this module are system APIs.
>
> The APIs of this module can be used only in the stage model.

## Modules to Import

```js
import { distributedMissionManager } from '@kit.AbilityKit';
```

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

## distributedMissionManager.registerMissionListener

registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback, callback: AsyncCallback&lt;void&gt;): void;

Registers a mission state listener. This API uses an asynchronous callback to return the result. After the call succeeds, the system starts listening for mission state changes on the specified device. This listener must be used in pair with `unRegisterMissionListener`. After registration, call `unRegisterMissionListener` in a timely manner to unregister listening when mission state listening is no longer needed, so as to release resources.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description       |
| --------- | --------------------------------------- | ---- | --------- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10) | Yes    | Device information used for register listening. The deviceId is the device identifier. |
| options   | [MissionCallback](#missioncallback10)     | Yes    | Callback function registered. |
| callback  | AsyncCallback&lt;void&gt;               | Yes    | Callback function invoked when register listening is complete. The err is undefined if the operation succeeds; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
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
## distributedMissionManager.registerMissionListener

registerMissionListener(parameter: MissionDeviceInfo, options: MissionCallback): Promise&lt;void&gt;

Registers a mission state listener. This API uses a promise to return the result. After the call succeeds, the system starts listening for mission state changes on the specified device. This listener must be used in pair with `unRegisterMissionListener`. After registration, call `unRegisterMissionListener` in a timely manner to unregister listening when mission state listening is no longer needed, so as to release resources.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10)  | Yes    | Device information used for register listening. The deviceId is the device identifier.   |
| options   | [MissionCallback](#missioncallback10) | Yes    | Callback function registered.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise object returned. When the operation succeeds, it indicates that the task state listener has been successfully registered; when it fails, an error message is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
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

## distributedMissionManager.unRegisterMissionListener

unRegisterMissionListener(parameter: MissionDeviceInfo, callback: AsyncCallback&lt;void&gt;): void;

Unregisters a mission state listener. This API uses an asynchronous callback to return the result. Before stopping listening, ensure that registration has been completed through registerMissionListener; otherwise, the call is invalid. After the call succeeds, the system no longer listens for mission state changes on the device.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description       |
| --------- | --------------------------------------- | ---- | --------- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10) | Yes | Device information specified when unregistering listening. The deviceId field is the device identifier. |
| callback  | AsyncCallback&lt;void&gt;               | Yes | Callback for the unregister listening event. The err parameter is undefined when unregistering succeeds, and is an error object otherwise. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    // Unregister task state listening.
    distributedMissionManager.unRegisterMissionListener(
      { deviceId: "" },
      (error: BusinessError) => {
        if (error) {
            console.error(`unRegisterMissionListener failed. Code: ${error.code}, message: ${error.message}`);
            return;
        }
        console.info('unRegisterMissionListener finished');
    })
  } catch (error) {
      console.error('unRegisterMissionListener failed, cause: ' + JSON.stringify(error));
  }
  ```

## distributedMissionManager.unRegisterMissionListener

unRegisterMissionListener(parameter: MissionDeviceInfo): Promise&lt;void&gt;

Unregisters a mission state listener. This API uses a promise to return the result. Before stopping listening, ensure that registration has been completed through registerMissionListener; otherwise, the call is invalid. After the call succeeds, the system no longer listens for mission state changes on the device.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10) | Yes | Device information used when unregistering listening. The deviceId is the device identifier. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; |Promise object. It indicates that the task state listening has been successfully unregistered when the operation succeeds, and returns an error message when the operation fails.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    distributedMissionManager.unRegisterMissionListener({deviceId: ""}).then(() => {
      console.info('unRegisterMissionListener finished successfully');
    }).catch((error: BusinessError) => {
        console.error(`unRegisterMissionListener failed. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
      console.error('unRegisterMissionListener failed, cause: ' + JSON.stringify(error));
  }
  ```

## distributedMissionManager.startSyncRemoteMissions

startSyncRemoteMissions(parameter: MissionParameter, callback: AsyncCallback&lt;void&gt;): void;

Starts to synchronize the mission list of a remote device. This API uses an asynchronous callback to return the result. It must be used in strict pairing with stopSyncRemoteMissions, following the "start first, then stop" order. After synchronization is complete, stop it immediately to release system resources.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                   | Mandatory  | Description       |
| --------- | ------------------------------------- | ---- | --------- |
| parameter | [MissionParameter](#missionparameter10) | Yes | Synchronization information, including the deviceId, fixConflict, and tag fields. tag is the synchronization identifier used to distinguish different synchronization sessions, and its value must meet the scenario requirements. fixConflict indicates whether to resolve conflicts. It is recommended to set it to true in scenarios where mission conflicts may occur to avoid mission conflict issues. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback function. When the remote mission list is synchronized, err is undefined; otherwise, an error object is returned. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    // Start synchronization of the mission list of the remote device.
    distributedMissionManager.startSyncRemoteMissions(
      {
        deviceId: "",
        fixConflict: false,
        tag: 0
      },
      (error: BusinessError) => {
        if (error) {
          console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
          return;
        }
        console.info('startSyncRemoteMissions finished');}
    )
  } catch (error) {
    console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.startSyncRemoteMissions

startSyncRemoteMissions(parameter: MissionParameter): Promise&lt;void&gt;

Starts to synchronize the mission list of a remote device. This API uses a promise to return the result. It must be used in strict pairing with stopSyncRemoteMissions, following the "start first, then stop" order. After synchronization is complete, stop it immediately to release system resources.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                   | Mandatory  | Description   |
| --------- | ------------------------------------- | ---- | ----- |
| parameter | [MissionParameter](#missionparameter10) | Yes    | Synchronization information, including the deviceId, fixConflict, and tag fields. tag is the synchronization identifier used to distinguish different synchronization sessions, and its value must meet the scenario requirements. fixConflict indicates whether to resolve conflicts. It is recommended to set it to true in scenarios where mission conflicts may occur to avoid mission conflict issues.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Returned Promise object. On operation success, it indicates that the remote device mission list synchronization has been started successfully. On failure, it returns the error message.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    distributedMissionManager.startSyncRemoteMissions(
      {
        deviceId: "",
        fixConflict: false,
        tag: 0
      }
    ).then(() => {
        console.info('startSyncRemoteMissions finished successfully');
      }).catch((error: BusinessError) => {
      console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
    console.error(`startSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.stopSyncRemoteMissions

stopSyncRemoteMissions(parameter: MissionDeviceInfo, callback: AsyncCallback&lt;void&gt;): void;

Stops synchronizing the mission list of a remote device. This API uses an asynchronous callback to return the result. After the call succeeds, the system stops synchronizing the mission list of the specified remote device. You must call startSyncRemoteMissions to start synchronization before calling this API. Calling this API without starting synchronization does not take effect.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description       |
| --------- | --------------------------------------- | ---- | --------- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10) | Yes | Device information for stopping synchronization. The deviceId is the ID of the remote device whose synchronization is to be stopped. |
| callback | AsyncCallback&lt;void&gt; | Yes | Callback invoked when the synchronization of the remote mission list is stopped. The err is undefined if the operation succeeds; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    // Stop synchronization of the mission list of the remote device.
    distributedMissionManager.stopSyncRemoteMissions(
      {
        deviceId: ""
      },
      (error: BusinessError) => {
        if (error) {
          console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
          return;
        }
        console.info('stopSyncRemoteMissions finished');}
    )
  } catch (error) {
    console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.stopSyncRemoteMissions

stopSyncRemoteMissions(parameter: MissionDeviceInfo): Promise&lt;void&gt;

Stops synchronizing the mission list of a remote device. This API uses a promise to return the result. After the call succeeds, the system stops synchronizing the mission list of the specified remote device. You must call startSyncRemoteMissions to start synchronization before calling this API. Calling this API without starting synchronization does not take effect.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [MissionDeviceInfo](#missiondeviceinfo10) | Yes    | Device information for stopping synchronization. deviceId is the ID of the remote device whose synchronization is to be stopped. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | The returned Promise object, which indicates that the remote device mission list synchronization has been successfully stopped when the operation succeeds, and returns an error message on failure.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    distributedMissionManager.stopSyncRemoteMissions(
      {
        deviceId: ""
      }).then(() => {
        console.info('stopSyncRemoteMissions finished successfully');
      }).catch((error: BusinessError) => {
      console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
    console.error(`stopSyncRemoteMissions failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.continueMission

continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback&lt;void&gt;): void;

Continues a mission on a remote device, with the mission ID specified. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [ContinueDeviceInfo](js-apis-inner-application-continueDeviceInfo-sys.md) | Yes    | Migration information for continuing a mission by mission ID, including the source device ID, target device ID, and mission ID. |
| options | [ContinueCallback](js-apis-inner-application-continueCallback-sys.md) | Yes    | Callback invoked when the mission is continued by mission ID, used to receive the continuation result. |
| callback | AsyncCallback&lt;void&gt; | Yes    | Callback function. When the mission is continued, **err** is **undefined** if the operation succeeds; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Distributed Scheduler Error Codes](./errorcode-DistributedSchedule.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 201      | Permission denied.|
| 202 | The application is not system-app, can not use system-api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300501 | The system ability work abnormally. |
| 16300502 | Failed to get the missionInfo of the specified missionId. |
| 16300503 | The application is not installed on the remote end and installation-free is not supported. |
| 16300504 | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| 16300505 | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| 16300506 | The local continuation task is already in progress. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // Implement a callback function.
  function onContinueDone(resultCode: number): void {
    console.info('onContinueDone resultCode: ' + JSON.stringify(resultCode));
  };
  try {
    // Migrate the mission by mission ID.
    // Obtain the actual mission ID through the system API.
    distributedMissionManager.continueMission(
      {
        srcDeviceId: '',
        dstDeviceId: '',
        missionId: 1,
        wantParam: {'key': 'value'}
      },
      { onContinueDone: onContinueDone },
      (error: BusinessError) => {
        if (error) {
          console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
          return;
        }
        console.info('continueMission finished');
    })
  } catch (error) {
    console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.continueMission

continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise&lt;void&gt;

Continues a mission from the source device to the target device by specifying the mission ID. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [ContinueDeviceInfo](js-apis-inner-application-continueDeviceInfo-sys.md) | Yes    | Migration information, including the source device ID, target device ID, mission ID, and custom parameters. |
| options | [ContinueCallback](js-apis-inner-application-continueCallback-sys.md) | Yes   | Callback invoked when the mission continuation is complete.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; |Promise object returned. It indicates that the mission migration by mission ID is complete when the operation succeeds, and returns an error message when the operation fails.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Distributed Scheduler Error Codes](./errorcode-DistributedSchedule.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 201      | Permission denied.|
| 202 | The application is not system-app, can not use system-api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300501 | The system ability work abnormally. |
| 16300502 | Failed to get the missionInfo of the specified missionId. |
| 16300503 | The application is not installed on the remote end and installation-free is not supported. |
| 16300504 | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| 16300505 | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| 16300506 | The local continuation task is already in progress. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  // Implement a callback function.
  function onContinueDone(resultCode: number): void {
    console.info('onContinueDone resultCode: ' + JSON.stringify(resultCode));
  };
  try {
    // Continue the mission by mission ID.
    // Obtain the actual mission ID through the system API for missionId.
    distributedMissionManager.continueMission(
      {
        srcDeviceId: '',
        dstDeviceId: '',
        missionId: 1,
        wantParam: {'key': 'value'}
      },
      { onContinueDone: onContinueDone }).then(() => {
        console.info('continueMission finished successfully');
      }).catch((error: BusinessError) => {
      console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
    });
  } catch (error) {
    console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.continueMission<sup>10+</sup>

continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback&lt;void&gt;): void;

Continues the mission of a specified application from the source device to the target device by specifying the bundle name. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [ContinueMissionInfo](./js-apis-inner-application-continueMissionInfo-sys.md) | Yes    | Migration information, including the source device ID, target device ID, application bundle name, and custom parameters.|
| callback | AsyncCallback&lt;void&gt; | Yes   | Callback used to return the result. If the mission is continued, **err** is **undefined**; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Distributed Scheduler Error Codes](./errorcode-DistributedSchedule.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 201      | Permission denied.|
| 202 | The application is not system-app, can not use system-api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300501 | The system ability work abnormally. |
| 16300503 | The application is not installed on the remote end and installation-free is not supported. |
| 16300504 | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| 16300505 | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| 16300506 | The local continuation task is already in progress. |
| 16300507 | Failed to get the missionInfo of the specified bundle name. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
    distributedMissionManager.continueMission(
      {
        srcDeviceId: '',
        dstDeviceId: '',
        bundleName: 'ohos.test.continueapp',
        wantParam: {'key': 'value'}
      },
      (error: BusinessError) => {
        if (error) {
          console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
          return;
        }
        console.info('continueMission finished');
    })
  } catch (error) {
    console.error(`continueMission failed. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.continueMission<sup>10+</sup>

continueMission(parameter: ContinueMissionInfo): Promise&lt;void&gt;

Continues the mission of a specified application from the source device to the target device by specifying the bundle name. This API uses a promise to return the result.

**Required permissions**: ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                     | Mandatory  | Description   |
| --------- | --------------------------------------- | ---- | ----- |
| parameter | [ContinueMissionInfo](./js-apis-inner-application-continueMissionInfo-sys.md) | Yes    | Migration information, including fields such as source device ID, target device ID, application bundle name, and custom parameters. |

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Return value of the Promise object. When the operation succeeds, it indicates that the mission migration by bundle name is complete. When the operation fails, it returns an error message. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Distributed Scheduler Error Codes](./errorcode-DistributedSchedule.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 201      | Permission denied.|
| 202 | The application is not system-app, can not use system-api. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 16300501 | The system ability work abnormally. |
| 16300503 | The application is not installed on the remote end and installation-free is not supported. |
| 16300504 | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| 16300505 | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| 16300506 | The local continuation task is already in progress. |
| 16300507 | Failed to get the missionInfo of the specified bundle name. |

**Example**

  ```ts
  import { distributedMissionManager } from '@kit.AbilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  try {
      distributedMissionManager.continueMission(
        {
          srcDeviceId: '',
          dstDeviceId: '',
          bundleName: 'ohos.test.continueapp',
          wantParam: {"key": "value"}
        }
      ).then(() => {
          console.info('continueMission finished successfully');
      }).catch((error: BusinessError) => {
          console.error(`Failed to continue mission. Code: ${error.code}, message: ${error.message}`);
      });
  } catch (error) {
      console.error(`Failed to continue mission. Code: ${error.code}, message: ${error.message}`);
  }
  ```

## distributedMissionManager.on('continueStateChange')<sup>10+</sup>

on(type: 'continueStateChange',  callback: Callback&lt;ContinueCallbackInfo&gt;): void

Registers listening for the mission continuation state change event. This API must be used in pair with `off('continueStateChange')`. When listening is no longer needed, unregister it in a timely manner. The calling sequence is to register listening through `on` first, and then call `off` to unregister listening when it is no longer needed.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type | string  | Yes    | Type of the event to subscribe to. The value is 'continueStateChange', indicating subscription to the mission state change event. |
| callback | Callback&lt;[ContinueCallbackInfo](#continuecallbackinfo11)&gt; | Yes   | Callback used to return the continuation state and information of the current mission.   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
  import { distributedMissionManager } from '@kit.AbilityKit';

  try {
    // Register a listener for mission continuation state change events.
    distributedMissionManager.on('continueStateChange', (data) => {
      console.info("continueStateChange on:" + JSON.stringify(data));
    });
  } catch (error) {
    console.error(`continueStateChange failed. Code: ${error.code}, message: ${error.message}`);
  }
```

## distributedMissionManager.off('continueStateChange')<sup>10+</sup>

off(type: 'continueStateChange',  callback?: Callback&lt;ContinueCallbackInfo&gt;): void

Unregisters the state listening for the current mission continuation. This API must be used in pair with `on('continueStateChange')`, and it should be called in a timely manner to release resources when listening is no longer needed.

**Required permissions**: ohos.permission.MANAGE_MISSIONS

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

**Parameters**

| Name      | Type                                      | Mandatory  | Description      |
| --------- | ---------------------------------------- | ---- | -------- |
| type | string  | Yes    | Event type to unregister. The value is fixed at 'continueStateChange', which indicates unregistering the mission continuation state change event.    |
| callback | Callback&lt;[ContinueCallbackInfo](#continuecallbackinfo11)&gt; | No    | Callback to be unregistered.<br>Pass this parameter to unregister a specific callback listener; do not pass it to unregister all callback listeners of the type. If this parameter is not passed, all callback listeners of this event type are unregistered.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 201      | Permission denied.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```js
  import { distributedMissionManager } from '@kit.AbilityKit';

  try {
    // Unregister listening for mission continuation state change events.
    distributedMissionManager.off('continueStateChange', (data) => {
      console.info("continueStateChange off:" + JSON.stringify(data));
    });
  } catch (err) {
    console.error(`continueStateChange failed. Code: ${err.code}, message: ${err.message}`);
  }
```

## MissionCallback<sup>10+</sup>

type MissionCallback = _MissionCallback

Callback function used to listen for task state changes, including mission list change notification, mission snapshot notification, and disconnection notification. As the input parameter of [registerMissionListener](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerregistermissionlistener), it indicates the callback function established after register listening.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Type| Description|
| --- | --- |
| [_MissionCallback](js-apis-inner-application-missionCallbacks-sys.md) | Callback function used to listen for task state changes, including mission list change notifications, mission snapshot notifications, and disconnection notifications. As an input parameter of registerMissionListener, it represents the callback function established after register listening.|

## MissionParameter<sup>10+</sup>

type MissionParameter = _MissionParameter

Parameter object required for synchronizing the remote mission list, containing fields such as deviceId, fixConflict, and tag. It is used as the input parameter of [startSyncRemoteMissions](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerstartsyncremotemissions).

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Type| Description|
| --- | --- |
| [_MissionParameter](js-apis-inner-application-missionParameter-sys.md) | Parameter object required for synchronizing the mission list of a remote device, including fields such as deviceId, fixConflict, and tag.|

## MissionDeviceInfo<sup>10+</sup>

type MissionDeviceInfo = _MissionDeviceInfo

Defines the device information object required for registering a mission state listener, including device identifier fields such as deviceId. It is used as an input parameter of [registerMissionListener](js-apis-distributedMissionManager-sys.md#distributedmissionmanagerregistermissionlistener).

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Type| Description|
| --- | --- |
| [_MissionDeviceInfo](js-apis-inner-application-missionDeviceInfo-sys.md) | Device information object required for register listening, including the deviceId field. |

## ContinueState<sup>10+</sup>

Enumerates the mission continuation states.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Name          | Value      | Description                                                        |
| ------------- | --------- | ------------------------------------------------------------ |
| ACTIVE        | 0         | Continuation is activated for the current mission.                             |
| INACTIVE      | 1         | Continuation is not activated for the current mission.                           |

## ContinueCallbackInfo<sup>11+</sup>

Defines the information object returned in the mission continuation state listening callback, including two fields: state (continuation state) and info (continuation details). A state value of ACTIVE indicates that the continuation is in the active state, and INACTIVE indicates that the continuation is in the inactive state.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.AbilityRuntime.Mission

**Device behavior difference:** This API does not take effect on Wearable devices that do not support distributed services.

| Name      | Type   | Read-Only  | Optional  | Description         |
| -------- | ------ | ---- | ---- | ----------- |
| state | [ContinueState](#continuestate10) | No | No | Current continuation state of the mission. The value is ACTIVE or INACTIVE, set based on the actual continuation state of the mission. |
| info  | [ContinuableInfo](./js-apis-inner-application-continuableInfo-sys.md) | No   | No   |   Continuation information of the mission.|