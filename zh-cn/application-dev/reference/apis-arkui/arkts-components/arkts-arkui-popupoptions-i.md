# PopupOptions

基础气泡的信息。

**起始版本：** 7

<!--Device-unnamed-declare interface PopupOptions--><!--Device-unnamed-declare interface PopupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

设置气泡箭头高度。

默认值：8

单位：vp

**说明：**

不支持设置百分比。

**类型：** Dimension

**默认值：** 8.0_vp.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-arrowHeight?: Dimension--><!--Device-PopupOptions-arrowHeight?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowOffset

```TypeScript
arrowOffset?: Length
```

Popup箭头在气泡处的偏移。

箭头在气泡上下方时，数值为0表示箭头居最左侧，偏移量为箭头至最左侧的距离，默认居中。

箭头在气泡左右侧时，偏移量为箭头至最上侧的距离，默认居中。

显示在屏幕边缘时，气泡会自动左右偏移，数值为0时箭头始终指向绑定组件。

单位：vp

**说明：**

1. 没设置arrowOffset的情况下，气泡箭头与四个角的距离不能小于圆角半径。2. 只有arrowPointPosition不设置或者设置为null、undefined时，arrowOffset属性才生效。3. 不支持设置百分比。

**类型：** Length

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-arrowOffset?: Length--><!--Device-PopupOptions-arrowOffset?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowPointPosition

```TypeScript
arrowPointPosition?: ArrowPointPosition
```

气泡箭头相对于父组件显示位置，气泡箭头在垂直和水平方向上有Start、Center、End三个位置点可选。以上所有位置点均位于父组件区域的范围内，不会超出父组件的边界范围。

默认值：ArrowPointPosition.CENTER

**类型：** ArrowPointPosition

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-arrowPointPosition?: ArrowPointPosition--><!--Device-PopupOptions-arrowPointPosition?: ArrowPointPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

设置气泡箭头宽度。若所设置的宽度超过所在边的长度减去两倍的气泡圆角大小，则不绘制气泡箭头。

默认值：16

单位：vp

**说明：**

不支持设置百分比。

**类型：** Dimension

**默认值：** 16.0_vp.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-arrowWidth?: Dimension--><!--Device-PopupOptions-arrowWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

页面有操作时，气泡是否自动关闭。

true：自动关闭气泡；false：气泡不会自动关闭。

默认值：true

**类型：** boolean

**默认值：** true

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-autoCancel?: boolean--><!--Device-PopupOptions-autoCancel?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## avoidTarget

```TypeScript
avoidTarget?: AvoidanceMode
```

设置Popup避让时是否覆盖指向组件。

默认值：AvoidanceMode.COVER_TARGET

**类型：** AvoidanceMode

**默认值：** AvoidanceMode.COVER_TARGET

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-avoidTarget?: AvoidanceMode--><!--Device-PopupOptions-avoidTarget?: AvoidanceMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyle

```TypeScript
backgroundBlurStyle?: BlurStyle
```

设置气泡模糊背景参数。

默认值：BlurStyle.COMPONENT_ULTRA_THICK

**类型：** BlurStyle

**默认值：** BlurStyle.COMPONENT_ULTRA_THICK

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-backgroundBlurStyle?: BlurStyle--><!--Device-PopupOptions-backgroundBlurStyle?: BlurStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundBlurStyleOptions

```TypeScript
backgroundBlurStyleOptions?: BackgroundBlurStyleOptions
```

定义Popup的背景模糊样式选项。

**类型：** BackgroundBlurStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-PopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## backgroundEffect

```TypeScript
backgroundEffect?: BackgroundEffectOptions
```

定义Popup的背景效果选项。

**类型：** BackgroundEffectOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-PopupOptions-backgroundEffect?: BackgroundEffectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderLinearGradient

```TypeScript
borderLinearGradient?: PopupBorderLinearGradient
```

设置Popup组件内描边线性渐变的颜色。

**说明：**

1. borderLinearGradient不设置或者设置为null、undefined时，内描边没有线性渐变效果。2. borderLinearGradient设置时，direction默认值是：GradientDirection.Bottom。

