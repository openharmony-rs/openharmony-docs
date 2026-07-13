# WindowLimits

窗口尺寸限制参数，应用可以通过[getWindowLimits](arkts-arkui-window-i.md#getwindowlimits-1)获得当前窗口的尺寸限制（单位为px）；从API version 2
2开始，还可以通过[getWindowLimitsVP](arkts-arkui-window-i.md#getwindowlimitsvp-1)获取窗口尺寸限制（单位为vp）。

窗口尺寸限制的最终生效结果由默认系统限制、应用配置和运行时设置的数据取交集得到，优先级从高到低依次为：

1. 应用通过[setWindowLimits](arkts-arkui-window-i.md#setwindowlimits-1)设置窗口尺寸限制。
2. 应用在[startAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md#startability-3)拉起窗口时通过[StartOptions](../../apis-ability-kit/arkts-apis/arkts-ability-startoptions-c.md)指定窗口尺寸限制（API version 17开始支持）。
3. 应用在[module.json5配置文件中的abilities标签](../../../../quick-start/module-configuration-file.md#abilities标签)中配置windowLimits。
4. 默认系统限制（基于不同产品和窗口类型，其windowLimits系统默认限制存在差异）。

> **说明：**
>
> 针对maxWidth、maxHeight、minWidth、minHeight属性：
>
> - 默认单位为px，从API version 22开始支持通过pixelUnit设置单位为px或vp。
>
> - 参数为整数，浮点数会向下取整。
>
> - 默认值为0，表示属性不发生变化。
>
> - 可生效范围下限值：系统限定的最小高度/宽度。
>
> - 可生效范围上限值：系统限定的最大高度/宽度。

**起始版本：** 11

**系统能力：** SystemCapability.Window.SessionManager

## maxHeight

```TypeScript
maxHeight?: number
```

窗口的最大高度。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## maxWidth

```TypeScript
maxWidth?: number
```

窗口的最大宽度。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## minHeight

```TypeScript
minHeight?: number
```

窗口的最小高度。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## minWidth

```TypeScript
minWidth?: number
```

窗口的最小宽度。

**类型：** number

**起始版本：** 11

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Window.SessionManager

## pixelUnit

```TypeScript
pixelUnit?: PixelUnit
```

窗口尺寸限制的单位，默认为px。可显式设置为px或vp。

**类型：** PixelUnit

**起始版本：** 22

**系统能力：** SystemCapability.Window.SessionManager

