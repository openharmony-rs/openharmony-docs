# ListItemOptions

ListItem组件参数。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ListItemStyle
```

设置List组件卡片样式。
默认值：ListItemStyle.NONE
设置为ListItemStyle.NONE时无样式。
设置为ListItemStyle.CARD时，建议配合ListItemGroup的ListItemGroupStyle.CARD同时使用，显示默认卡片样式。
卡片样式下，ListItem默认规格：高度48vp，宽度100%，左右内边距8vp。如果需要实现ListItem高度自适应，可以把height设置为undefined。
卡片样式下，为卡片内的列表选项提供了默认的focus、hover、press、selected和disable样式。
当设置为ListItemStyle.CARD时，List的listDirection属性值须为Axis.Vertical，如果设置为Axis.Horizontal，会导致显示混乱；
List属性alignListItem默认为ListItemAlign.Center，居中对齐显示。

**类型：** ListItemStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

