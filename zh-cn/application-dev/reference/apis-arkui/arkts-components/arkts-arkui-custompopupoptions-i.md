# CustomPopupOptions

弹出自定义气泡的信息。

**起始版本：** 8

<!--Device-unnamed-declare interface CustomPopupOptions--><!--Device-unnamed-declare interface CustomPopupOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowHeight

```TypeScript
arrowHeight?: Dimension
```

设置箭头高度。

默认值：8

单位：vp

**说明：**

不支持设置百分比。

**类型：** Dimension

**默认值：** 8.0_vp. [since 11 - 11]
@default 8.0_vp.
<p><strong>NOTE</strong>:
<br>This parameter cannot be set in percentage.
</p>
*

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-arrowHeight?: Dimension--><!--Device-CustomPopupOptions-arrowHeight?: Dimension-End-->

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

<!--Device-CustomPopupOptions-arrowOffset?: Length--><!--Device-CustomPopupOptions-arrowOffset?: Length-End-->

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

<!--Device-CustomPopupOptions-arrowPointPosition?: ArrowPointPosition--><!--Device-CustomPopupOptions-arrowPointPosition?: ArrowPointPosition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## arrowWidth

```TypeScript
arrowWidth?: Dimension
```

设置箭头宽度。若所设置的箭头宽度超过所在边的长度减去两倍的气泡圆角大小，则不绘制气泡箭头。

默认值：16

单位：vp

**说明：**

不支持设置百分比。

**类型：** Dimension

**默认值：** 16.0_vp. [since 11 - 11]
@default 16.0_vp.
<p><strong>NOTE</strong>:
<br>This parameter cannot be set in percentage.
</p> [since 12]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-arrowWidth?: Dimension--><!--Device-CustomPopupOptions-arrowWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoCancel

```TypeScript
autoCancel?: boolean
```

页面有操作时，气泡是否自动关闭。

true：自动关闭气泡；false：气泡不会自动关闭。

默认值：true

**说明：**

如果要实现点击气泡内消失需要在builder中先放一个布局组件，然后再将Popup高级组件放在布局组件里面，再在布局组件的onClick事件中修改控制显隐的状态变量show为false。

**类型：** boolean

