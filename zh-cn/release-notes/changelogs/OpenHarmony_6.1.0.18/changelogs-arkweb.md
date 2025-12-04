# ArkWeb子系统changelog

## cl.arkweb.1 ArkWeb遗留内核M114下线

**访问级别**

公共能力

**变更原因**

遗留内核M114版本生命周期已结束。为了提升开发者使用ArkWeb内核的安全性，使用最新的W3C特性，以及获得最新的性能体验优化成果，系统正式下线M114内核，仅支持M132内核。

**变更影响**

变更前：三方应用调用[setActiveWebEngineVersion](../../../application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#setactivewebengineversion20)(ArkWebEngineVersion::M114)选择使用遗留内核M114，基于[getActiveWebEngineVersion](../../../application-dev/reference/apis-arkweb/arkts-apis-webview-WebviewController.md#getactivewebengineversion20)接口查询的内核版本为M114。

变更后：三方应用调用setActiveWebEngineVersion(ArkWebEngineVersion::M114)无效，不会抛异常，基于getActiveWebEngineVersion接口查询的内核版本为M132。

**起始API Level**

不涉及

**变更发生版本**

从OpenHarmony SDK 6.1.0.18开始。

**关键的接口/组件变更**

ArkWeb

**适配指导**

如果三方应用使用遗留内核M114的Web组件展示网页内容，则需要遵循[ArkWeb 版本的差异总结](https://gitcode.com/openharmony-tpc/chromium_src/blob/132_trunk/web/ReleaseNote/ArkWeb_114_132.md)中所涉及的最新W3C规格变更完成适配。