# WidthBreakpoint

```TypeScript
declare enum WidthBreakpoint
```

表示窗口不同宽度阈值下对应的宽度断点枚举值。通过[getWindowWidthBreakpoint](arkts-arkui-arkui-uicontext-uicontext-c.md#getwindowwidthbreakpoint)返回。

下表列出了典型设备默认宽度断点的阈值划分，可在基于窗口宽度断点布局设计时作为参考。个别设备可根据需求通过产品化配置调整断点阈值。

**起始版本：** 13

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WIDTH_XS

```TypeScript
WIDTH_XS = 0
```

窗口宽度小于320vp。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WIDTH_SM

```TypeScript
WIDTH_SM = 1
```

窗口宽度大于等于320vp，且小于600vp。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WIDTH_MD

```TypeScript
WIDTH_MD = 2
```

窗口宽度大于等于600vp，且小于840vp。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WIDTH_LG

```TypeScript
WIDTH_LG = 3
```

窗口宽度大于等于840vp，且小于1440vp。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WIDTH_XL

```TypeScript
WIDTH_XL = 4
```

窗口宽度大于等于1440vp。

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
