# getBundleInfo

## 导入模块

```TypeScript
import { bundle } from '@kit.AbilityKit';
```

## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string,
    bundleFlags: number, options: BundleOptions, callback: AsyncCallback<BundleInfo>): void
```

根据给定的Bundle名称获取BundleInfo，使用callback异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getBundleInfo(bundleName: string,
    bundleFlags: number, options: BundleOptions, callback: AsyncCallback<BundleInfo>): void--><!--Device-bundle-function getBundleInfo(bundleName: string,
    bundleFlags: number, options: BundleOptions, callback: AsyncCallback<BundleInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中包信息相关flag。 |
| options | [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) | 是 | 包含userid。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<BundleInfo> | 是 | 程序启动作为入参的回调函数，返回包信息。 |


## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void
```

根据给定的Bundle名称获取BundleInfo，使用callback异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void--><!--Device-bundle-function getBundleInfo(bundleName: string, bundleFlags: number, callback: AsyncCallback<BundleInfo>): void-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 需要查询的应用Bundle名称。 |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中包信息相关flag。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<BundleInfo> | 是 | 程序启动作为入参的回调函数，返回包信息。 |


## getBundleInfo

```TypeScript
function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise<BundleInfo>
```

根据给定的Bundle名称获取BundleInfo，使用Promise异步回调。

获取调用方自己的信息时不需要权限。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

**需要权限：** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

<!--Device-bundle-function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise<BundleInfo>--><!--Device-bundle-function getBundleInfo(bundleName: string, bundleFlags: number, options?: BundleOptions): Promise<BundleInfo>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 要查询的应用Bundle名称。 |
| bundleFlags | number | 是 | 用于指定返回的应用信息对象中包含信息的标记。取值范围：参考[BundleFlag说明](arkts-ability-bundle-bundleflag-e.md)中包信息相关flag。 |
| options | [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) | 否 | 包含userid的查询选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<BundleInfo> | Promise对象，获取成功时返回包信息。 |

