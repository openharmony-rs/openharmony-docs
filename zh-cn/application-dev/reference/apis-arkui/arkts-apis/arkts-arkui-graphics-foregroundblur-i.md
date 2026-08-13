# ForegroundBlur

设置前景模糊效果，支持通过模糊半径控制模糊程度。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface ForegroundBlur--><!--Device-unnamed-export interface ForegroundBlur-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: double
```

模糊半径。 单位：px 取值范围为[0, +∞)，默认值为0，负数、NaN和Infinity按默认值处理。值越大前景模糊效果越明显，为0时不模糊。

**类型：** double

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ForegroundBlur-radius: double--><!--Device-ForegroundBlur-radius: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

