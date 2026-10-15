# FontSettingOptions

```TypeScript
declare interface FontSettingOptions
```

Defines font setting options.

**Since:** 12

<!--Device-unnamed-declare interface FontSettingOptions--><!--Device-unnamed-declare interface FontSettingOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

Whether to enable variable font weight adjustment. This font configuration item is used as an input parameter of the [fontWeight](../arkts-components/arkts-arkui-text-comp-attribute.md#fontweight2) API. When the value of **weight** in the **fontWeight** API is a non-multiple-of-100 value within [100, 900], **enableVariableFontWeight** determines whether the value of **weight** takes effect.

Default value: **false**

**true**: Variable font weight adjustment is enabled. In this case, if the value of **weight** is any integer within [100, 900], the font weight is the value of **weight**; otherwise, the default value **400** is used.

**false**: Variable font weight adjustment is disabled. In this case, if the value of **weight** is a multiple of 100 within [100, 900], the font weight is the value of **weight**; if **weight** is a non-multiple-of-100 value, the default value **400** is used.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-FontSettingOptions-enableVariableFontWeight?: boolean--><!--Device-FontSettingOptions-enableVariableFontWeight?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
