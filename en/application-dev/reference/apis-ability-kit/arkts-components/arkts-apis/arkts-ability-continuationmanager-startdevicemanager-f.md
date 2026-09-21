# startDeviceManager

## Modules to Import

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## startDeviceManager

```TypeScript
function startDeviceManager(token: number, callback: AsyncCallback<void>): void
```

Starts the device selection module to show the list of available devices on the network. This API does not involve any filter parameters and uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startDiscovering](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the module is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
continuationManager.startDeviceManager(token, (err) => {
  if (err.code != 0) {
    console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
    return;
  }
  console.info('startDeviceManager finished. ');
});
```


<a id="startdevicemanager-1"></a>

## startDeviceManager

```TypeScript
function startDeviceManager(token: number, options: ContinuationExtraParams, callback: AsyncCallback<void>): void
```

Starts the device selection module to show the list of available devices on the network. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startDiscovering](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| options | [ContinuationExtraParams](arkts-ability-continuationmanager-continuationextraparams-t.md) | Yes | Extra parameters used to filter the list of available devices. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the module is started, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';

let token: number = 1;
continuationManager.startDeviceManager(
  token,
  {
    deviceType: ["00E"]
  },
  (err) => {
    if (err.code != 0) {
      console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
      return;
    }
    console.info('startDeviceManager finished. ');
});
```


<a id="startdevicemanager-2"></a>

## startDeviceManager

```TypeScript
function startDeviceManager(token: number, options?: ContinuationExtraParams): Promise<void>
```

Starts the device selection module to show the list of available devices on the network. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [startDiscovering](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#startdiscovering)(discoverParam: { [key: string]: Object; }, filterOptions?: { [key: string]: Object; })

**Model restriction:** This API can be used only in the stage model.

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

**Examples**

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let token: number = -1;
continuationManager.startDeviceManager(
  token,
  {
    deviceType: ["00E"]
  }).then(() => {
    console.info('startDeviceManager finished. ');
  }).catch((err: BusinessError) => {
    console.error('startDeviceManager failed, cause: ' + JSON.stringify(err));
});
```
