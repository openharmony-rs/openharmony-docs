# isAbilityEnabled

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo, callback: AsyncCallback<boolean>): void
```

Checks whether the ability that matches a given AbilityInfo object is enabled. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md) | Yes | Ability information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. **true** if enabled, **false** otherwise. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName).then((abilityInfo) => {
  bundle.isAbilityEnabled(abilityInfo).then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
})
```

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName).then((abilityInfo) => {
  bundle.isAbilityEnabled(abilityInfo, (err, data) => {
    if (err) {
      console.error('Operation failed. Cause: ' + JSON.stringify(err));
      return;
    }
    console.info('Operation successful. Data:' + JSON.stringify(data));
  })
})
```


## isAbilityEnabled

```TypeScript
function isAbilityEnabled(info: AbilityInfo): Promise<boolean>
```

Checks whether the ability that matches a given AbilityInfo object is enabled. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md) | Yes | Ability information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. **true** if enabled, **false** otherwise. |

**Examples**

See [isAbilityEnabled](#isabilityenabled)
