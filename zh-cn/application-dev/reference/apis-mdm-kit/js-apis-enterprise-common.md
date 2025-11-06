# @ohos.enterprise.common
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

本模块提供通用接口或枚举

## ApplicationInstance<sup>22+</sup>

应用的实例数据。
该接口目前在[addUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddusernonstopapps22)、[removeUserNonStopApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremoveusernonstopapps22)、[addFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanageraddfreezeexemptedapps22)、[removeFreezeExemptedApps](./js-apis-enterprise-applicationManager.md#applicationmanagerremovefreezeexemptedapps22)接口中作为入参使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

| 名称          | 类型                             | 只读 | 可选 | 说明                                                        |
| ------------- | --------------------------------| ---- | -----| ------------------------------------------------------ |
| appIdentifier          | string       | 否   | 否 | 应用[唯一标识符](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo)，可以通过接口[bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2)获取bundleInfo.signatureInfo.appIdentifier。           |
| accountId        | number       | 否   | 否 | 用户ID。取值范围：大于等于0的整数。<br> accountId可以通过[getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1)接口获取。            |
| appIndex        | number       | 否   | 否 | 应用分身索引。取值范围：大于等于0的整数。<br> appIndex可以通过[getAppCloneIdentity](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetappcloneidentity14)接口获取。           |
