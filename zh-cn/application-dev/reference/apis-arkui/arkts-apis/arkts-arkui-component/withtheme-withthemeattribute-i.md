# WithThemeAttribute

不支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和[通用事件]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface WithThemeAttribute--><!--Device-unnamed-export declare interface WithThemeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyAttributesFinish

```TypeScript
default applyAttributesFinish(): void
```

通知组件已完成设置其属性。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithThemeAttribute-default applyAttributesFinish(): void--><!--Device-WithThemeAttribute-default applyAttributesFinish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## debugLine

```TypeScript
default debugLine(sourceLine: string, moduleName?: string): this
```

设置组件的源码跳转信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithThemeAttribute-default debugLine(sourceLine: string, moduleName?: string): this--><!--Device-WithThemeAttribute-default debugLine(sourceLine: string, moduleName?: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sourceLine | string | 是 | 源代码行。 |
| moduleName | string | 否 | 组件所属的模块。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setWithThemeOptions

```TypeScript
default setWithThemeOptions(options: WithThemeOptions | undefined): this
```

设置WithTheme选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WithThemeAttribute-default setWithThemeOptions(options: WithThemeOptions | undefined): this--><!--Device-WithThemeAttribute-default setWithThemeOptions(options: WithThemeOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 创建WithTheme的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回WithThemeAttribute的实例。 |

