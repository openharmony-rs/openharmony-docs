# ScaleOptions

定义缩放选项。

> **说明：** 
> 
> 当组件同时设置了[rotate](arkts-arkui-commonmethod-c.md#rotate)和
> [scale](arkts-arkui-commonmethod-c.md#scale)属性时，centerX和centerY的取值会发生冲突，此时centerX和centerY的值以属性链中后设置的属性值为
> 准。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerX

```TypeScript
centerX?: number | string
```

变换中心点x轴坐标。表示组件变换中心点（即锚点）的x方向坐标。类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。取值示例：'50'、'50%'。取值范围：(-∞, +∞)。默认值：'50 %'。

单位：vp

**类型：** number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## centerY

```TypeScript
centerY?: number | string
```

变换中心点y轴坐标。表示组件变换中心点（即锚点）的y方向坐标。类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。取值示例：'50'、'50%'。取值范围：(-∞, +∞)。默认值：'50 %'。

单位：vp

**类型：** number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number
```

x轴的缩放倍数。取值范围：(-∞, +∞)。默认值：1。x=1时表示无缩放效果，x&gt;1时以x轴方向放大，0&lt;x&lt;1时以x轴方向缩小，x=0时组件在x轴方向不可见，x&lt;0时沿x轴反向并缩放。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number
```

y轴的缩放倍数。取值范围：(-∞, +∞)。默认值：1。y=1时表示无缩放效果，y&gt;1时以y轴方向放大，0&lt;y&lt;1时以y轴方向缩小，y=0时组件在y轴方向不可见，y&lt;0时沿y轴反向并缩放。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number
```

z轴的缩放倍数。取值范围：(-∞, +∞)。默认值：1。z=1时表示无缩放效果，z&gt;1时以z轴方向放大，0&lt;z&lt;1时以z轴方向缩小，z=0时组件在z轴方向不可见，z&lt;0时沿z轴反向并缩放。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
