# ListItemGroupOptions

ListItemGroup组件参数。

**起始版本：** 9

<!--Device-unnamed-declare interface ListItemGroupOptions--><!--Device-unnamed-declare interface ListItemGroupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## footer

```TypeScript
footer?: CustomBuilder
```

设置ListItemGroup尾部组件。 **说明：** 可以放单个子组件或不放子组件，不设置时无尾部组件。该参数的优先级低于参数footerComponent。即同时设置footer和footerComponent时，以footerComponent设置的值为准。

**类型：** CustomBuilder

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-footer?: CustomBuilder--><!--Device-ListItemGroupOptions-footer?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerComponent

```TypeScript
footerComponent?: ComponentContent
```

使用ComponentContent类型参数设置ListItemGroup尾部组件。 **说明：** 可以放单个子组件或不放子组件，不设置时无尾部组件。该参数的优先级高于参数footer。即同时设置footer和footerComponent时，以footerComponent设置的值为准。 同一个footerComponent不推荐同时给不同的ListItemGroup使用，否则会导致显示问题。

**类型：** ComponentContent

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-footerComponent?: ComponentContent--><!--Device-ListItemGroupOptions-footerComponent?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerStyle

```TypeScript
footerStyle?: ListItemGroupHeaderFooterStyle
```

设置ListItemGroup尾部样式。 默认值：ListItemGroupHeaderFooterStyle.NONE 设置为ListItemGroupHeaderFooterStyle.NONE时无样式。 设置为ListItemGroupHeaderFooterStyle.FLOATING时，尾部组件在滚动时悬浮显示。

**类型：** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md)

**默认值：** ListItemGroupHeaderFooterStyle.NONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: CustomBuilder
```

设置ListItemGroup头部组件。 **说明：** 可以放单个子组件或不放子组件，不设置时无头部组件。该参数的优先级低于参数headerComponent。即同时设置header和headerComponent时，以headerComponent设置的值为准。

**类型：** CustomBuilder

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-header?: CustomBuilder--><!--Device-ListItemGroupOptions-header?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## headerComponent

```TypeScript
headerComponent?: ComponentContent
```

使用ComponentContent类型参数设置ListItemGroup头部组件。 **说明：** 可以放单个子组件或不放子组件，不设置时无头部组件。该参数的优先级高于参数header。即同时设置header和headerComponent时，以headerComponent设置的值为准。 同一个headerComponent不推荐同时给不同的ListItemGroup使用，否则会导致显示问题。

**类型：** ComponentContent

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-headerComponent?: ComponentContent--><!--Device-ListItemGroupOptions-headerComponent?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## headerStyle

```TypeScript
headerStyle?: ListItemGroupHeaderFooterStyle
```

设置ListItemGroup头部样式。 默认值：ListItemGroupHeaderFooterStyle.NONE 设置为ListItemGroupHeaderFooterStyle.NONE时无样式。 设置为ListItemGroupHeaderFooterStyle.FLOATING时，头部组件在滚动时悬浮显示。

**类型：** [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md)

**默认值：** ListItemGroupHeaderFooterStyle.NONE

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: number | string
```

列表项间距。只作用于ListItem与ListItem之间，不作用于header与ListItem、footer与ListItem之间。 默认值：0 单位：vp **说明：** 设置为负数或者大于等于List内容区长度时，按默认值显示。如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。

**类型：** number \| string

**默认值：** 0

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-space?: number | string--><!--Device-ListItemGroupOptions-space?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

列表项间距。只作用于ListItem与ListItem之间，不作用于header与ListItem、footer与ListItem之间。 默认值：0 单位：vp **说明：** 设置为负数或者大于等于List内容区长度时，按默认值显示。如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。

**类型：** Dimension

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-spaceWidth?: Dimension--><!--Device-ListItemGroupOptions-spaceWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ListItemGroupStyle
```

设置ListItemGroup组件卡片样式。 默认值：ListItemGroupStyle.NONE 设置为ListItemGroupStyle.NONE时无样式。 设置为ListItemGroupStyle.CARD时，建议配合ListItem的ListItemStyle.CARD同时使用，显示默认卡片样式。 卡片样式下，ListItemGroup默认规格：左右外边距12vp，上下左右内边距4vp。 卡片样式下，为卡片内的列表选项提供了默认的focused、hover、pressed、selected和disabled样式。 **说明：** 当设置为ListItemGroupStyle.CARD时，List的listDirection属性值须为Axis.Vertical，如果设置为Axis.Horizontal，会导致显示混乱；List属性 alignListItem默认为ListItemAlign.Center，居中对齐显示。

**类型：** [ListItemGroupStyle](arkts-arkui-listitemgroupstyle-e.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ListItemGroupOptions-style?: ListItemGroupStyle--><!--Device-ListItemGroupOptions-style?: ListItemGroupStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

