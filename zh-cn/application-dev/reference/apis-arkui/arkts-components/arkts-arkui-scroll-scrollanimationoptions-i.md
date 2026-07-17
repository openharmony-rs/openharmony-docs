# ScrollAnimationOptions

自定义滚动动画的参数。

**起始版本：** 12

<!--Device-unnamed-declare interface ScrollAnimationOptions--><!--Device-unnamed-declare interface ScrollAnimationOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canOverScroll

```TypeScript
canOverScroll?: boolean
```

是否启用过滚动。

<p><strong>说明</strong><br> 设置为<em>true</em>时可以滚动超出边界并触发回弹动画，同时组件的<em>edgeEffect</em>属性需设置为EdgeEffect.Spring。</p>

**类型：** boolean

**默认值：** false

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-canOverScroll?: boolean--><!--Device-ScrollAnimationOptions-canOverScroll?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

滚动曲线。

**类型：** Curve | ICurve

**默认值：** Curve.Ease

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-curve?: Curve | ICurve--><!--Device-ScrollAnimationOptions-curve?: Curve | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

滚动时长。

<p><strong>说明</strong><br>设置为小于0的值时，按默认值处理。</p>

**类型：** number

**默认值：** 1000

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ScrollAnimationOptions-duration?: number--><!--Device-ScrollAnimationOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

