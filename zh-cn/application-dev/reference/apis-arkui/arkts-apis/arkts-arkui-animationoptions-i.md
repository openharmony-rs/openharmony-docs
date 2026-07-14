# AnimationOptions

动画播放参数。包括播放时延，迭代次数，单帧播放时间，是否自动播放。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## autoPlay

```TypeScript
autoPlay?: boolean
```

设置动图是否自动播放。

true表示自动播放，false表示不自动播放。

默认值为true。

**类型：** boolean

**默认值：** true

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

设置图片数组播放总时间。

PixelMap数组的默认值是每张图片播放1秒。本地图片或者应用资源的默认值是图片资源中携带的播放时延。

单位：毫秒

取值范围：[0, +∞)

设置负数取默认值。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## frameDurations

```TypeScript
frameDurations?: Array<number>
```

设置动图中的单帧播放时间。不设置则按照总时间播放。

设置的优先级高于duration，即同时设置了duration和frameDurations时，duration不生效。

当设置的frameDurations长度与图片的数量不一致时，按照总时间播放。

单位：毫秒

**类型：** Array<number>

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

设置图片数组播放次数。

值为-1时表示无限播放，值为0时表示不播放，值大于0时表示有限的播放次数。

默认值为1。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## stopMode

```TypeScript
stopMode?: AnimationStopMode
```

设置动图的停止模式。

默认值：AnimationStopMode.FIRST_FRAME，表示动图停止时回到首帧。

**类型：** AnimationStopMode

**默认值：** AnimationStopMode.FIRST_FRAME

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

