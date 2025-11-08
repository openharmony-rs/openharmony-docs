# @ohos.enterprise.common（Enterprise公共模块）
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->

本模块提供MDM Kit中常用公共能力的纯类型定义，包含枚举类型和数据结构。本模块仅导出类型声明，不包含具体实现逻辑或可执行代码。

> **说明：**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { common } from '@kit.MDMKit';
```

## ManagedPolicy

企业设备管控策略。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

| 名称         | 值 | 说明                            |
| ----------- | -------- | ------------------------------- |
| DEFAULT | 0  | 默认，无管控策略。|
| DISALLOW | 1  | 禁用。|
| FORCE_OPEN | 2  | 强制开启。|

## ApplicationInstance

应用的实例数据。
该接口目前在[addUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddusernonstopapps22)、[removeUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremoveusernonstopapps22)、[addFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddfreezeexemptedapps22)、[removeFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremovefreezeexemptedapps22)接口中作为入参使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

| 名称          | 类型                             | 只读 | 可选 | 说明                                                        |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| appIdentifier          | string       | 否   | 否 | 应用[唯一标识符](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo)，可以通过接口[bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2)获取bundleInfo.signatureInfo.appIdentifier。           |
| accountId        | number       | 否   | 否 | 用户ID。取值范围：大于等于0的整数。<br> accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1)接口获取。            |
| appIndex        | number       | 否   | 否 | 应用分身索引。取值范围：大于等于0的整数。<br> appIndex可以通过[getAppCloneIdentity](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetappcloneidentity14)接口获取。           |
