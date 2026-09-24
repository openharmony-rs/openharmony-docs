# HeightBreakpoint

```TypeScript
declare enum HeightBreakpoint
```

表示窗口不同高宽比阈值下对应的高度断点枚举值。通过[getWindowHeightBreakpoint](arkts-arkui-arkui-uicontext-uicontext-c.md#getwindowheightbreakpoint)返回。

下表列出了典型设备默认高宽比断点的阈值划分，可在基于窗口高宽比布局设计时作为参考。个别设备可根据需求通过产品化配置调整断点阈值。

**起始版本：** 13

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_SM

```TypeScript
HEIGHT_SM = 0
```

窗口高宽比小于0.8。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_MD

```TypeScript
HEIGHT_MD = 1
```

窗口高宽比大于等于0.8，且小于1.2。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## HEIGHT_LG

```TypeScript
HEIGHT_LG = 2
```

窗口高宽比大于等于1.2。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
