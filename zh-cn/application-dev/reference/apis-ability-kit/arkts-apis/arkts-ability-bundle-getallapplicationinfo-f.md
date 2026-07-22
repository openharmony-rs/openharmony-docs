# getAllApplicationInfo

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number,
    userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

获取指定用户下所有已安装的应用信息，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getAllApplicationInfo(bundleFlags: number,    userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundle-function getAllApplicationInfo(bundleFlags: number,    userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中应用信息相关flag。 |
| userId | number | 是 | 用户ID。默认值：调用方所在用户，取值范围：大于等于0。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回应用信息列表。 |


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

获取调用方所在用户下已安装的应用信息，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void--><!--Device-bundle-function getAllApplicationInfo(bundleFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中应用信息相关flag。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;ApplicationInfo&gt;&gt; | 是 | 程序启动作为入参的回调函数，返回应用信息列表。 |


## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>
```

获取指定用户下所有已安装的应用信息，使用promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

<!--Device-bundle-function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>--><!--Device-bundle-function getAllApplicationInfo(bundleFlags: number, userId?: number): Promise<Array<ApplicationInfo>>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中应用信息相关flag。 |
| userId | number | 否 | 用户ID。默认值：调用方所在用户，取值范围：大于等于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ApplicationInfo&gt;&gt; | Promise对象，获取成功时返回应用信息列表。 |

