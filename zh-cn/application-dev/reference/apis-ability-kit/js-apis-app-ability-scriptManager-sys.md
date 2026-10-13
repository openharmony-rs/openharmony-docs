# @ohos.app.ability.scriptManager (脚本管理)(系统接口)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @RuiChen_01-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

本模块提供管理和组织脚本信息的能力，支持应用的ArkTS脚本执行结果上报。

**起始版本：** 26.2.0

> **说明：**
>
> 当前页面仅包含本模块的系统接口，其他公开接口参见[@ohos.app.ability.scriptManager (脚本管理)](js-apis-app-ability-scriptManager.md)。

## 导入模块

```ts
import { scriptManager } from '@kit.AbilityKit';
```

## ArkTSScriptInfo

应用的ArkTS脚本入口函数的第一个参数，用于接收系统传递的脚本上下文信息。

**原子化服务API**：从API版本26.2.0开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AgentRuntime.Core

**系统接口**：此接口为系统接口。

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| toolCallId | string | 是 | 是 | 调用方传入的工具调用ID，用于将本次ArkTS脚本调用与调用方的维测步骤进行关联。当调用方未传入工具调用ID或传入空字符串时，该属性值为undefined。|
