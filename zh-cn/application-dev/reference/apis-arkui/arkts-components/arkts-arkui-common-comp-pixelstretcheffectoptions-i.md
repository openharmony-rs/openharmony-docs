# PixelStretchEffectOptions

```TypeScript
declare interface PixelStretchEffectOptions
```

像素扩展属性集合，用于描述像素扩展的信息。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom?: Length
```

组件图像下边沿像素扩展距离。需与left、right、top方向保持一致：四个方向的扩展统一为非正值或者非负值，不支持百分比和具体值混用。

默认值：0vp

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: Length
```

组件图像左边沿像素扩展距离。需与right、top、bottom方向保持一致：四个方向的扩展统一为非正值或者非负值，不支持百分比和具体值混用。

默认值：0vp

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: Length
```

组件图像右边沿像素扩展距离。需与left、top、bottom方向保持一致：四个方向的扩展统一为非正值或者非负值，不支持百分比和具体值混用。

默认值：0vp

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: Length
```

组件图像上边沿像素扩展距离。需与left、right、bottom方向保持一致：四个方向的扩展统一为非正值或者非负值，不支持百分比和具体值混用。

默认值：0vp

**类型：** [Length](../arkts-apis/arkts-arkui-length-t.md)

**默认值：** 0

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
