# getBundleInfos（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void--><!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, userId: number, callback: AsyncCallback<Array<BundleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | 是 | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | 是 | User ID. Value range: greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-depr-i.md)&gt;&gt; | 是 | Callback used to return the result. If ${具体的操作} is successful, **err** is **undefined**, and ${XX} is ${XX} obtained. Otherwise, **err** is an error object. |

<!--Del-->
**示例**

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

<!--DelEnd-->


## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void--><!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, callback: AsyncCallback<Array<BundleInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | 是 | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-depr-i.md)&gt;&gt; | 是 | Callback used to return the result. If getBundleInfos is successful, **err** is **undefined**, and all available BundleInfo as the input parameter at program startup. Otherwise, **err** is an error object. |

<!--Del-->
**示例**

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

<!--DelEnd-->


## getBundleInfos

```TypeScript
function getBundleInfos(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>--><!--Device-bundle-function getBundleInfos(bundleFlag: BundleFlag, userId?: number): Promise<Array<BundleInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlag | [BundleFlag](arkts-ability-bundle-bundleflag-e.md) | 是 | Flag used to specify the information contained in the returned bundle information object. Value range: see the bundle information related flags in [BundleFlag](arkts-ability-bundle-bundleflag-e.md). |
| userId | number | 否 | User ID.Default value: the user to which the caller belongs. Value range: greater than or equal to 0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[BundleInfo](arkts-ability-bundleinfo-depr-i.md)&gt;&gt; | Promise used to return all available BundleInfo. |

<!--Del-->
**示例**

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

<!--DelEnd-->
