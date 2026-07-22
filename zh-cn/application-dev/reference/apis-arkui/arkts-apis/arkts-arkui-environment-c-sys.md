# Environment

Environment具体使用说明，详见[Environment(设备环境查询)](../../../ui/state-management/arkts-environment.md)

## 内置环境变量说明

| key | 类型 | 说明 |  
| -------------------- | --------------- | ------------------------------------------------------------ |  
| accessibilityEnabled | string | 无障碍屏幕朗读是否启用。当无法获取环境变量中的accessibilityEnabled的值时，将通过envProp、envProps等接口传入的开发者指定的默认值添加到AppStorage中。 |  
| colorMode | [ColorMode](arkts-arkui-colormode-e.md) | 深浅色模式，可选值为：<br/>- ColorMode.LIGHT：浅色模式；<br/>- ColorMode.DARK：深色模式。 |  
| fontScale | number | 字体大小比例。 |  
| fontWeightScale | number | 字重比例。 |  
| layoutDirection | [LayoutDirection](arkts-arkui-layoutdirection-e.md) | 布局方向类型，可选值为：<br/>- LayoutDirection.LTR：从左到右；<br/>- LayoutDirection.RTL：从右到左。<br/>- Auto：跟随系统。 |  
| languageCode | string | 当前系统语言，小写字母，例如zh。

**起始版本：** 7

<!--Device-unnamed-declare class Environment--><!--Device-unnamed-declare class Environment-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

构造函数。

**起始版本：** 7

<!--Device-Environment-constructor()--><!--Device-Environment-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

