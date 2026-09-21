# queryAbilityByWant

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want,
    bundleFlags: number, userId: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

Obtains the ability information of the specified user based on given Want. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name. |
| bundleFlags | number | Yes | Ability information to be returned. For details about the available enumerated values, see the ability information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | Yes | User ID. The value must be greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the ability information. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import Want from '@ohos.app.ability.Want';

let bundleFlags: number = 0;
let userId: number = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

bundle.queryAbilityByWant(want, bundleFlags, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


<a id="queryabilitybywant-1"></a>

## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

Obtains the ability information based on given Want. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name. |
| bundleFlags | number | Yes | Ability information to be returned. For details about the available enumerated values, see the ability information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the ability information. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import Want from '@ohos.app.ability.Want';

let bundleFlags: number = 0;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

bundle.queryAbilityByWant(want, bundleFlags, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


<a id="queryabilitybywant-2"></a>

## queryAbilityByWant

```TypeScript
function queryAbilityByWant(want: Want, bundleFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

Obtains the ability information based on given Want. This API uses a promise to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name. |
| bundleFlags | number | Yes | Ability information to be returned. For details about the available enumerated values, see the ability information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | No | User ID. The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-abilityinfo-abilityinfo-depr-i.md)&gt;&gt; | Promise used to return the ability information. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';
import Want from '@ohos.app.ability.Want';

let bundleFlags: number = 0;
let userId: number = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

bundle.queryAbilityByWant(want, bundleFlags, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```
