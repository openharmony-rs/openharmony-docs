# startContinuationDeviceManager

## Modules to Import

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## startContinuationDeviceManager

```TypeScript
function startContinuationDeviceManager(token: number, callback: AsyncCallback<void>): void
```

Starts the device selection module to show the list of available devices on the network. This API does not involve any filter parameters and uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 22

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the module is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-the-system-ability-works-abnormally) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-the-specified-token-or-callback-is-not-registered) | The specified token or callback is not registered. |

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = -1;
try {
  continuationManager.startContinuationDeviceManager(token, (err) => {
    if (err.code != 0) {
      console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
      return;
    }
    console.info('startContinuationDeviceManager finished. ');
  });
} catch (err) {
  console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
}
```


<a id="startcontinuationdevicemanager-1"></a>

## startContinuationDeviceManager

```TypeScript
function startContinuationDeviceManager(
    token: number,
    options: ContinuationExtraParams,
    callback: AsyncCallback<void>
  ): void
```

Starts the device selection module to show the list of available devices on the network. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 22

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| options | [ContinuationExtraParams](arkts-ability-continuationmanager-continuationextraparams-t.md) | Yes | Extra parameters used to filter the list of available devices. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the module is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-the-system-ability-works-abnormally) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-the-specified-token-or-callback-is-not-registered) | The specified token or callback is not registered. |

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = -1;
try {
  continuationManager.startContinuationDeviceManager(
    token,
    {
      deviceType: ["00E"]
    },
    (err) => {
      if (err.code != 0) {
        console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
        return;
      }
      console.info('startContinuationDeviceManager finished. ');
  });
} catch (err) {
  console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
}
```


<a id="startcontinuationdevicemanager-2"></a>

## startContinuationDeviceManager

```TypeScript
function startContinuationDeviceManager(token: number, options?: ContinuationExtraParams): Promise<void>
```

Starts the device selection module to show the list of available devices on the network. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 22

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| options | [ContinuationExtraParams](arkts-ability-continuationmanager-continuationextraparams-t.md) | No | Extra parameters used to filter the list of available devices. This parameter can be null. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types;<br>2. Parameter verification failed; |
| [16600001](../errorcode-DistributedSchedule.md#16600001-the-system-ability-works-abnormally) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-the-specified-token-or-callback-is-not-registered) | The specified token or callback is not registered. |

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = -1;
try {
  continuationManager.startContinuationDeviceManager(
    token,
    {
      deviceType: ["00E"]
    }).then(() => {
      console.info('startContinuationDeviceManager finished. ');
    }).catch((err: BusinessError) => {
      console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
    });
} catch (err) {
  console.error('startContinuationDeviceManager failed, cause: ' + JSON.stringify(err));
}
```
