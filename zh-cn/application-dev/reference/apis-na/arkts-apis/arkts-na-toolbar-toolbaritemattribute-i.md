# ToolBarItemAttribute

定义ToolBarItem组件的属性方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ToolBarItemAttribute--><!--Device-unnamed-export declare interface ToolBarItemAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## applyAttributesFinish

```TypeScript
applyAttributesFinish(): void
```

通知ToolBarItem已完成属性设置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolBarItemAttribute-applyAttributesFinish(): void--><!--Device-ToolBarItemAttribute-applyAttributesFinish(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## debugLine

```TypeScript
debugLine(sourceLine: string, moduleName?: string): this
```

设置组件的源代码重定向信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolBarItemAttribute-debugLine(sourceLine: string, moduleName?: string): this--><!--Device-ToolBarItemAttribute-debugLine(sourceLine: string, moduleName?: string): this-End-->

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

## setToolBarItemOptions

```TypeScript
setToolBarItemOptions(options?: ToolBarItemOptions): this
```

设置toolbar item选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToolBarItemAttribute-setToolBarItemOptions(options?: ToolBarItemOptions): this--><!--Device-ToolBarItemAttribute-setToolBarItemOptions(options?: ToolBarItemOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ToolBarItemOptions](arkts-na-toolbar-toolbaritemoptions-i.md) | 否 | 列选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | ToolBarItemAttribute实例 |

