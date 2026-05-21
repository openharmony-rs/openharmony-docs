# SkillInfo
<!--Kit: Ability Kit-->
<!--Subsystem: BundleManager-->
<!--Owner: @wanghang904-->
<!--Designer: @hanfeng6-->
<!--Tester: @kongjing2-->
<!--Adviser: @HelloCrease-->

技能（Skill）是系统为AI 代理提供的能力封装单元。技能通过[module.json5配置文件](../../quick-start/module-configuration-file.md#skillprofiles标签)中的skillProfiles标签声明能力。应用可以通过[skillManager](js-apis-skillManager.md)中提供的接口查询已安装的技能信息，发现并调用设备上的AI 代理能力。

>
>**说明：**
>
>本模块仅适用于ArkTS-Dyn。

**起始版本：** 26.0.0

## 导入模块

```ts
import { skillManager } from '@kit.AbilityKit';
```

## SkillInfo

技能配置信息，用于定义AI 代理的技能能力。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称           | 类型   | 只读 | 可选 | 说明           |
| -------------- | ------ | ---- | ---- | -------------- |
| bundleName   | string | 是   | 否   | 技能所属应用的包名。   |
| moduleName   | string | 是   | 否   | 技能所属模块的名称。   |
| skillName   | string | 是   | 否   | 技能的名称。   |
| skillType   | [SkillType](#skilltype) | 是   | 否   | 技能的类型。   |
| skillPath   | string | 是   | 否   | 技能的安装路径。   |
| abilityName   | string | 是   | 否   | 技能关联的ability名称。   |
| versionCode   | number | 是   | 否   | 技能的版本号。   |
| description   | string | 是   | 是   | 技能的描述信息。默认值为undefined。 |
| srcEntries   | Array\<string\> | 是   | 是   | 实现技能的代码文件路径列表。默认值为undefined。  |
| permissions   | Array\<string\> | 是   | 是   | 调用该技能所需要的权限列表。默认值为undefined。  |
| requestPermissions   | Array\<string\> | 是   | 是   | 技能所在的模块申请的权限。默认值为undefined。|

## SkillType

技能类型的枚举。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 26开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

| 名称 | 值 | 说明 |
| --- | --- |------|
| APP_SKILL | 0 | 应用技能。 |
| INDEPENDENT_SKILL | 1 | 独立技能。 |
