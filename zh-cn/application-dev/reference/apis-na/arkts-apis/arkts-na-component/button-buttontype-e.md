# ButtonType

按钮的类型。 > **说明：** > > - 按钮圆角通过 > [通用属性borderRadius]\_\_\_JSDOC\_LINK\_DESC\_USD\_7\_\_\_设置。 > > - 当按钮类型为Capsule时，borderRadius设置不生效，按钮圆角始终为宽、高中较小值的一半。 > > - 当按钮类型为Circle时，若同时设置了宽和高，则borderRadius不生效，且按钮半径为宽高中较小值的一半；若只设置宽、高中的一个，则borderRadius不生效，且按钮半径为所设宽或所设高值的一半；若不设置宽高，则 > borderRadius为按钮半径；若borderRadius的值为负，则borderRadius的值按照0处理。 > > - 按钮文本通过[fontSize]\_\_\_JSDOC\_LINK\_DESC\_USD\_8\_\_\_、[fontColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_9\_\_\_、[fontStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_10\_\_\_、 > [fontFamily]\_\_\_JSDOC\_LINK\_DESC\_USD\_11\_\_\_、[fontWeight]\_\_\_JSDOC\_LINK\_DESC\_USD\_12\_\_\_进行设置。 > > - 设置[颜色渐变]\_\_\_JSDOC\_LINK\_DESC\_USD\_13\_\_\_需先设置[backgroundColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_14\_\_\_为透明色。 > > - 在不设置borderRadius时，圆角矩形按钮的圆角大小保持默认值不变。圆角大小不会随按钮高度变化而变化，和controlSize属性有关，controlSize为NORMAL时圆角大小20vp，controlSize为 > SMALL时圆角大小14vp。 > > - 设置Button的[border]\_\_\_JSDOC\_LINK\_DESC\_USD\_15\_\_\_时，会有默认的 > [borderRadius]\_\_\_JSDOC\_LINK\_DESC\_USD\_16\_\_\_值。如果同时使用 > \_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_和\_\_\_INLINE\_CODE\_DESC\_USD\_1\_\_\_，需将\_\_\_INLINE\_CODE\_DESC\_USD\_2\_\_\_放在\_\_\_INLINE\_CODE\_DESC\_USD\_3\_\_\_之后，以确保\_\_\_INLINE\_CODE\_DESC\_USD\_4\_\_\_不会被\_\_\_INLINE\_CODE\_DESC\_USD\_5\_\_\_中的默认\_\_\_INLINE\_CODE\_DESC\_USD\_6\_\_\_覆盖。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare enum ButtonType--><!--Device-unnamed-export declare enum ButtonType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule
```

胶囊型按钮（圆角默认为高度的一半）。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonType-Capsule--><!--Device-ButtonType-Capsule-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Circle

```TypeScript
Circle
```

圆形按钮。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonType-Circle--><!--Device-ButtonType-Circle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

普通按钮（默认不带圆角）。 **卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonType-Normal--><!--Device-ButtonType-Normal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ROUNDED_RECTANGLE

```TypeScript
ROUNDED_RECTANGLE = 3
```

圆角矩形按钮（默认值：controlSize为NORMAL，圆角大小20vp，controlSize为SMALL，圆角大小14vp）。 **卡片能力（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在ArkTS卡片中使用。 **原子化服务API（仅ArkTS-Dyn）：** 从API version 15开始，该接口支持在原子化服务中使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ButtonType-ROUNDED_RECTANGLE = 3--><!--Device-ButtonType-ROUNDED_RECTANGLE = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

