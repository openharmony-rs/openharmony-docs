# getBundleInfos (System API)

## Modules to Import

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

Obtains all BundleInfo for a specified user in the system. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** getAllBundleInfo

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | Yes | User ID. Value range: greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the result. If getBundleInfos is successful, **err** is **undefined**, and the BundleInfo of all bundles under the specified user as the input parameter at program startup. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;
let userId: number = 100;

bundle.getBundleInfos(bundleFlag, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;

bundle.getBundleInfos(bundleFlag, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlag: number = bundle.BundleFlag.GET_BUNDLE_DEFAULT;
let userId: number = 100;

bundle.getBundleInfos(bundleFlag, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```


## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void
```

Obtains all BundleInfo for the current user. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** getAllBundleInfo

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Yes | Callback used to return the result. If getBundleInfos is successful, **err** is **undefined**, and all available BundleInfo as the input parameter at program startup. Otherwise, **err** is an error object. |

**Examples**

See [getBundleInfos](#getbundleinfos)


## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>
```

Obtains all BundleInfo for a specified user. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 8

**Substitutes:** getAllBundleInfo

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | Yes | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | No | User ID.Default value: the user to which the caller belongs. Value range: greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-bundleinfo-depr-i.md)&gt;&gt; | Promise used to return all available BundleInfo. |

**Examples**

See [getBundleInfos](#getbundleinfos)
