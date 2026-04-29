# 元能力子系统Changelog

## cl.ability.1 废弃ActionExtensionAbility
**访问级别**

公开

**变更原因**

ActionExtensionAbility设计用于系统分享操作区，系统分享操作区仅支持系统提供能力接入，三方开发者实现ActionExtensionAbility也无法接入操作区。

**变更影响**

此变更不涉及应用适配。

**起始 API Level**

API 10

**变更发生版本**

从OpenHarmony SDK 7.0.0.26开始。

**变更的接口/组件**

|模块名|变更类型|
|------|-------|
|api/@ohos.app.ability.ActionExtensionAbility.d.ts|废弃|

**适配指导**

如上所述。