# 嵌入式组件公共接口

提供嵌入式组件相关的公共接口。

>  **说明：**
>
>  - 本模块仅适用于ArkTS-Sta。
>
>  - 本模块首批接口从API version 23开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## TerminationInfo<sup>23+</sup>

用于表示被拉起的UIExtensionAbility通过调用[terminateSelfWithResult](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateselfwithresult)或者[terminateSelf](../../apis-ability-kit/js-apis-app-ability-uiExtensionContentSession.md#terminateself)正常退出时的返回结果。

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 23

| 名称 | 类型                      | 只读 | 可选 | 说明                                                 |
| ---- | -------------------------| ---- | ---- | ---------------------------------------------------- |
| code | int | 否 | 否 | 被拉起UIExtensionAbility退出时返回的结果码。 |
| want | [Want](../../apis-ability-kit/js-apis-app-ability-want.md) | 否 | 是 | 被拉起UIExtensionAbility退出时返回的数据。   |
