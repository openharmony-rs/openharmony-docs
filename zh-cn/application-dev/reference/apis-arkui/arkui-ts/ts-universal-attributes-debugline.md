# 设置源码跳转信息

设置组件的源码跳转信息。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 从API version 24开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

## debugLine

debugLine(sourceLine: string, moduleName?: string): this

设置组件的源码跳转信息和组件所在模块。

[ArkTS编译工具链](../../../arkts-utils/compilation-tool-chain-overview.md)需调用本接口，[UI组件源码跳转](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-arkui-inspector#section1226015494335)功能才生效。开发者无需关注本接口。

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名   | 类型                           | 必填   | 说明                  |
| ----- | ---------------------------- | ---- | ------------------- |
| sourceLine | string | 是    | 设置组件的源码跳转信息。参数符合字符串类型即可。 |
| moduleName | string | 否    | 设置组件所在的模块名，对应[module.json5](../../../quick-start/module-configuration-file.md)中的name字段配置。用于明确当前组件的源码所处模块。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
|  this | 返回当前组件。 |