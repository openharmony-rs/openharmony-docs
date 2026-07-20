# CustomSpanMeasureInfo

定义自定义绘制Span的测量信息接口。

**起始版本：** 12

<!--Device-unnamed-declare interface CustomSpanMeasureInfo--><!--Device-unnamed-declare interface CustomSpanMeasureInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number
```

设置文本字体大小。

单位：[fp](docroot://reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomSpanMeasureInfo-fontSize: number--><!--Device-CustomSpanMeasureInfo-fontSize: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## layoutPolicy

```TypeScript
layoutPolicy?: LayoutPolicy
```

自定义span所在父组件的宽度布局策略。

**说明：**

当值为null或undefined时，表示父组件没有设置宽度布局策略。

**类型：** LayoutPolicy

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomSpanMeasureInfo-layoutPolicy?: LayoutPolicy--><!--Device-CustomSpanMeasureInfo-layoutPolicy?: LayoutPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxWidth

```TypeScript
maxWidth?: number
```

自定义span所在父组件的内容区的最大宽度约束。

单位：[px](docroot://reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CustomSpanMeasureInfo-maxWidth?: number--><!--Device-CustomSpanMeasureInfo-maxWidth?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

