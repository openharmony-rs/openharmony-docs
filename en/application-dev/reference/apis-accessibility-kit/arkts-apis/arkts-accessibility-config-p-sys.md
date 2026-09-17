# Properties (System API)

## animationOff

```TypeScript
let animationOff: Config<boolean>
```

Whether to disable animation. The value **true** indicates that animation is disabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## brightnessDiscount

```TypeScript
let brightnessDiscount: Config<number>
```

Indicates the brightness discount configuration, which is used to proportionally adjust the screen display brightness. The value ranges from 0 to 1.0, where **0** indicates no brightness discount (original brightness) and **1.0** indicates the maximum brightness discount. The default value is **0.0**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## captions

```TypeScript
let captions: Config<boolean>
```

Whether to enable captions. The value **true** indicates that caption is enabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## captionsStyle

```TypeScript
let captionsStyle: Config<accessibility.CaptionsStyle>
```

Indicates the configuration of the caption style.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[accessibility.CaptionsStyle](arkts-accessibility-accessibility-captionsstyle-i.md)&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## contentTimeout

```TypeScript
let contentTimeout: Config<number>
```

Indicates the content display suggested duration configuration, which is used to set the duration for which accessibility prompts and other content remain displayed on the screen. The value ranges from 0 to 5000, in milliseconds. The default value is **0**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## daltonizationColorFilter

```TypeScript
let daltonizationColorFilter: Config<DaltonizationColorFilter>
```

Indicates the color correction filter configuration. Used together with daltonizationState. This configuration takes effect only when daltonizationState is set to **true**. The default value is Normal, indicating the standard type.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;[DaltonizationColorFilter](arkts-accessibility-config-daltonizationcolorfilter-t-sys.md)&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## highContrastText

```TypeScript
let highContrastText: Config<boolean>
```

Whether to enable high-contrast text. The value **true** indicates that high-contrast text is enabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## invertColor

```TypeScript
let invertColor: Config<boolean>
```

Whether to enable color inversion. The value **true** indicates that color inversion is enabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## mouseAutoClick

```TypeScript
let mouseAutoClick: Config<number>
```

Indicates the configuration for the mouse auto-click operation. The value ranges from 0 to 5000, in milliseconds. **0** indicates that the feature is disabled, and other values indicate the duration of mouse hovering that triggers the auto-click operation. The default value is **0**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;number&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## mouseKey

```TypeScript
let mouseKey: Config<boolean>
```

Whether to enable the mouse button. The value **true** indicates that the mouse button is enabled, and **false** indicates the opposite.

Default value: **false**

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## shortkey

```TypeScript
let shortkey: Config<boolean>
```

Indicates the accessibility extension shortcut key feature status. Used together with shortkeyTarget. The value **true** indicates that the accessibility extension shortcut key feature is enabled, and **false** indicates that it is disabled. The default value is **false**.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;boolean&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## shortkeyTarget

```TypeScript
let shortkeyTarget: Config<string>
```

Indicates the target configuration of the accessibility extension shortcut key. The value is the name of the accessibility extension app, in the format 'bundleName/abilityName'. If the format is incorrect or the name is invalid, the setting does not take effect.

**Type:** [Config](arkts-accessibility-config-config-i-sys.md)&lt;string&gt;

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
