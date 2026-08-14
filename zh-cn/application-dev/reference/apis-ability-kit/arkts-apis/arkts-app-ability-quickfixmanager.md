# @ohos.app.ability.quickFixManager

quickFixManager模块提供快速修复的能力，快速修复是系统提供给开发者的一种技术手段，支持开发者以远快于（小时级、分钟级）应用升级的方式进行缺陷修复。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace quickFixManager--><!--Device-unnamed-declare namespace quickFixManager-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.QuickFix

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [applyQuickFix](arkts-ability-quickfixmanager-applyquickfix-f-sys.md#applyQuickFix) | 快速修复的补丁安装接口。使用callback异步回调。 |
| [applyQuickFix](arkts-ability-quickfixmanager-applyquickfix-f-sys.md#applyQuickFix（系统接口）) | 快速修复的补丁安装接口。使用Promise异步回调。 |
| [getApplicationQuickFixInfo](arkts-ability-quickfixmanager-getapplicationquickfixinfo-f-sys.md#getApplicationQuickFixInfo) | 获取应用的快速修复信息。使用callback异步回调。 |
| [getApplicationQuickFixInfo](arkts-ability-quickfixmanager-getapplicationquickfixinfo-f-sys.md#getApplicationQuickFixInfo（系统接口）) | 获取应用的快速修复信息。使用Promise异步回调。 |
| [revokeQuickFix](arkts-ability-quickfixmanager-revokequickfix-f-sys.md#revokeQuickFix) | 撤销快速修复的接口，使用callback方式返回结果。 |
| [revokeQuickFix](arkts-ability-quickfixmanager-revokequickfix-f-sys.md#revokeQuickFix（系统接口）) | 撤销快速修复的接口。使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ApplicationQuickFixInfo](arkts-ability-quickfixmanager-applicationquickfixinfo-i-sys.md) | 应用级别的快速修复信息。 |
| [HapModuleQuickFixInfo](arkts-ability-quickfixmanager-hapmodulequickfixinfo-i-sys.md) | hap级别的快速修复信息。 |
<!--DelEnd-->

