# getApplicationInfos（系统接口）

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getApplicationInfos

```TypeScript
function getApplicationInfos(bundleFlags: number, userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getApplicationInfos(bundleFlags: number, userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundle-function getApplicationInfos(bundleFlags: number, userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in BundleFlag. |
| userId | number | 是 | User ID. Value range: greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ApplicationInfo](arkts-ability-applicationinfo-depr-i.md)&gt;&gt; | 是 | Callback used to return the result. If getApplicationInfos is successful, **err** is **undefined**, and the list of app information as the input parameter at program startup. Otherwise, **err** is an error object. |

<!--Del-->
**示例**

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;
let userId: number = 100;

bundle.getApplicationInfos(bundleFlags, userId, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

<!--DelEnd-->


## getApplicationInfos

```TypeScript
function getApplicationInfos(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getApplicationInfos(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundle-function getApplicationInfos(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in BundleFlag. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ApplicationInfo](arkts-ability-applicationinfo-depr-i.md)&gt;&gt; | 是 | Callback used to return the result. If getApplicationInfos is successful, **err** is **undefined**, and the list of app information as the input parameter at program startup. Otherwise, **err** is an error object. |

<!--Del-->
**示例**

```TypeScript
import bundle from '@ohos.bundle';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;

bundle.getApplicationInfos(bundleFlags, (err, data) => {
  if (err) {
    console.error('Operation failed. Cause: ' + JSON.stringify(err));
    return;
  }
  console.info('Operation successful. Data:' + JSON.stringify(data));
})
```

<!--DelEnd-->


## getApplicationInfos

```TypeScript
function getApplicationInfos(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>
```

**起始版本：** 7

**废弃版本：** 8

**替代接口：** [getAllApplicationInfo](arkts-ability-bundlemanager-getallapplicationinfo-f-sys.md)

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getApplicationInfos(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>--><!--Device-bundle-function getApplicationInfos(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | Flag used to specify the information contained in the returned application information object. Value range: see the application information related flags in BundleFlag. |
| userId | number | 否 | User ID. Default value: the user to which the caller belongs. Value range: greater than or equal to 0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[ApplicationInfo](arkts-ability-applicationinfo-depr-i.md)&gt;&gt; | Promise used to return the list of app information when obtained successfully. |

<!--Del-->
**示例**

```TypeScript
import bundle from '@ohos.bundle';
import { BusinessError } from '@ohos.base';

let bundleFlags: number = bundle.BundleFlag.GET_APPLICATION_INFO_WITH_PERMISSION;
let userId: number = 100;

bundle.getApplicationInfos(bundleFlags, userId)
  .then((data) => {
    console.info('Operation successful. Data: ' + JSON.stringify(data));
  }).catch((error: BusinessError) => {
    console.error('Operation failed. Cause: ' + JSON.stringify(error));
  })
```

<!--DelEnd-->
