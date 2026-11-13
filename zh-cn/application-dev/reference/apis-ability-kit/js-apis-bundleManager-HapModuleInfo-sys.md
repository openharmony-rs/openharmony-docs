# HapModuleInfo (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @memghaiyang-->
<!--Adviser: @HelloCrease-->

HAP信息，可以通过[getBundleInfoForSelf](js-apis-bundleManager.md#bundlemanagergetbundleinfoforself)获取自身的HAP信息，其中参数[bundleFlags](js-apis-bundleManager.md#bundleflag)至少包含GET_BUNDLE_INFO_WITH_HAP_MODULE。

**起始版本：** 26.0.1

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见（[HapModuleInfo](js-apis-bundleManager-hapModuleInfo.md)）。

## 导入模块

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## HapModuleInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

<!--Table: 20%; 20%; 8%; 8%; 44%-->
| 名称                              | 类型                                                         | 只读 | 可选 | 说明                 |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | -------------------- |
| codePhysicalPath                  | string                                                       | 是   | 是   | 模块的物理安装路径。<br>**模型约束：** 此字段仅可在Stage模型下使用。<br>**起始版本：** 26.0.1 |
 

