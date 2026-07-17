# BorderImageOption

Border image option

**起始版本：** 11

<!--Device-unnamed-declare interface BorderImageOption--><!--Device-unnamed-declare interface BorderImageOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fill

```TypeScript
fill?: boolean
```

Whether to fill the center of the border image.true: Fill the center of the border image.false: Do not fill the center of the border image.

**类型：** boolean

**默认值：** false

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-fill?: boolean--><!--Device-BorderImageOption-fill?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outset

```TypeScript
outset?: Length | EdgeWidths | LocalizedEdgeWidths
```

Amount by which the border image is extended beyond the border box.

**类型：** Length | EdgeWidths | LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-outset?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat?: RepeatMode
```

Repeat mode of the source image's slices on the border.

**类型：** RepeatMode

**默认值：** RepeatMode.Stretch

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-repeat?: RepeatMode--><!--Device-BorderImageOption-repeat?: RepeatMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## slice

```TypeScript
slice?: Length | EdgeWidths | LocalizedEdgeWidths
```

Slice width of the upper left corner, upper right corner, lower left corner,and lower right corner of the border image.

**类型：** Length | EdgeWidths | LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-slice?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## source

```TypeScript
source?: string | Resource | LinearGradient
```

Source or gradient color of the border image.When the type is string, this parameter sets the border image source.For details about how to reference image resources, see Loading Image Resources.

<p><strong>NOTE</strong>:<br>The border image source applies only to container components, such as Row, Column, and Flex.</p>

**类型：** string | Resource | LinearGradient

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-source?: string | Resource | LinearGradient--><!--Device-BorderImageOption-source?: string | Resource | LinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length | EdgeWidths | LocalizedEdgeWidths
```

Width of the border image.

**类型：** Length | EdgeWidths | LocalizedEdgeWidths

**默认值：** 0

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths--><!--Device-BorderImageOption-width?: Length | EdgeWidths | LocalizedEdgeWidths-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

