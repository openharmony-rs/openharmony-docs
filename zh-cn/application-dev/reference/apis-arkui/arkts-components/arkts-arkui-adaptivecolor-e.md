# AdaptiveColor

取色模式。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## DEFAULT

```TypeScript
DEFAULT = 0
```

不使用取色模糊。使用系统预设颜色作为蒙版颜色。采用非DEFAULT方式的取色计算耗时高于DEFAULT方式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## AVERAGE

```TypeScript
AVERAGE = 1
```

使用取色模糊。将取色区域的颜色平均值作为蒙版颜色。采用AVERAGE方式较DEFAULT方式耗时，在性能敏感场景建议使用DEFAULT。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
