# ProgressType

进度条类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ProgressType--><!--Device-unnamed-export declare enum ProgressType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Linear

```TypeScript
Linear = 0
```

线性样式。当高度大于宽度时，自适应垂直显示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressType-Linear = 0--><!--Device-ProgressType-Linear = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Ring

```TypeScript
Ring = 1
```

环形无刻度样式，环形圆环逐渐显示直至完全填充。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressType-Ring = 1--><!--Device-ProgressType-Ring = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Eclipse

```TypeScript
Eclipse = 2
```

圆形样式，显示类似月圆月缺的进度展示效果，从月牙逐渐变化至满月。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressType-Eclipse = 2--><!--Device-ProgressType-Eclipse = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ScaleRing

```TypeScript
ScaleRing = 3
```

环形有刻度样式，显示类似时钟刻度形式的进度展示效果。刻度外圈出现重叠时自动转换为环形无刻度进度条。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressType-ScaleRing = 3--><!--Device-ProgressType-ScaleRing = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule = 4
```

胶囊样式，头尾两端圆弧处的进度展示效果与Eclipse相同，中段的进度展示效果与Linear相同。当高度大于宽度时，自适应垂直显示。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ProgressType-Capsule = 4--><!--Device-ProgressType-Capsule = 4-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

