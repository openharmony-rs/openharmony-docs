# SliderChangeMode

滑块状态值，包括按下、拖动、离开、点击滑动条使滑块移动时。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Begin

```TypeScript
Begin
```

手势或鼠标接触/按下滑块。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Moving

```TypeScript
Moving
```

拖动滑块过程中。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## End

```TypeScript
End
```

手势或鼠标离开滑块。  
**说明：**异常值恢复成默认值时触发，即value设置小于min或大于max。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Click

```TypeScript
Click
```

点击滑动条使滑块移动。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
