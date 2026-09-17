# getAllBundleInfo

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

Obtains the information of all bundles of the specified user. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Type of information that will be returned. For details about the available enumerated values, see the bundle information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | Yes | User ID. The default value is the user ID of the caller. The value must be greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the information of all bundles. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleFlag: number = 0;
let userId: number = 100;

bundle.getAllBundleInfo(bundleFlag, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlag: number = 0;

bundle.getAllBundleInfo(bundleFlag, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlag: number = 0;
let userId: number = 100;

bundle.getAllBundleInfo(bundleFlag, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void
```

Obtains the information of all bundles of the current user. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Type of information that will be returned. For details about the available enumerated values, see the bundle information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the information of all bundles. |

**Examples**

See [getAllBundleInfo](#getallbundleinfo)


## getAllBundleInfo

```TypeScript
function getAllBundleInfo(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>
```

Obtains the information of all bundles of the specified user. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Type of information that will be returned. For details about the available enumerated values, see the bundle information flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | No | User ID. The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Promise used to return the information of all bundles. |

**Examples**

See [getAllBundleInfo](#getallbundleinfo)
