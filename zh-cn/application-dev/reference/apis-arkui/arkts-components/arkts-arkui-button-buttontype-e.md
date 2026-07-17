# ButtonType

按钮的类型。

> **说明：**  
>  
> - 按钮圆角通过  
> [通用属性borderRadius](arkts-arkui-common-commonmethod-c.md#borderradius-1)设置。  
>  
> - 当按钮类型为Capsule时，borderRadius设置不生效，按钮圆角始终为宽、高中较小值的一半。  
>  
> - 当按钮类型为Circle时，若同时设置了宽和高，则borderRadius不生效，且按钮半径为宽高中较小值的一半；若只设置宽、高中的一个，则borderRadius不生效，且按钮半径为所设宽或所设高值的一半；若不设置宽高，则  
> borderRadius为按钮半径；若borderRadius的值为负，则borderRadius的值按照0处理。  
>  
> - 按钮文本通过[fontSize](ButtonAttribute#fontSize)、[fontColor](ButtonAttribute#fontColor)、  
> [fontStyle](ButtonAttribute#fontStyle)、[fontFamily](ButtonAttribute#fontFamily)、  
> [fontWeight](ButtonAttribute#fontWeight)进行设置。  
>  
> - 设置[颜色渐变](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)需先设置[backgroundColor](arkts-arkui-common-commonmethod-c.md#backgroundcolor-1)为透明色。  
>  
> - 在不设置borderRadius时，圆角矩形按钮的圆角大小保持默认值不变。圆角大小不会随按钮高度变化而变化，和controlSize属性有关，controlSize为NORMAL时圆角大小20vp，controlSize为  
> SMALL时圆角大小14vp。  
>  
> - 设置Button的[border](arkts-arkui-common-commonmethod-c.md#border-1)时，会有默认的  
> [borderRadius](arkts-arkui-common-commonmethod-c.md#borderradius-1)值。如果同时使用  
> `border`和`borderRadius`，需将`borderRadius`放在`border`之后，以确保`borderRadius`不会被`border`中的默认`radius`覆盖。

**起始版本：** 7

<!--Device-unnamed-declare enum ButtonType--><!--Device-unnamed-declare enum ButtonType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule
```

胶囊型按钮（圆角默认为高度的一半）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonType-Capsule--><!--Device-ButtonType-Capsule-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Circle

```TypeScript
Circle
```

圆形按钮。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonType-Circle--><!--Device-ButtonType-Circle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

普通按钮（默认不带圆角）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonType-Normal--><!--Device-ButtonType-Normal-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ROUNDED_RECTANGLE

```TypeScript
ROUNDED_RECTANGLE = 3
```

圆角矩形按钮（默认值：controlSize为NORMAL，圆角大小20vp，controlSize为SMALL，圆角大小14vp）。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-ButtonType-ROUNDED_RECTANGLE = 3--><!--Device-ButtonType-ROUNDED_RECTANGLE = 3-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

