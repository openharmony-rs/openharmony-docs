# BundleInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

应用包信息，可以通过[bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取自身的应用包信息，其中参数[bundleFlags](js-apis-bundleManager.md#bundleflag)指定所返回的[BundleInfo](js-apis-bundleManager-bundleInfo.md)中所包含的信息。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## BundleInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称                              | 类型                                                         | 只读 | 可选 | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name                              | string                                                       | 是   | 否   | 应用包的名称，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的bundleName字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| vendor                            | string                                                       | 是   | 否   | 应用包的供应商，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的vendor字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| versionCode                       | number                                                       | 是   | 否   | 应用包的版本号，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的versionCode字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| versionName                       | string                                                       | 是   | 否   | 应用包的版本文本描述信息，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的versionName字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| minCompatibleVersionCode          | number                                                       | 是   | 否   | 分布式场景下的应用包兼容的最低版本，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的minCompatibleVersionCode字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| targetVersion                     | number                                                       | 是   | 否   | 应用运行目标版本，对应[app.json5](../../quick-start/app-configuration-file.md)中配置的targetAPIVersion字段。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| appInfo                           | [ApplicationInfo](js-apis-bundleManager-applicationInfo.md)         | 是   | 否   | 应用程序的配置信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_APPLICATION获取。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| hapModulesInfo                    | Array\<[HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md)>     | 是   | 否   | 模块的配置信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE获取。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| reqPermissionDetails     | Array\<[ReqPermissionDetail](#reqpermissiondetail)>   | 是   | 否   | 应用运行时需向系统申请的权限集合的详细信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| permissionGrantStates        | Array\<[bundleManager.PermissionGrantState](js-apis-bundleManager.md#permissiongrantstate)> | 是   | 否   | 申请权限的授予状态，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_REQUESTED_PERMISSION获取。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| signatureInfo          | [SignatureInfo](#signatureinfo)                                          | 是   | 否   | 应用包的签名信息，通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_SIGNATURE_INFO获取。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| installTime                       | number                                                       | 是   | 否   | 应用包安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/> **说明：** <br/> 设备出厂首次开机时，如果未获取到当前时间，会以Unix时间戳基准（1970-01-01 08:00:00 UTC+8）作为当前系统的起始时间。例如，开机后未获取到时间，等待32s之后安装成功，则应用包安装时间戳为32000。 |
| updateTime                        | number                                                       | 是   | 否   | 应用包更新时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| routerMap<sup>12+</sup>           | Array\<[RouterItem](js-apis-bundleManager-hapModuleInfo.md#routeritem12)>           | 是   | 否   | 应用的路由表配置，由hapModulesInfo下的routerMap信息，根据RouterItem中的name字段进行去重后合并得到。通过调用[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)接口，bundleFlags参数传入GET_BUNDLE_INFO_WITH_HAP_MODULE和GET_BUNDLE_INFO_WITH_ROUTER_MAP获取。<br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |
| appIndex<sup>12+</sup>    | number    | 是   | 否   | 应用包的分身索引标识，仅在分身应用中生效。 |
| firstInstallTime<sup>18+</sup>                        | number                                                       | 是   | 是   | 应用在当前设备的首次安装时间戳，表示从1970-01-01 08:00:00 UTC+8逝去的毫秒数，单位毫秒，预置应用的首次安装时间戳为1533657660000。<br/>**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。 |


## ReqPermissionDetail

应用运行时需向系统申请的权限集合的详细信息。
> **说明：**
> - 如果应用内多包申请的权限名称一样，但是权限申请理由不一致，系统只会返回一个权限申请理由，优先级从高到低顺序为entry类型HAP、feature类型HAP、应用内HSP。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称                  | 类型                    | 只读 | 可选 | 说明                 |
| --------------------- | ----------------------- | ---- | ---- | ---------------------|
| name                  | string                  | 否   | 否   | 需要使用的[权限名称](../../security/AccessToken/app-permissions.md)。   |
| moduleName<sup>10+</sup>            | string                  | 否   | 否   | 申请该权限的module名称。   |
| reason                | string                  | 否   | 否   | 描述申请权限的原因。  |
| reasonId              | number                  | 否   | 否  | 描述申请权限的原因ID。 |
| usedScene             | [UsedScene](#usedscene) | 否   | 否   | 权限使用的场景和时机。 |



## UsedScene

描述权限使用的场景和时机。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称      | 类型           | 只读 | 可选 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| abilities | Array\<string> | 否   | 否   | 使用到该权限的Ability集合。   |
| when      | string         | 否   | 否   | 使用该权限的时机。支持的取值有inuse（使用时）、always（始终）。          |

## SignatureInfo

描述应用包的签名信息。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称      | 类型           | 只读 | 可选 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| appId     | string         | 是   | 否   | 应用的appId，由包名、下划线和证书公钥的Base64编码组成。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。                 |
|fingerprint| string         | 是   | 否   | 应用包的指纹信息，由签名证书通过SHA-256算法计算哈希值生成。使用的签名证书发生变化时，该字段也会发生变化。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。            |
|appIdentifier<sup>11+</sup>| string         | 是   | 否   | 应用的唯一标识，是AppGallery Connect创建应用时分配的[APP ID](https://developer.huawei.com/consumer/cn/doc/app/agc-help-createharmonyapp-0000001945392297)，为云端统一分配的随机字符串。该ID在应用全生命周期中不会发生变化，包括版本升级、证书变更、开发者公私钥变更、应用转移等。当需要进行跨设备调试、跨应用交互调试等场景，必须使用手动签名，签名方式的选择具体请参考[使用场景说明](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-signing#section54361623194519)。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。          |
|certificate<sup>14+</sup>| string         | 是   | 是   | 应用的证书公钥。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。            |

## AppCloneIdentity<sup>14+<sup>

描述应用包的身份信息。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称      | 类型           | 只读 | 可选 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| bundleName | string         | 是   | 否   | 应用的bundleName。          |
| appIndex | number | 是   | 否   | 应用包的分身索引信息。 |
