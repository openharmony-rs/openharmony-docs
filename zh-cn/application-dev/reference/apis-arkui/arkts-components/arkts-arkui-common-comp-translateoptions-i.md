# TranslateOptions

```TypeScript
declare interface TranslateOptions
```

定义平移选项。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: number | string
```

x轴的平移距离。

类型为number时，单位为vp，取值范围为(-∞, +∞)。

默认值：0

类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。

**类型：** number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: number | string
```

y轴的平移距离。

类型为number时，单位为vp，取值范围为(-∞, +∞)。

默认值：0

类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。

**类型：** number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## z

```TypeScript
z?: number | string
```

z轴的平移距离。z轴方向移动时由于观察点位置不变，z的值接近观察点组件会有放大效果，远离则缩小。

类型为number时，单位为vp，取值范围为(-∞, +∞)。

默认值：0

类型为string时，形式参考[Length](../arkts-apis/arkts-arkui-length-t.md)的string类型。

**类型：** number &#124; string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
