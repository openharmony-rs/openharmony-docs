# ListItemGroupOptions

ListItemGroup组件参数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ListItemGroupOptions--><!--Device-unnamed-export declare interface ListItemGroupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footer

```TypeScript
footer?: CustomBuilder
```

设置ListItemGroup尾部组件。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-footer?: CustomBuilder--><!--Device-ListItemGroupOptions-footer?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerComponent

```TypeScript
footerComponent?: ComponentContentBase
```

使用ComponentContent类型参数设置ListItemGroup尾部组件。

**类型：** ComponentContentBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-footerComponent?: ComponentContentBase--><!--Device-ListItemGroupOptions-footerComponent?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## footerStyle

```TypeScript
footerStyle?: ListItemGroupHeaderFooterStyle
```

设置ListItemGroup尾部样式。

**类型：** ListItemGroupHeaderFooterStyle

**默认值：** ListItemGroupHeaderFooterStyle.NONE

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-footerStyle?: ListItemGroupHeaderFooterStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## header

```TypeScript
header?: CustomBuilder
```

设置ListItemGroup头部组件。

**类型：** CustomBuilder

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-header?: CustomBuilder--><!--Device-ListItemGroupOptions-header?: CustomBuilder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## headerComponent

```TypeScript
headerComponent?: ComponentContentBase
```

使用ComponentContent类型参数设置ListItemGroup头部组件。

**类型：** ComponentContentBase

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-headerComponent?: ComponentContentBase--><!--Device-ListItemGroupOptions-headerComponent?: ComponentContentBase-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## headerStyle

```TypeScript
headerStyle?: ListItemGroupHeaderFooterStyle
```

设置ListItemGroup头部样式。

**类型：** ListItemGroupHeaderFooterStyle

**默认值：** ListItemGroupHeaderFooterStyle.NONE

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle--><!--Device-ListItemGroupOptions-headerStyle?: ListItemGroupHeaderFooterStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: double | string
```

列表项间距。只作用于ListItem与ListItem之间，不作用于header与ListItem、footer与ListItem之间。

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-space?: double | string--><!--Device-ListItemGroupOptions-space?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## spaceWidth

```TypeScript
spaceWidth?: Dimension
```

列表项间距。只作用于ListItem与ListItem之间，不作用于header与ListItem、footer与ListItem之间。 \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_说明：\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_ \_\_\_HTML\_TAG\_DESC\_USD\_3\_\_\_设置为负数或者大于等于List内容区长度时，按默认值显示。 \_\_\_HTML\_TAG\_DESC\_USD\_4\_\_\_如果同时设置了spaceWidth和space，则spaceWidth优先生效。当spaceWidth为undefined或null时，space生效。 \_\_\_HTML\_TAG\_DESC\_USD\_5\_\_\_。

**类型：** Dimension

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-spaceWidth?: Dimension--><!--Device-ListItemGroupOptions-spaceWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: ListItemGroupStyle
```

设置List组件卡片样式。

**类型：** ListItemGroupStyle

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ListItemGroupOptions-style?: ListItemGroupStyle--><!--Device-ListItemGroupOptions-style?: ListItemGroupStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

