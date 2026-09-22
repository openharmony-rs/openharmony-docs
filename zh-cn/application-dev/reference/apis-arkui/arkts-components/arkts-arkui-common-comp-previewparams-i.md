# PreviewParams

```TypeScript
interface PreviewParams
```

@Preview参数对象。

设置@Preview的参数，指定预览设备的相关属性，如不同设备、不同屏幕状态等。

> **说明：** 
> 
> PreviewParams中只支持使用与定义参数类型相匹配的入参，否则所有的@Preview的参数都将被置为默认值。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: string
```

显示的亮暗模式，取值为light或dark，tv设备默认为dark，其他设备默认为light，wearable设备仅支持dark。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## deviceType

```TypeScript
deviceType?: string
```

组件预览渲染的设备类型，默认为Phone。设备类型枚举值参考[deviceTypes标签](docroot:./../../../quick-start/module-configuration-file.md#devicetypes标签)。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dpi

```TypeScript
dpi?: number
```

预览设备的屏幕DPI值，默认为480。取值范围为[120, 640]内的整数。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: number
```

预览设备的高度，单位：px，默认为2340px。取值范围为[20, 3000]内的整数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## locale

```TypeScript
locale?: string
```

预览设备的语言区域，如zh_CN、en_US等，默认为zh_CN。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## orientation

```TypeScript
orientation?: string
```

预览设备的横竖屏状态，取值为portrait或landscape，默认为portrait。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## roundScreen

```TypeScript
roundScreen?: boolean
```

预览的屏幕形状是否为圆形，默认为false。true为圆形，false为非圆形。

**类型：** boolean

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## title

```TypeScript
title?: string
```

组件预览标题，默认为自定义组件名称。仅支持英文和数字，不支持中文和特殊字符。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: number
```

预览设备的宽度，单位：px，默认为1080px。取值范围为[20, 3000]内的整数。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
