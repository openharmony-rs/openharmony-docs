# setAbilityEnabled (System API)

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnable: boolean, callback: AsyncCallback<void>): void
```

Sets whether to enable an ability. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md) | Yes | Ability information. |
| isEnable | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";
let abilityName: string = "EntryAbility";

bundle.getAbilityInfo(bundleName, abilityName).then((abilityInfo) => {
  console.info('getAbilityInfo successfully. Data: ' + JSON.stringify(abilityInfo));

  bundle.setAbilityEnabled(abilityInfo, false).then(data => {
    console.info('setAbilityEnabled successfully.');
  }).catch((error: BusinessError) => {
    console.error('setAbilityEnabled failed:' + JSON.stringify(error));
  })
}).catch((error: BusinessError) => {
  console.error('getAbilityInfo failed. Cause: ' + JSON.stringify(error));
});
```


## setAbilityEnabled

```TypeScript
function setAbilityEnabled(info: AbilityInfo, isEnable: boolean): Promise<void>
```

Sets whether to enable an ability. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md) | Yes | Ability information. |
| isEnable | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setAbilityEnabled](#setabilityenabled)
