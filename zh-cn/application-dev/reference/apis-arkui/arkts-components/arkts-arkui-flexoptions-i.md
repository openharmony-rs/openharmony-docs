# FlexOptions

设置Flex子组件的排列对齐方式。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

<!--Device-unnamed-declare interface FlexOptions--><!--Device-unnamed-declare interface FlexOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: FlexAlign
```

当交叉轴存在额外空间时，多行内容之间的对齐方式。仅在wrap为Wrap或WrapReverse下生效。 默认值：FlexAlign.Start 异常值按默认值处理。 取值包括： - Start：首端对齐。 - Center：居中对齐。 - End：尾端对齐。 - SpaceBetween：两端对齐，行与行之间间距相等。 - SpaceAround：每行两侧间距相等。 - SpaceEvenly：行与行之间及两端间距完全相等。

**类型：** FlexAlign

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexOptions-alignContent?: FlexAlign--><!--Device-FlexOptions-alignContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: ItemAlign
```

所有子组件在Flex容器交叉轴上的对齐格式。设置后，子组件将按照指定的对齐方式在交叉轴方向上定位。 默认值：ItemAlign.Start 异常值按默认值处理。 取值包括： - Auto：使用父容器的对齐方式。 - Start：首部对齐。 - Center：居中对齐。 - End：尾部对齐。 - Stretch：拉伸填充。 - Baseline：基线对齐。

**类型：** ItemAlign

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexOptions-alignItems?: ItemAlign--><!--Device-FlexOptions-alignItems?: ItemAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: FlexDirection
```

子组件在Flex容器上排列的方向，即主轴的方向。设置后，子组件将按照指定的方向在主轴上依次排列。 默认值：FlexDirection.Row 异常值按默认值处理。 取值包括： - Row：主轴为水平方向，起点在左端。 - RowReverse：主轴为水平方向，起点在右端。 - Column：主轴为垂直方向，起点在上端。 - ColumnReverse：主轴为垂直方向，起点在下端。 Row和RowReverse的起点位置受容器的direction属性影响。

**类型：** FlexDirection

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexOptions-direction?: FlexDirection--><!--Device-FlexOptions-direction?: FlexDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在Flex容器主轴上的对齐格式。设置后，子组件将按照指定的对齐方式在主轴方向上分布和排列。 默认值：FlexAlign.Start 异常值按默认值处理。 取值包括： - Start：首端对齐。 - Center：居中对齐。 - End：尾端对齐。 - SpaceBetween：两端对齐，子组件之间间距相等。 - SpaceAround：子组件两侧间距相等。 - SpaceEvenly：子组件之间及两端间距完全相等。 **说明：** 当justifyContent设置为SpaceBetween、SpaceAround、SpaceEvenly时，space参数不生效。

**类型：** FlexAlign

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexOptions-justifyContent?: FlexAlign--><!--Device-FlexOptions-justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: FlexSpaceOptions
```

设置Flex容器子组件在主轴和交叉轴上的间距，包含main和cross两个属性。当需要调整子组件之间的间距时传入此参数，不传入时子组件之间无间距。 默认值：{main: LengthMetrics.px(0), cross: LengthMetrics.px(0)} 非法值：按默认值处理。 当space.main或space.cross的值为负数，或者justifyContent设置为FlexAlign.SpaceBetween、FlexAlign.SpaceAround、FlexAlign.SpaceEvenly 时，space参数不生效。其中main属性在单行或多行布局时均生效，cross属性仅在wrap为Wrap或WrapReverse（多行布局）时生效。

**类型：** [FlexSpaceOptions](arkts-arkui-flexspaceoptions-i.md)

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-FlexOptions-space?: FlexSpaceOptions--><!--Device-FlexOptions-space?: FlexSpaceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wrap

```TypeScript
wrap?: FlexWrap
```

Flex容器是单行/列还是多行/列排列。设置后，子组件将在容器中按指定的换行方式进行布局。 默认值：FlexWrap.NoWrap 异常值按默认值处理。 取值包括： - NoWrap：不换行，子组件总宽度超过容器宽度时被截断。 - Wrap：换行，第一行在上方。 - WrapReverse：换行，第一行在下方。 **说明：** 在多行布局时，通过交叉轴方向，确认新行堆叠方向。

**类型：** FlexWrap

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexOptions-wrap?: FlexWrap--><!--Device-FlexOptions-wrap?: FlexWrap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

