# RichEditorBuilderSpanOptions

设置builder插入的偏移位置和样式。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## dragBackgroundColor

```TypeScript
dragBackgroundColor? : ColorMetrics
```

设置BuilderSpan单独拖拽时的背板颜色。未配置或传入无效颜色值时，按默认值处理。默认值：跟随系统主题拖拽背板色。

**类型：** ColorMetrics

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isDragShadowNeeded

```TypeScript
isDragShadowNeeded?: boolean
```

设置BuilderSpan单独拖拽时是否需要投影。true表示需要投影，false表示不需要投影。未配置或传入无效值时，按默认值处理。默认值：true。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
