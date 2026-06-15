# AppProvisionInfo (系统接口)
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->

应用[HarmonyAppProvision配置文件](../../security/app-provision-structure.md)中的信息，可以通过[getAppProvisionInfo](./js-apis-bundleManager-sys.md#bundlemanagergetappprovisioninfo10)获取。

> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块为系统接口。

## 导入模块

```ts
import { bundleManager } from '@kit.AbilityKit';
```

## AppProvisionInfo

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

| 名称                      | 类型   | 只读 | 可选 | 说明                 |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| versionCode               | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 配置文件的版本号。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| versionName               | string | 是   | 否   | 配置文件的版本名称。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| uuid                      | string | 是   | 否   | 配置文件中的uuid。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| type                      | string | 是   | 否   | 配置文件的类型，为debug或release。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| appDistributionType       | string | 是   | 否   | 配置文件中的[分发类型](../../security/app-provision-structure.md)。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| validity                  | [Validity](#validity) | 是   | 否   | 配置文件中的有效期。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| developerId               | string | 是   | 否   | 配置文件中的开发者ID。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| certificate               | string | 是   | 否   | 配置文件中的证书信息。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| apl                       | string | 是   | 否   | 配置文件中的apl字段，为normal、system_basic和system_core其中之一。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| issuer                    | string | 是   | 否   | 配置文件中的发行者名称。<br>**ArkTS-Dyn起始版本：** 10<br>**ArkTS-Sta起始版本：** 23 |
| appIdentifier<sup>11+</sup> | string      | 是   | 否   | 应用的唯一标识，详情信息可参考[什么是appIdentifier](../../quick-start/common-problem-of-application.md#什么是appidentifier)。<br>**ArkTS-Dyn起始版本：** 11<br>**ArkTS-Sta起始版本：** 23 |
| organization<sup>12+</sup> | string       | 是   | 否   | 应用的组织信息。<br>**ArkTS-Dyn起始版本：** 12<br>**ArkTS-Sta起始版本：** 23 |
| bundleName<sup>23+</sup>  | string | 是   | 是   | 应用的包名。<br>**ArkTS-Dyn起始版本：** 23<br>**ArkTS-Sta起始版本：** 23 |

## Validity

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**ArkTS-Dyn起始版本：** 10

**ArkTS-Sta起始版本：** 23

**系统接口：** 此接口为系统接口。

| 名称                      | 类型   | 只读 | 可选 | 说明                 |
| ------------------------- | ------ | ---- | ---- | -------------------- |
| notBefore                 | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示配置文件有效期的开始时间，单位：秒。 |
| notAfter                  | ArkTS-Dyn: number<br>ArkTS-Sta: long | 是   | 否   | 表示配置文件有效期的结束时间，单位：秒。 |