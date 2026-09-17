# setApplicationEnabled (System API)

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnable: boolean, callback: AsyncCallback<void>): void
```

Sets whether to enable an application. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| isEnable | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';

let bundleName: string = "com.example.myapplication";

bundle.setApplicationEnabled(bundleName, false, err => {
  if (err) {
    console.error('setApplicationEnabled failed.');
  } else {
    console.info('setApplicationEnabled successfully.');
  }
});
```

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleName: string = "com.example.myapplication";

bundle.setApplicationEnabled(bundleName, false).then(() => {
  console.info('setApplicationEnabled successfully.');
}).catch((error: BusinessError) => {
  console.error('setApplicationEnabled failed.');
});
```


## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnable: boolean): Promise<void>
```

Sets whether to enable an application. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** null

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| isEnable | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

See [setApplicationEnabled](#setapplicationenabled)
