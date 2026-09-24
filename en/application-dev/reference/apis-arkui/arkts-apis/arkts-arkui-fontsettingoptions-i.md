# FontSettingOptions

```TypeScript
declare interface FontSettingOptions
```

Defines font setting options.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

Whether to enable variable font weight adjustment. This parameter serves as the input for the [fontWeight](../arkts-components/arkts-arkui-text-comp-attribute.md#fontweight-1) API. When the **weight** value in **fontWeight** is a non-hundred value within the [100, 900] range, **enableVariableFontWeight** controls whether this **weight** value is applied.

Default value: **false**

**true**: Enable variable font weight adjustment. If the **weight** value is an integer within the [100, 900] range, it is applied as the font weight.

**false**: Disable variable font weight adjustment. If the value of **weight** is a multiple of 100 within [100, 900], the value is used. If **weight** is a non-multiple of 100, the default value **400** is used.

**Type:** boolean

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