**类型：** PopupBorderLinearGradient

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-borderLinearGradient?: PopupBorderLinearGradient--><!--Device-PopupOptions-borderLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Dimension
```

设置Popup组件内描边的宽度。

默认值：1

单位：vp

**说明：**

1. 不支持设置百分比，设置百分比时按0处理。2. 在没有设置Popup组件内描边的情况下，该接口需要和borderLinearGradient配合使用。3. 当设置双描边时，建议内描边宽度不超过10vp。

**类型：** Dimension

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-borderWidth?: Dimension--><!--Device-PopupOptions-borderWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: AnchoredColorMode
```

设置气泡深浅色模式，默认跟随绑定组件深浅色模式。

默认值：AnchoredColorMode.FOLLOW_TARGET

**说明：**

1. 仅当绑定组件使用了[WithTheme](docroot://reference/apis-arkui/arkui-ts/ts-container-with-theme.md#接口)标签时，该属性才会生效。2. 该属性仅影响组件的默认样式，以及开发者设置的涉及深浅色资源的属性。3. 设置为AnchoredColorMode.FOLLOW_SYSTEM时，模糊材质可以跟随，文字颜色以及涉及深浅色资源的属性仍保持跟随绑定组件的深浅色配置。

**类型：** AnchoredColorMode

**默认值：** AnchoredColorMode.FOLLOW_TARGET

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-PopupOptions-colorMode?: AnchoredColorMode--><!--Device-PopupOptions-colorMode?: AnchoredColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

设置是否显示箭头。

true：显示箭头；false：不显示箭头。

默认值：true

**说明：**

当页面可用空间无法让气泡完全避让时，气泡会覆盖到组件上并且不显示箭头。

**类型：** boolean

**默认值：** true

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-enableArrow?: boolean--><!--Device-PopupOptions-enableArrow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableHoverMode

```TypeScript
enableHoverMode?: boolean
```

Popup组件是否响应悬停态（半折叠状态）变化，即在悬停态下是否触发避让折痕区域。

默认值：false，2in1设备默认为true。未设置或者值为非法值时，生效默认值。

**说明：**

1. 如果Popup的弹出位置在悬停态折痕区域，Popup组件不会响应悬停态。2. 2in1设备从API version 20开始生效。3. 2in1设备仅在窗口瀑布模式下生效。

**类型：** boolean

**默认值：** false

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-enableHoverMode?: boolean--><!--Device-PopupOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## followTransformOfTarget

```TypeScript
followTransformOfTarget?: boolean
```

气泡绑定的宿主组件或其宿主组件的父容器添加了旋转、缩放等变换时，气泡是否跟随宿主组件变换。

true：气泡可以拿到变换后宿主的位置，显示到相应位置；false：气泡拿不到宿主变换后的位置，可能显示异常。

默认值：false

**类型：** boolean

**默认值：** false

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-followTransformOfTarget?: boolean--><!--Device-PopupOptions-followTransformOfTarget?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## keyboardAvoidMode

```TypeScript
keyboardAvoidMode?: KeyboardAvoidMode
```

气泡是否避让软键盘，默认不避让。设置为避让后，气泡显示空间不足时，由原先居中覆盖父组件的方式改为平移覆盖父组件，且气泡箭头不指向宿主时，不再显示箭头。

默认值：KeyboardAvoidMode.NONE

**类型：** KeyboardAvoidMode

**默认值：** KeyboardAvoidMode.NONE

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-PopupOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## levelMode

```TypeScript
levelMode?: LevelMode
```

设置气泡的显示层级模式。

默认值：LevelMode.OVERLAY

**类型：** LevelMode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-levelMode?: LevelMode--><!--Device-PopupOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | { color: ResourceColor }
```

设置气泡是否有遮罩层及遮罩颜色。

true：显示透明色遮罩层；false：不显示遮罩层。

Color：显示指定颜色的遮罩层。

默认值：true

**类型：** boolean \| { color: ResourceColor }

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-mask?: boolean | { color: ResourceColor }--><!--Device-PopupOptions-mask?: boolean | { color: ResourceColor }-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## message

```TypeScript
message: string
```

气泡信息内容。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-message: string--><!--Device-PopupOptions-message: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## messageOptions

```TypeScript
messageOptions?: PopupMessageOptions
```

设置气泡信息文本参数。

**类型：** PopupMessageOptions

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-messageOptions?: PopupMessageOptions--><!--Device-PopupOptions-messageOptions?: PopupMessageOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: Position
```

设置Popup组件相对于placement设置的显示位置的偏移。

默认值：{ x: 0, y: 0 }

单位：vp

**说明：**

不支持设置百分比。

**类型：** Position

**默认值：** { x: 0, y: 0 } [since 11]

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-offset?: Position--><!--Device-PopupOptions-offset?: Position-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onStateChange

```TypeScript
onStateChange?: (event: {
    /**
     * is Visible.
     *
     ******/
    /**
     * is Visible.
     *
     *******/
    isVisible: boolean
  }) => void
```

气泡状态变化事件回调，参数isVisible为气泡的显示状态。返回true时，表示气泡从关闭到打开，返回false时，表示气泡从打开到关闭。

**类型：** (event: {     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @since 10      */     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @atomicservice      * @since 11      */     isVisible: boolean   }) =&gt; void

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-onStateChange?: (event: {
    /**
     * is Visible.
     *
     ******/
    /**
     * is Visible.
     *
     *******/
    isVisible: boolean
  }) => void--><!--Device-PopupOptions-onStateChange?: (event: {
    /**
     * is Visible.
     *
     ******/
    /**
     * is Visible.
     *
     *******/
    isVisible: boolean
  }) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onWillDismiss

```TypeScript
onWillDismiss?: boolean | Callback<DismissPopupAction>
```

设置Popup交互式关闭拦截开关及拦截回调函数，默认值为true，Popup响应点击、侧滑（左滑/右滑）、三键back。

1. 当为boolean类型时，如果设置为false，则不响应点击、侧滑（左滑/右滑）、三键back、路由跳转或键盘ESC退出事件，仅当设置“气泡显示状态”参数show值为false时才退出；如果设置为true，则正常响应退出事件；2. 如果设置为函数类型，则拦截退出事件且执行回调函数。侧滑（左滑/右滑）、三键back、路由跳转或键盘ESC在回调函数中返回的reason为PRESS_BACK，点击为TOUCH_OUTSIDE。

**说明：**

在onWillDismiss回调中，不能再做onWillDismiss拦截。

**类型：** boolean \| Callback&lt;DismissPopupAction&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>--><!--Device-PopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineLinearGradient

```TypeScript
outlineLinearGradient?: PopupBorderLinearGradient
```

设置Popup组件外描边线性渐变的颜色。

**说明：**

1. outlineLinearGradient不设置或者设置为null、undefined时，外描边没有线性渐变效果。2. outlineLinearGradient设置时，direction默认值是：GradientDirection.Bottom。

**类型：** PopupBorderLinearGradient

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-outlineLinearGradient?: PopupBorderLinearGradient--><!--Device-PopupOptions-outlineLinearGradient?: PopupBorderLinearGradient-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outlineWidth

```TypeScript
outlineWidth?: Dimension
```

设置Popup组件外描边的宽度。

默认值：1

单位：vp

**说明：**

1. 不支持设置百分比，设置百分比时按0处理。2. 在没有设置Popup组件外描边的情况下，该接口需要和outlineLinearGradient配合使用。3. 当设置双描边时，建议外描边宽度不超过10vp。

**类型：** Dimension

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-outlineWidth?: Dimension--><!--Device-PopupOptions-outlineWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

设置Popup组件相对于宿主节点的显示位置，默认值为Placement.Bottom。

如果同时设置了`placementOnTop`和`placement`，则以`placement`的设置为准。如果开发者设置的位置上无法完整显示气泡，气泡会自动避让至可以完整显示的位置

**类型：** Placement

**默认值：** Placement.Bottom

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-placement?: Placement--><!--Device-PopupOptions-placement?: Placement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placementOnTop

```TypeScript
placementOnTop?: boolean
```

是否在组件上方显示，默认值为false。取值为true：气泡显示到绑定组件的上方，取值false：气泡显示到绑定组件的下方。

**说明：**

从API version 7开始支持，从API version 10开始废弃，建议使用`placement`替代。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [placement](arkts-arkui-popupoptions-i.md#placement)

<!--Device-PopupOptions-placementOnTop?: boolean--><!--Device-PopupOptions-placementOnTop?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: Color | string | Resource | number
```

气泡的颜色。如需去除模糊背景填充效果，需将backgroundBlurStyle设置为BlurStyle.NONE。

默认值：透明色[TRANSPARENT](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md)加模糊背景填充效果[COMPONENT_ULTRA_THICK](arkts-arkui-blurstyle-e.md)。

**类型：** Color \| string \| Resource \| number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-popupColor?: Color | string | Resource | number--><!--Device-PopupOptions-popupColor?: Color | string | Resource | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## primaryButton

```TypeScript
primaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }
```

第一个按钮。

value：气泡里主按钮的文本。

action：点击主按钮的回调函数。

**类型：** {     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @since 10      */     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @atomicservice      * @since 11      */     value: string;      /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @since 10      */     /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @atomicservice      * @since 11      */     action: () =&gt; void;   }

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-primaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }--><!--Device-PopupOptions-primaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Dimension
```

设置气泡圆角半径。

默认值：20

单位：vp

**类型：** Dimension

**默认值：** 20.0_vp.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-radius?: Dimension--><!--Device-PopupOptions-radius?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## secondaryButton

```TypeScript
secondaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }
```

第二个按钮。

value：气泡里辅助按钮的文本。

action：点击辅助按钮的回调函数。

**类型：** {     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @since 10      */     /**      * Button text value      *      * @type { string }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @atomicservice      * @since 11      */     value: string;      /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @since 7      */     /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @since 10      */     /**      * action      *      * @type { function }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @crossplatform      * @atomicservice      * @since 11      */     action: () =&gt; void;   }

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-secondaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }--><!--Device-PopupOptions-secondaryButton?: {
    /**
     * Button text value
     *
     ****/
    /**
     * Button text value
     *
     *****/
    /**
     * Button text value
     *
     ******/
    value: string;

    /**
     * action
     *
     ****/
    /**
     * action
     *
     *****/
    /**
     * action
     *
     ******/
    action: () => void;
  }-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shadow

