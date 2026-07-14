# UnionEffectContainerOptions（系统接口）

设置UnionEffectContainer构造参数。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## spacing

```TypeScript
spacing?: number
```

spacing表示后代组件发生融合形变的程度。它不代表实际的间距，只有设置了使用祖先组件UnionEffectContainer融合效果的后代组件且后代组件靠近到一定程度时才会发生融合。

**说明：**

设置的spacing大于0，且设置了祖先组件UnionEffectContainer融合效果的后代组件彼此靠近到一定程度，这些后代组件会开始相互融合形变，且随着距离的变近融合形变的效果越强。该值越大，后代组件彼此靠近时，它们的
融合会越早开始，越容易发生融合形变。

默认值：0，此时子组件形状会融合在一起，但不会有形变效果。

取值范围：[0, +∞)。小于0时按0处理。

**类型：** number

**默认值：** 0

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

