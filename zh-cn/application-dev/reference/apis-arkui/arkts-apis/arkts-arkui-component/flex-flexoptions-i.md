# FlexOptions

设置Flex子组件的排列对齐方式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface FlexOptions--><!--Device-unnamed-export declare interface FlexOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: FlexAlign
```

当交叉轴存在额外空间时，多行内容之间的对齐方式。 仅在wrap为Wrap或WrapReverse下生效。

**类型：** FlexAlign

**默认值：** FlexAlign.Start

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-alignContent?: FlexAlign--><!--Device-FlexOptions-alignContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems?: ItemAlign
```

所有子组件在Flex容器交叉轴上的对齐格式。

**类型：** ItemAlign

**默认值：** ItemAlign.Start

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-alignItems?: ItemAlign--><!--Device-FlexOptions-alignItems?: ItemAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: FlexDirection
```

子组件在Flex容器上排列的方向，即主轴的方向。

**类型：** FlexDirection

**默认值：** FlexDirection.Row

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-direction?: FlexDirection--><!--Device-FlexOptions-direction?: FlexDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## justifyContent

```TypeScript
justifyContent?: FlexAlign
```

所有子组件在Flex容器主轴上的对齐格式。

**类型：** FlexAlign

**默认值：** FlexAlign.Start

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-justifyContent?: FlexAlign--><!--Device-FlexOptions-justifyContent?: FlexAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## space

```TypeScript
space?: FlexSpaceOptions
```

所有子组件在Flex容器主轴或交叉轴的间距。

**类型：** FlexSpaceOptions

**默认值：** {main: LengthMetrics.px(0), cross: LengthMetrics.px(0)}

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-space?: FlexSpaceOptions--><!--Device-FlexOptions-space?: FlexSpaceOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wrap

```TypeScript
wrap?: FlexWrap
```

Flex容器是单行/列还是多行/列排列。

**类型：** FlexWrap

**默认值：** FlexWrap.NoWrap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FlexOptions-wrap?: FlexWrap--><!--Device-FlexOptions-wrap?: FlexWrap-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

