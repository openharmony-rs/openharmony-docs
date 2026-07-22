# Rectangle

矩形区域类型。
> **说明：**  
>  
> - x和y可以设置正负值百分比。当x设置为'100%'时表示热区往右偏移组件本身宽度大小，当x设置为'-100%'时表示热区往左偏移组件本身宽度大小。当y设置为'100%'时表示热区往下偏移组件本身高度大小，当y设置为  
> '-100%'时表示热区往上偏移组件本身高度大小。  
>  
> - width和height设置百分比时，只能设置正值百分比。width：'100%'表示热区宽度设置为该组件本身的宽度。比如组件本身宽度是100vp，那么'100%'表示热区宽度也为100vp。height：'100%'表示热区  
> 高度设置为该组件本身的高度。  
>  
> - 百分比相对于组件自身宽高进行计算。  
>  
> - 当父组件设置[clip](arkts-arkui-commonmethod-c.md#clip)(true)时，子组件的响应会受到父组件触摸热区的影响，不在父组件触摸热区内的子组件无法响应手势和事件。  
>  
> - width和height不支持calc()的动态计算。

**起始版本：** 8

<!--Device-unnamed-declare interface Rectangle--><!--Device-unnamed-declare interface Rectangle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

触摸热区的高度。

默认值：'100%'

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Rectangle-height?: Length--><!--Device-Rectangle-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

触摸热区的宽度。

默认值：'100%'

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Rectangle-width?: Length--><!--Device-Rectangle-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## x

```TypeScript
x?: Length
```

触摸点相对于组件左上角的x轴坐标。

默认值：0vp

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Rectangle-x?: Length--><!--Device-Rectangle-x?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## y

```TypeScript
y?: Length
```

触摸点相对于组件左上角的y轴坐标。

默认值：0vp

**类型：** Length

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-Rectangle-y?: Length--><!--Device-Rectangle-y?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

