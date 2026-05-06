# ArkTS子系统Changelog

## cl.arkts.1 JSVM基于上游社区的Chromium/v8内核从132升级为144版本

**访问级别**

公开接口

**变更原因**

为了提升使用JSVM应用的安全性，为开发者提供最新的W3C HTML5特性，Chromium上游社区从133到144版本共发布300+项特性，带来了更多W3C特性、安全、性能、稳定性的提升，故本次进行内核升级 (132 -> 144)。

**变更影响**

从上游社区300+ issue说明、社区5000+ ReleaseNotes以及JSVM xts/tdd用例测试，当前共发现38项需要开发者注意的变更点，请参考[JSVM 132 内核升级 144 内核版本差异总结](https://gitcode.com/openharmony/arkcompiler_jsvm/blob/master/ReleaseNote/JSVM_132_144.md)。

**起始 API Level**

不涉及

**变更发生版本**

从OpenHarmony SDK 7.0.0.18开始。

**变更的接口/组件**

ArkTS/JSVM

**适配指导**

如果在应用中使用Web组件展示网页内容，则需要遵循[JSVM 132 内核升级 144 内核版本差异总结](https://gitcode.com/openharmony/arkcompiler_jsvm/blob/master/ReleaseNote/JSVM_132_144.md)中所涉及的最新W3C规格变更。
