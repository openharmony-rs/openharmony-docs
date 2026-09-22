# GridItemOptions

```TypeScript
declare interface GridItemOptions
```

GridItem样式对象，用于配置GridItem的样式选项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: GridItemStyle
```

设置GridItem样式。

默认值：GridItemStyle.NONE

设置为GridItemStyle.NONE时无样式。

设置为GridItemStyle.PLAIN时，显示Hover、Press态样式。Hover态为鼠标悬停时的样式，Press态为按下时的样式。

**类型：** [GridItemStyle](arkts-arkui-griditem-comp-griditemstyle-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
