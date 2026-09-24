# continueMission (System API)

## Modules to Import

```TypeScript
import { distributedMissionManager } from '@kit.AbilityKit';
```

## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback, callback: AsyncCallback<void>): void
```

Continues a mission on a remote device, with the mission ID specified. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | Yes | Parameters required for mission continuation. |
| options | [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | Yes | Callback invoked when the mission continuation is complete. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is continued, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-the-system-ability-works-abnormally) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-failed-to-get-the-missioninfo-of-the-specified-missionid) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-not-supported) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-supported-try-again-with-the-freeinstall-flag) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-the-operation-device-must-be-the-device-where-the-application-to-be-continued-is-currently-located-or-the-target-device) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-the-local-continuation-task-is-already-in-progress) | The local continuation task is already in progress. |

**Examples**

```TypeScript
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


<a id="continuemission-1"></a>

## continueMission

```TypeScript
function continueMission(parameter: ContinueDeviceInfo, options: ContinueCallback): Promise<void>
```

Continues a mission on a remote device, with the mission ID specified. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [ContinueDeviceInfo](arkts-ability-distributedmissionmanager-continuedeviceinfo-t-sys.md) | Yes | Parameters required for mission continuation. |
| options | [ContinueCallback](arkts-ability-distributedmissionmanager-continuecallback-t-sys.md) | Yes | Callback invoked when the mission continuation is complete. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-the-system-ability-works-abnormally) | The system ability work abnormally. |
| [16300502](../errorcode-DistributedSchedule.md#16300502-failed-to-get-the-missioninfo-of-the-specified-missionid) | Failed to get the missionInfo of the specified missionId. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-not-supported) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-supported-try-again-with-the-freeinstall-flag) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-the-operation-device-must-be-the-device-where-the-application-to-be-continued-is-currently-located-or-the-target-device) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-the-local-continuation-task-is-already-in-progress) | The local continuation task is already in progress. |

**Examples**

```TypeScript
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


<a id="continuemission-2"></a>

## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo, callback: AsyncCallback<void>): void
```

Continues a mission on a remote device, with the bundle name specified. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | Yes | Parameters required for mission continuation. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the mission is continued, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-the-system-ability-works-abnormally) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-not-supported) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-supported-try-again-with-the-freeinstall-flag) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-the-operation-device-must-be-the-device-where-the-application-to-be-continued-is-currently-located-or-the-target-device) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-the-local-continuation-task-is-already-in-progress) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-failed-to-get-the-missioninfo-of-the-specified-bundlename) | Failed to get the missionInfo of the specified bundle name. |

**Examples**

```TypeScript
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


<a id="continuemission-3"></a>

## continueMission

```TypeScript
function continueMission(parameter: ContinueMissionInfo): Promise<void>
```

Continues a mission on a remote device, with the bundle name specified. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_MISSIONS and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Mission

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parameter | [ContinueMissionInfo](arkts-ability-distributedmissionmanager-continuemissioninfo-t-sys.md) | Yes | Parameters required for mission continuation. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16300501](../errorcode-DistributedSchedule.md#16300501-the-system-ability-works-abnormally) | The system ability work abnormally. |
| [16300503](../errorcode-DistributedSchedule.md#16300503-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-not-supported) | The application is not installed on the remote end and installation-free is not supported. |
| [16300504](../errorcode-DistributedSchedule.md#16300504-the-application-is-not-installed-on-the-remote-end-and-installation-free-is-supported-try-again-with-the-freeinstall-flag) | The application is not installed on the remote end but installation-free is supported, try again with freeInstall flag. |
| [16300505](../errorcode-DistributedSchedule.md#16300505-the-operation-device-must-be-the-device-where-the-application-to-be-continued-is-currently-located-or-the-target-device) | The operation device must be the device where the application to be continued is located or the target device to be continued. |
| [16300506](../errorcode-DistributedSchedule.md#16300506-the-local-continuation-task-is-already-in-progress) | The local continuation task is already in progress. |
| [16300507](../errorcode-DistributedSchedule.md#16300507-failed-to-get-the-missioninfo-of-the-specified-bundlename) | Failed to get the missionInfo of the specified bundle name. |

**Examples**

```TypeScript
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
