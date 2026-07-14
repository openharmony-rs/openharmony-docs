# RichEditorBuilderSpanOptions

设置builder的偏移位置和样式。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dragBackgroundColor

```TypeScript
dragBackgroundColor? : ColorMetrics
```

添加builder单独拖拽时的背板背景颜色。不配置或者异常值时，颜色按系统默认配置。

**类型：** ColorMetrics

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isDragShadowNeeded

```TypeScript
isDragShadowNeeded?: boolean
```

添加builder单独拖拽时是否需要投影。不配置或者异常值时，默认需要投影。true表示需要投影，false表示不需要投影。

默认值： true

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