```TypeScript
shadow?: ShadowOptions | ShadowStyle
```

设置气泡阴影。

默认值：ShadowStyle.OUTER_DEFAULT_MD

**类型：** ShadowOptions \| ShadowStyle

**默认值：** ShadowStyle.OUTER_DEFAULT_MD.

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-PopupOptions-shadow?: ShadowOptions | ShadowStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showInSubWindow

```TypeScript
showInSubWindow?: boolean
```

气泡是否显示在创建的子窗里。

true：气泡会显示在创建的子窗里；false：气泡会显示在对应的主窗中。

默认值：false

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-showInSubWindow?: boolean--><!--Device-PopupOptions-showInSubWindow?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## systemMaterial

```TypeScript
systemMaterial?: SystemUiMaterial
```

设置组件的系统材质。

默认值：undefined，会清除由该接口设置的材质效果。

**说明：**

不同系统材质对应不同的属性影响效果，该接口影响背景色[backgroundColor](arkts-arkui-commonmethod-c.md#backgroundcolor-1)、边框颜色[borderColor](arkts-arkui-commonmethod-c.md#bordercolor-1)、边框宽度[borderWidth](arkts-arkui-commonmethod-c.md#borderwidth-1)、阴影[shadow](arkts-arkui-commonmethod-c.md#shadow-1)，不建议与上述接口一起使用。

**类型：** SystemUiMaterial

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-systemMaterial?: SystemUiMaterial--><!--Device-PopupOptions-systemMaterial?: SystemUiMaterial-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## targetSpace

```TypeScript
targetSpace?: Length
```

设置Popup与宿主节点的间距。不支持设置百分比。

默认值：8

单位：vp

**类型：** Length

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-targetSpace?: Length--><!--Device-PopupOptions-targetSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

自定义设置Popup气泡显示和退出的动画效果。

**说明：**

1. 不设置时使用默认的显示/退出动效。2. 显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。3. 退出动效中按back键，不会打断退出动效，back键不被响应。

**类型：** TransitionEffect

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-transition?: TransitionEffect--><!--Device-PopupOptions-transition?: TransitionEffect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Dimension
```

气泡宽度，未设置或者异常值场景下，气泡自适应内容宽度。

单位：vp

**类型：** Dimension

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PopupOptions-width?: Dimension--><!--Device-PopupOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

