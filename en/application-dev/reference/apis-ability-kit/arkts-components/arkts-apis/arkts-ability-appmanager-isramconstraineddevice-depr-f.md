# isRamConstrainedDevice

## Modules to Import

```TypeScript
```

## isRamConstrainedDevice

```TypeScript
function isRamConstrainedDevice(): Promise<boolean>
```

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the API call result and the result indicating whether the device is RAM-constrained. You can perform error handling or custom processing in this callback. **true** if the device is RAM -constrained, **false** otherwise. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

appManager.isRamConstrainedDevice().then((data) => {
  console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`error: ${JSON.stringify(error)}`);
});
```


<a id="isramconstraineddevice-1"></a>

## isRamConstrainedDevice

```TypeScript
function isRamConstrainedDevice(callback: AsyncCallback<boolean>): void
```

Checks whether the current device is a RAM-constrained device (a device with severely limited memory resources). This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isRamConstrainedDevice](arkts-ability-appmanager-isramconstraineddevice-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the API call result and the result indicating whether the device is RAM-constrained. You can perform error handling or custom processing in this callback. **true** if the device is RAM-constrained, **false** otherwise. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';

appManager.isRamConstrainedDevice((error, data) => {
  if (error && error.code !== 0) {
    console.error(`isRamConstrainedDevice fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`The result of isRamConstrainedDevice is: ${JSON.stringify(data)}`);
  }
});
```
