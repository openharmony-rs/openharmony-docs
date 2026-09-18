# FontWeightConfigs

Defines font weight configurations. When the configuration object (including an empty object **{}**) is passed, the default values are used for properties that are not explicitly set. When **null** or **undefined** is passed, default values are not applied, and the font weight behavior is consistent with that of the parent component text.

**Since:** 24

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableDeviceFontWeightCategory

```TypeScript
enableDeviceFontWeightCategory?: boolean
```

Whether to automatically synchronize the font weight with the device's font weight setting.

Default value: **true**

**true**: The font weight is automatically synchronized when the device's font weight setting changes.

**false**: The font weight is not automatically synchronized when the device's font weight setting changes.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableVariableFontWeight

```TypeScript
enableVariableFontWeight?: boolean
```

Whether to enable variable font weight adjustment. When **weight** is set to a non-multiple of 100 within [100, 900], **enableVariableFontWeight** is used to set whether the **weight** value takes effect.

Default value: **false**

**true**: Enable variable font weight adjustment. If the value of **weight** is any integer within [100, 900], the value is used. Otherwise, the default value **400** is used.

**false**: Disable variable font weight adjustment. If the value of **weight** is a multiple of 100 within [100, 900], the value is used. If **weight** is a non-multiple of 100, the default value **400** is used.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