**默认值：** true [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-autoCancel?: boolean--><!--Device-CustomPopupOptions-autoCancel?: boolean-End-->

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

<!--Device-CustomPopupOptions-avoidTarget?: AvoidanceMode--><!--Device-CustomPopupOptions-avoidTarget?: AvoidanceMode-End-->

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

<!--Device-CustomPopupOptions-backgroundBlurStyle?: BlurStyle--><!--Device-CustomPopupOptions-backgroundBlurStyle?: BlurStyle-End-->

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

<!--Device-CustomPopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions--><!--Device-CustomPopupOptions-backgroundBlurStyleOptions?: BackgroundBlurStyleOptions-End-->

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

<!--Device-CustomPopupOptions-backgroundEffect?: BackgroundEffectOptions--><!--Device-CustomPopupOptions-backgroundEffect?: BackgroundEffectOptions-End-->

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

<!--Device-CustomPopupOptions-borderLinearGradient?: PopupBorderLinearGradient--><!--Device-CustomPopupOptions-borderLinearGradient?: PopupBorderLinearGradient-End-->

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

<!--Device-CustomPopupOptions-borderWidth?: Dimension--><!--Device-CustomPopupOptions-borderWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder: CustomBuilder
```

提示气泡内容的构造器。

**说明：**

1. Popup为通用属性，自定义Popup中不支持再次弹出Popup。对builder下的第一层容器组件不支持使用position属性，如果使用将导致气泡不显示。2. builder中若使用自定义组件，自定义组件的aboutToAppear和aboutToDisappear生命周期与Popup气泡的显隐无关，不能使用其生命周期判断Popup气泡的显隐。3. 该构造器的builder仅支持定义在UI组件中，例如可以定义在Builder函数、方法或者[build](docroot://reference/apis-arkui/arkui-ts/ts-custom-component-lifecycle.md#build)方法里。

**类型：** CustomBuilder

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-builder: CustomBuilder--><!--Device-CustomPopupOptions-builder: CustomBuilder-End-->

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

<!--Device-CustomPopupOptions-colorMode?: AnchoredColorMode--><!--Device-CustomPopupOptions-colorMode?: AnchoredColorMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableArrow

```TypeScript
enableArrow?: boolean
```

是否显示箭头。

true：显示箭头；false：不显示箭头。

从API version 9开始，如果箭头所在方位侧的气泡长度不足以显示下箭头，则会默认不显示箭头。比如：placement设置为Left，此时如果气泡高度小于箭头的宽度（32vp）与气泡圆角两倍（48vp）之和（80vp），则实际不会显示箭头。

默认值：true

**类型：** boolean

**默认值：** true [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-enableArrow?: boolean--><!--Device-CustomPopupOptions-enableArrow?: boolean-End-->

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

<!--Device-CustomPopupOptions-enableHoverMode?: boolean--><!--Device-CustomPopupOptions-enableHoverMode?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## focusable

```TypeScript
focusable?: boolean
```

设置气泡弹出后是否获焦。

true：气泡可以获焦；false：气泡不会获焦。

默认值：false

**类型：** boolean

**默认值：** true [since 11 - 11]
@default false [since 12]

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-focusable?: boolean--><!--Device-CustomPopupOptions-focusable?: boolean-End-->

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

<!--Device-CustomPopupOptions-followTransformOfTarget?: boolean--><!--Device-CustomPopupOptions-followTransformOfTarget?: boolean-End-->

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

<!--Device-CustomPopupOptions-keyboardAvoidMode?: KeyboardAvoidMode--><!--Device-CustomPopupOptions-keyboardAvoidMode?: KeyboardAvoidMode-End-->

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

<!--Device-CustomPopupOptions-levelMode?: LevelMode--><!--Device-CustomPopupOptions-levelMode?: LevelMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean | { color: ResourceColor }
```

设置气泡是否有遮罩层及遮罩颜色。如果设置为false，则没有遮罩层；如果设置为true，则设置有遮罩层并且颜色为透明色；如果设置为Color，则为遮罩层的颜色。默认值：true

**类型：** boolean \| { color: ResourceColor }

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-mask?: boolean | { color: ResourceColor }--><!--Device-CustomPopupOptions-mask?: boolean | { color: ResourceColor }-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maskColor

```TypeScript
maskColor?: Color | string | Resource | number
```

设置气泡遮罩层颜色。

**说明：**

从 API version 10 开始废弃，建议使用`mask`替代。

**类型：** Color \| string \| Resource \| number

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [mask](arkts-arkui-custompopupoptions-i.md#mask)

<!--Device-CustomPopupOptions-maskColor?: Color | string | Resource | number--><!--Device-CustomPopupOptions-maskColor?: Color | string | Resource | number-End-->

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

<!--Device-CustomPopupOptions-offset?: Position--><!--Device-CustomPopupOptions-offset?: Position-End-->

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

气泡状态变化事件回调，参数为气泡的显示状态。返回true时，表示气泡从关闭到打开，返回false时，表示气泡从打开到关闭。

**类型：** (event: {     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @since 10      */     /**      * is Visible.      *      * @type { boolean }      * @syscap SystemCapability.ArkUI.ArkUI.Full      * @stagemodelonly      * @crossplatform      * @atomicservice      * @since 11      */     isVisible: boolean   }) =&gt; void

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-onStateChange?: (event: {
    /**
     * is Visible.
     *
     ******/
    /**
     * is Visible.
     *
     *******/
    isVisible: boolean
  }) => void--><!--Device-CustomPopupOptions-onStateChange?: (event: {
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

**默认值：** true

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>--><!--Device-CustomPopupOptions-onWillDismiss?: boolean | Callback<DismissPopupAction>-End-->

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

<!--Device-CustomPopupOptions-outlineLinearGradient?: PopupBorderLinearGradient--><!--Device-CustomPopupOptions-outlineLinearGradient?: PopupBorderLinearGradient-End-->

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

<!--Device-CustomPopupOptions-outlineWidth?: Dimension--><!--Device-CustomPopupOptions-outlineWidth?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## placement

```TypeScript
placement?: Placement
```

气泡组件优先显示的位置，当前位置显示不下时，会自动调整位置。

默认值：Placement.Bottom

**类型：** Placement

**默认值：** Placement.Bottom

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-placement?: Placement--><!--Device-CustomPopupOptions-placement?: Placement-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## popupColor

```TypeScript
popupColor?: Color | string | Resource | number
```

气泡的颜色。如需去除模糊背景填充效果，需将backgroundBlurStyle设置为BlurStyle.NONE。

API version 10，默认值：'#4d4d4d'

API version 11及以后，默认值：透明色[TRANSPARENT](../../apis-arkgraphics3d/arkts-apis/arkts-arkgraphics3d-scenetypes-color-i.md)加模糊背景填充效果[COMPONENT_ULTRA_THICK](arkts-arkui-blurstyle-e.md)

**类型：** Color \| string \| Resource \| number

**默认值：** '#4d4d4d' [since 10 - 10]
@default TRANSPARENT plus COMPONENT_ULTRA_THICK [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-popupColor?: Color | string | Resource | number--><!--Device-CustomPopupOptions-popupColor?: Color | string | Resource | number-End-->

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

<!--Device-CustomPopupOptions-radius?: Dimension--><!--Device-CustomPopupOptions-radius?: Dimension-End-->

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

<!--Device-CustomPopupOptions-shadow?: ShadowOptions | ShadowStyle--><!--Device-CustomPopupOptions-shadow?: ShadowOptions | ShadowStyle-End-->

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

<!--Device-CustomPopupOptions-showInSubWindow?: boolean--><!--Device-CustomPopupOptions-showInSubWindow?: boolean-End-->

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

<!--Device-CustomPopupOptions-systemMaterial?: SystemUiMaterial--><!--Device-CustomPopupOptions-systemMaterial?: SystemUiMaterial-End-->

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

<!--Device-CustomPopupOptions-targetSpace?: Length--><!--Device-CustomPopupOptions-targetSpace?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition?: TransitionEffect
```

自定义设置Popup气泡显示和退出的动画效果。

**说明：**

1. 如果不设置，则使用默认的显示/退出动效。2. 显示动效中按back键，打断显示动效，执行退出动效，动画效果为显示动效与退出动效的曲线叠加后的效果。3. 退出动效中按back键，不会打断退出动效，退出动效继续执行，back键不被响应。

**类型：** TransitionEffect

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CustomPopupOptions-transition?: TransitionEffect--><!--Device-CustomPopupOptions-transition?: TransitionEffect-End-->

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

<!--Device-CustomPopupOptions-width?: Dimension--><!--Device-CustomPopupOptions-width?: Dimension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

