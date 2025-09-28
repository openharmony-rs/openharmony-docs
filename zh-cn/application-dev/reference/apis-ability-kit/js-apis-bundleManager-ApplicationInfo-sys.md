# ApplicationInfo (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @Brilliantry_Rui-->

应用程序信息，可以通过[bundleManager.getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取自身的应用程序信息，其中参数[bundleFlags](js-apis-bundleManager.md#bundleflag)至少包含GET_BUNDLE_INFO_WITH_APPLICATION。

> **说明：**
>
> 本模块首批接口从API version 9 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见（[ApplicationInfo](js-apis-bundleManager-applicationInfo.md)）。

## 导入模块

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## ApplicationInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

| 名称      | 类型           | 只读 | 可选 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| flags<sup>12+</sup>    | number    | 是   | 是   | 标识当前应用和当前用户之间的状态集合，每一位表示一个特定的布尔状态，取值参考[ApplicationInfoFlag](js-apis-bundleManager-sys.md#applicationinfoflag12)。<br/>**系统API：** 从API version 12开始，该接口支持在系统API中使用。 |


## PreinstalledApplicationInfo<sup>12+<sup>

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

| 名称      | 类型           | 只读 | 可选 | 说明                        |
| --------- | -------------- | ---- | ---- | --------------------------- |
| bundleName | string         | 是   | 否   | 应用包的名称。                 |
| moduleName | string         | 是   | 否   | 应用包的模块名，返回entry模块的moduleName。若不存在entry模块则返回feature模块的moduleName。            |
| iconId | number         | 是   | 否   | 应用图标Id。            |
| labelId | number         | 是   | 否   | 应用标签Id。            |