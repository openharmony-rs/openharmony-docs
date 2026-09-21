# ButtonType

```TypeScript
declare enum ButtonType
```

Enumerates the button types.

> **NOTE:** 
> 
> - The corner radius of the rounded rectangle button is set using the universal attribute [borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius).
> 
> - For a button of the **Capsule** type, the **borderRadius** settings do not take effect, and the radius of its rounded corner is always half of the button height or width, whichever is smaller.
> 
> - For a button of the **Circle** type: (1) If both its width and height are set, **borderRadius** does not take effect, and the button radius is half of the width or height (whichever is smaller). (2) If either its width or height is set, **borderRadius** does not take effect, and the button radius is half of the set width or height. (3)If neither its width nor height is set, the button radius is as specified by **borderRadius**; if **borderRadius**is set to a negative value, the value **0** will be used.
> 
> - The button text is set using [fontSize](arkts-arkui-button-comp-attribute.md#fontsize),[fontColor](arkts-arkui-button-comp-attribute.md#fontcolor), [fontStyle](arkts-arkui-button-comp-attribute.md#fontstyle),[fontFamily](arkts-arkui-button-comp-attribute.md#fontfamily), and [fontWeight](arkts-arkui-button-comp-attribute.md#fontweight).
> 
> - Before setting the gradient color, you need to set [backgroundColor](arkts-arkui-common-comp-commonmethod-c.md#backgroundcolor) to transparent.
> 
> - When **borderRadius** is not set, the corner radius of the rounded rectangle button remains at the default value.In this case, the corner radius does not change with the button height and is subject to the **controlSize**property. When **controlSize** is **NORMAL**, the corner radius is 20 vp; when **controlSize** is **SMALL**, the corner radius is 14 vp.
> 
> - When [border](arkts-arkui-common-comp-commonmethod-c.md#border) is set for the button, a default [borderRadius](arkts-arkui-common-comp-commonmethod-c.md#borderradius) value is automatically applied. When both **border** and **borderRadius** attributes are used, **borderRadius** must be specified after **border** to prevent the border radius from being overridden by the default radius value in the border style.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Capsule

```TypeScript
Capsule
```

Capsule-type button (the round corner is half of the height by default).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Circle

```TypeScript
Circle
```

Circular button.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Normal

```TypeScript
Normal
```

Normal button, with no rounded corners by default.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ROUNDED_RECTANGLE

```TypeScript
ROUNDED_RECTANGLE = 3
```

Rounded rectangle button (default value: when **controlSize** is **NORMAL**, the corner radius is 20 vp; when controlSize is **SMALL**, the corner radius is 14 vp).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
