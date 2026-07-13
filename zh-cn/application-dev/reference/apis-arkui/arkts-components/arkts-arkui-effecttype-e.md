# EffectType

使用效果模板种类的枚举值。

**效果模板：**

| 设备类型 | 模糊半径(单位: px) | 饱和度 | 亮度 | 颜色 |
| -------- | ---- | ---------------------- | -------- | -------- |
| 移动设备 | 0 | 0 | 0 | '#ffffffff'，显示为白色。 |
| 2in1设备：深色模式 | 80 | 1.5 | 1.0 | '#e52e3033'，显示为淡红色的半透明效果。 |
| 2in1设备：浅色模式 | 80 | 1.9 | 1.0 | '#e5ffffff'，显示为半透明的深红色。 |
| Tablet设备 | 0 | 0 | 0 | '#ffffffff'，显示为白色。 |

**起始版本：** 14

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

使用<!--Del-->父级EffectComponent定义的<!--DelEnd-->效果模板进行定义。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## WINDOW_EFFECT

```TypeScript
WINDOW_EFFECT = 1
```

使用窗口定义的效果模板进行定义。

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

