# SurfaceRect

描述XComponent所持有的surface的矩形。

> **说明：**

> 如果未调用[setXComponentSurfaceRect](arkts-arkui-xcomponentcontroller-c.md#setxcomponentsurfacerect)接口，且未设置
> [border](arkts-arkui-commonmethod-c.md#border)和
> padding，则**surfaceWidth**和**surfaceHeight**属性默认为**XComponent**的尺寸。
> 
> 请确保**surfaceWidth**和**surfaceHeight**的值不超过8192 px。超过此限制可能导致渲染问题。
> 
> 在沉浸式场景中，**SurfaceRect**的默认布局不包含安全区域。要实现沉浸式效果，必须使用
> [setXComponentSurfaceRect](arkts-arkui-xcomponentcontroller-c.md#setxcomponentsurfacerect)接口设置surface显示区域。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## offsetX

```TypeScript
offsetX?: number
```

surface矩形相对于XComponent左上角的X坐标。单位：px。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY?: number
```

surface矩形相对于XComponent左上角的Y坐标。单位：px。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## surfaceHeight

```TypeScript
surfaceHeight: number
```

surface矩形的高度。单位：px。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## surfaceWidth

```TypeScript
surfaceWidth: number
```

surface矩形的宽度。单位：px。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
