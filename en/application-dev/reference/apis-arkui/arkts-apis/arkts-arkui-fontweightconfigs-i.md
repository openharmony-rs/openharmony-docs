# FontWeightConfigs

```TypeScript
declare interface FontWeightConfigs
```

Defines font weight configurations. When the configuration object (including an empty object **{}**) is passed, the default values are used for properties that are not explicitly set. When **null** or **undefined** is passed, default values are not applied, and the font weight behavior is consistent with that of the parent component text.

**Since:** 24

<!--Device-unnamed-declare interface FontWeightConfigs--><!--Device-unnamed-declare interface FontWeightConfigs-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableDeviceFontWeightCategory

```TypeScript
enableDeviceFontWeightCategory?: boolean
```

Whether to automatically update the font weight with the device font weight level.

Default value: **true**

**true**: When the device font weight level changes, the font weight is automatically updated.

**false**: When the device font weight level changes, the font weight is not automatically updated.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-FontWeightConfigs-enableDeviceFontWeightCategory?: boolean--><!--Device-FontWeightConfigs-enableDeviceFontWeightCategory?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

Whether to enable variable font weight adjustment. When the font weight value **weight** is set to a non-hundred value within [100, 900], **enableVariableFontWeight** determines whether the **weight** value takes effect.

Default value: **false**

**true**: Variable font weight adjustment is enabled. In this case, if **weight** is any integer within [100, 900], the font weight is **weight**; otherwise, the default value 400 is used.

**false**: Variable font weight adjustment is disabled. In this case, if **weight** is a hundred value within [100, 900], the font weight is **weight**; if **weight** is a non-hundred value, the default value 400 is used.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

<!--Device-FontWeightConfigs-enableVariableFontWeight?: boolean--><!--Device-FontWeightConfigs-enableVariableFontWeight?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
