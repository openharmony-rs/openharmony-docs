# text.h

## Overview

Defines a set of Text enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | OH_ArkUI_TextDataDetectorConfig | Defines the configuration of text entity recognition. |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | ArkUI_TextMarqueeOptions | Defines the marquee options of text. |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | OH_ArkUI_TextController | Defines controller for text. |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | OH_ArkUI_FontWeightConfigs | Defines the font weight configuration of text. |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | OH_ArkUI_FontConfigs | Defines the font configuration of text. |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) | OH_ArkUI_NativeModule_LineSpacingOptions | Defines the line spacing options for text. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_FontStyle](#arkui_fontstyle) | ArkUI_FontStyle | Enumerates the font styles. |
| [ArkUI_FontWeight](#arkui_fontweight) | ArkUI_FontWeight | Enumerates the font weights. |
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy) | ArkUI_TextHeightAdaptivePolicy | Defines how the adaptive height is determined for the text. |
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype) | ArkUI_TextDataDetectorType | Defines the entity type for text recognition. |
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy) | ArkUI_MarqueeStartPolicy | Enumerates the MarqueeStartPolicy. |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) | ArkUI_MarqueeUpdatePolicy | Enumerates the MarqueeUpdatePolicy. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()](#oh_arkui_textmarqueeoptions_create) | Create an option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_dispose) | Dispose the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)](#oh_arkui_textmarqueeoptions_setstart) | Sets the start flag of the option object for marquee animation of text. |
| [bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstart) | Gets the start flag of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)](#oh_arkui_textmarqueeoptions_setstep) | Sets the step size of the option object for marquee animation of text. |
| [float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstep) | Gets the step size of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)](#oh_arkui_textmarqueeoptions_setspacing) | Sets the spacing between two rounds of the option object for marquee animation of text. |
| [float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getspacing) | Gets the spacing between two rounds of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)](#oh_arkui_textmarqueeoptions_setloop) | Sets the rounds of the option object for marquee animation of text. |
| [int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getloop) | Gets the rounds of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)](#oh_arkui_textmarqueeoptions_setfromstart) | Sets the fromStart flag of the option object for marquee animation of text. |
| [bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfromstart) | Gets the fromStart flag of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)](#oh_arkui_textmarqueeoptions_setdelay) | Sets the delay time between each round of the option object for marquee animation of text. |
| [int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getdelay) | Gets the delay time between each round of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)](#oh_arkui_textmarqueeoptions_setfadeout) | Sets the fadeout flag of the option object for marquee animation of text. |
| [bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfadeout) | Gets the fadeout flag of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)](#oh_arkui_textmarqueeoptions_setstartpolicy) | Sets the start policy of the option object for marquee animation of text. |
| [ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstartpolicy) | Gets the start policy of the option object for marquee animation of text. |
| [void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)](#oh_arkui_textmarqueeoptions_setupdatepolicy) | Sets the update policy of the option object for marquee animation of text. |
| [ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getupdatepolicy) | Gets the update policy of the option object for marquee animation of text. |
| [OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()](#oh_arkui_textdatadetectorconfig_create) | Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it. |
| [void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)](#oh_arkui_textdatadetectorconfig_destroy) | Destroys the text entity recognition configuration object. |
| [OH_ArkUI_TextController* OH_ArkUI_TextController_Create()](#oh_arkui_textcontroller_create) | Create a controller object for text. |
| [void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)](#oh_arkui_textcontroller_destroy) | Destroys the text controller. |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()](#oh_arkui_fontweightconfigs_create) | Create an option object for font weight configuration of text. |
| [void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_destroy) | Destroy an option object for font weight configuration of text. |
| [void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenablevariablefontweight) | Sets the enableVariableFontWeight flag of an option object for font weight configuration of text. The flag defines whether VariableFontWeight is supported. The default value is false. True means enable VariableFontWeight, false means disable VariableFontWeight. |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenablevariablefontweight) | Gets the enableVariableFontWeight flag of an option object for font weight configuration of text. The flag defines whether VariableFontWeight is supported. The default value is false. True means enable VariableFontWeight, false means disable VariableFontWeight. |
| [void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) | Sets the enableDeviceFontWeightCategory flag of an option object for font weight configuration of text. Defines whether font weight will be automatically updated when the device's font weight category changes. The default value is true. True means font weight will be automatically updated when the device's font weight category changes. False means font weight will not be automatically updated when the device's font weight category changes. |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) | Gets the enableDeviceFontWeightCategory flag of an option object for font weight configuration of text. Defines whether font weight will be automatically updated when the device's font weight category changes. The default value is true. True means font weight will be automatically updated when the device's font weight category changes. False means font weight will not be automatically updated when the device's font weight category changes. |
| [OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()](#oh_arkui_fontconfigs_create) | Create an option object for font configuration of text. |
| [void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_destroy) | Destroy an option object for font configuration of text. |
| [void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)](#oh_arkui_fontconfigs_setfontweightconfigs) | Sets the font weight configs of an option object for font configuration of text. |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_getfontweightconfigs) | Gets the font weight configs of an option object for font configuration of text. |
| [OH_ArkUI_NativeModule_LineSpacingOptions *OH_ArkUI_NativeModule_LineSpacingOptions_Create()](#oh_arkui_nativemodule_linespacingoptions_create) | Creates a line spacing options object for text. When the object is no longer used, call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy it. |
| [void OH_ArkUI_NativeModule_LineSpacingOptions_Destroy(OH_ArkUI_NativeModule_LineSpacingOptions *options)](#oh_arkui_nativemodule_linespacingoptions_destroy) | Destroys the line spacing options object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines(OH_ArkUI_NativeModule_LineSpacingOptions *options, bool onlyBetweenLines)](#oh_arkui_nativemodule_linespacingoptions_setonlybetweenlines) | Sets the onlyBetweenLines parameter for the line spacing options. When set to true, line spacing is only applied between lines, not for the first and last lines. When set to false, line spacing is applied uniformly to all lines. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines(const OH_ArkUI_NativeModule_LineSpacingOptions *options, bool *onlyBetweenLines)](#oh_arkui_nativemodule_linespacingoptions_getonlybetweenlines) | Gets the onlyBetweenLines parameter from the line spacing options. |

## Enum type description

### ArkUI_FontStyle

```c
enum ArkUI_FontStyle
```

**Description**

Enumerates the font styles.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FONT_STYLE_NORMAL = 0 | Standard font style. |
| ARKUI_FONT_STYLE_ITALIC | Italic font style. |

### ArkUI_FontWeight

```c
enum ArkUI_FontWeight
```

**Description**

Enumerates the font weights.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_FONT_WEIGHT_W100 = 0 | 100 |
| ARKUI_FONT_WEIGHT_W200 | 200 |
| ARKUI_FONT_WEIGHT_W300 | 300 |
| ARKUI_FONT_WEIGHT_W400 | 400 |
| ARKUI_FONT_WEIGHT_W500 | 500 |
| ARKUI_FONT_WEIGHT_W600 | 600 |
| ARKUI_FONT_WEIGHT_W700 | 700 |
| ARKUI_FONT_WEIGHT_W800 | 800 |
| ARKUI_FONT_WEIGHT_W900 | 900 |
| ARKUI_FONT_WEIGHT_BOLD | The font weight is bold. |
| ARKUI_FONT_WEIGHT_NORMAL | The font weight is normal. |
| ARKUI_FONT_WEIGHT_BOLDER | The font weight is bolder. |
| ARKUI_FONT_WEIGHT_LIGHTER | The font weight is lighter. |
| ARKUI_FONT_WEIGHT_MEDIUM | The font weight is medium. |
| ARKUI_FONT_WEIGHT_REGULAR | The font weight is normal. |

### ArkUI_TextHeightAdaptivePolicy

```c
enum ArkUI_TextHeightAdaptivePolicy
```

**Description**

Defines how the adaptive height is determined for the text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST = 0 | Prioritize the <b>maxLines</b> settings. |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST | Prioritize the <b>minFontSize</b> settings. |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST | Prioritize the layout constraint settings in terms of height. |

### ArkUI_TextDataDetectorType

```c
enum ArkUI_TextDataDetectorType
```

**Description**

Defines the entity type for text recognition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER = 0 | Phone Number. |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_URL | Link. |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL | Mailbox. |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS | Address. |

### ArkUI_MarqueeStartPolicy

```c
enum ArkUI_MarqueeStartPolicy
```

**Description**

Enumerates the MarqueeStartPolicy.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_MARQUEESTARTPOLICY_DEFAULT = 0 | Start marquee in any case. This is the default policy. |
| ARKUI_MARQUEESTARTPOLICY_ONFOCUS = 1 | Start marquee only when get focus. |

### ArkUI_MarqueeUpdatePolicy

```c
enum ArkUI_MarqueeUpdatePolicy
```

**Description**

Enumerates the MarqueeUpdatePolicy.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

| Enum item | Description |
| -- | -- |
| ARKUI_MARQUEEUPDATEPOLICY_DEFAULT = 0 | Reset scroll position and restart scroll. |
| ARKUI_MARQUEEUPDATEPOLICY_PRESERVEPOSITION = 1 | Preserve scroll position, just change to new text. |


## Function description

### OH_ArkUI_TextMarqueeOptions_Create()

```c
ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()
```

**Description**

Create an option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions*](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | A pointer to the option object. |

### OH_ArkUI_TextMarqueeOptions_Dispose()

```c
void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)
```

**Description**

Dispose the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be disposed. |

### OH_ArkUI_TextMarqueeOptions_SetStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)
```

**Description**

Sets the start flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| bool start | Flag of is need to start marquee. True means start marquee, false means stop marquee. |

### OH_ArkUI_TextMarqueeOptions_GetStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the start flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the start flag. |

### OH_ArkUI_TextMarqueeOptions_SetStep()

```c
void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)
```

**Description**

Sets the step size of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| float step | The step size of the marquee. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_GetStep()

```c
float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the step size of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the step size of the marquee. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_SetSpacing()

```c
void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)
```

**Description**

Sets the spacing between two rounds of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| float spacing | The spacing between two rounds of marquee. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_GetSpacing()

```c
float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the spacing between two rounds of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the spacing between two rounds of marquee. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_SetLoop()

```c
void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)
```

**Description**

Sets the rounds of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| int32_t loop | The rounds of the marquee. |

### OH_ArkUI_TextMarqueeOptions_GetLoop()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the rounds of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the rounds of the marquee. |

### OH_ArkUI_TextMarqueeOptions_SetFromStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)
```

**Description**

Sets the fromStart flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| bool fromStart | The running direction of the marquee, true means running from start. |

### OH_ArkUI_TextMarqueeOptions_GetFromStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the fromStart flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the fromStart flag. |

### OH_ArkUI_TextMarqueeOptions_SetDelay()

```c
void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)
```

**Description**

Sets the delay time between each round of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| int32_t delay | The delay time between each round of the marquee. |

### OH_ArkUI_TextMarqueeOptions_GetDelay()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the delay time between each round of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the delay time between each round of the marquee. |

### OH_ArkUI_TextMarqueeOptions_SetFadeout()

```c
void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)
```

**Description**

Sets the fadeout flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| bool fadeout | The flag of whether the text is faded out. |

### OH_ArkUI_TextMarqueeOptions_GetFadeout()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the fadeout flag of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the fadeout flag. |

### OH_ArkUI_TextMarqueeOptions_SetStartPolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)
```

**Description**

Sets the start policy of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) startPolicy | The start policy for marquee. |

### OH_ArkUI_TextMarqueeOptions_GetStartPolicy()

```c
ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the start policy of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) | Returns the start policy for marquee. |

### OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)
```

**Description**

Sets the update policy of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object to be modified. |
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) updatePolicy | The update policy for marquee. |

### OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy()

```c
ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Gets the update policy of the option object for marquee animation of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) | Returns the update policy for marquee. |

### OH_ArkUI_TextDataDetectorConfig_Create()

```c
OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()
```

**Description**

Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig*](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | Pointer to the [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) object. |

### OH_ArkUI_TextDataDetectorConfig_Destroy()

```c
void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)
```

**Description**

Destroys the text entity recognition configuration object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | Pointer to the [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) object. |

### OH_ArkUI_TextController_Create()

```c
OH_ArkUI_TextController* OH_ArkUI_TextController_Create()
```

**Description**

Create a controller object for text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextController*](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | A pointer to the text controller object. |

### OH_ArkUI_TextController_Destroy()

```c
void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)
```

**Description**

Destroys the text controller.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | <b>Text</b> controller. |

### OH_ArkUI_FontWeightConfigs_Create()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()
```

**Description**

Create an option object for font weight configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | A pointer to the option object. |

### OH_ArkUI_FontWeightConfigs_Destroy()

```c
void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Destroy an option object for font weight configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the option object to be destroyed. |

### OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets the enableVariableFontWeight flag of an option object for font weight configuration of text. The flag defines whether VariableFontWeight is supported. The default value is false. True means enable VariableFontWeight, false means disable VariableFontWeight.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the option object to be modified. |
| bool enable | enableVariableFontWeight Flag. |

### OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Gets the enableVariableFontWeight flag of an option object for font weight configuration of text. The flag defines whether VariableFontWeight is supported. The default value is false. True means enable VariableFontWeight, false means disable VariableFontWeight.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the enableVariableFontWeight flag. |

### OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets the enableDeviceFontWeightCategory flag of an option object for font weight configuration of text. Defines whether font weight will be automatically updated when the device's font weight category changes. The default value is true. True means font weight will be automatically updated when the device's font weight category changes. False means font weight will not be automatically updated when the device's font weight category changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the option object to be modified. |
| bool enable | enableDeviceFontWeightCategory Flag. |

### OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Gets the enableDeviceFontWeightCategory flag of an option object for font weight configuration of text. Defines whether font weight will be automatically updated when the device's font weight category changes. The default value is true. True means font weight will be automatically updated when the device's font weight category changes. False means font weight will not be automatically updated when the device's font weight category changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Returns the enableDeviceFontWeightCategory flag. |

### OH_ArkUI_FontConfigs_Create()

```c
OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()
```

**Description**

Create an option object for font configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs*](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | A pointer to the option object. |

### OH_ArkUI_FontConfigs_Destroy()

```c
void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)
```

**Description**

Destroy an option object for font configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the option object to be destroyed. |

### OH_ArkUI_FontConfigs_SetFontWeightConfigs()

```c
void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)
```

**Description**

Sets the font weight configs of an option object for font configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the option object to be modified. |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* fontWeightConfigs | font weight configs. |

### OH_ArkUI_FontConfigs_GetFontWeightConfigs()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)
```

**Description**

Gets the font weight configs of an option object for font configuration of text.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the option object. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | Returns the font weight configs. |

### OH_ArkUI_NativeModule_LineSpacingOptions_Create()

```c
OH_ArkUI_NativeModule_LineSpacingOptions *OH_ArkUI_NativeModule_LineSpacingOptions_Create()
```

**Description**

Creates a line spacing options object for text. When the object is no longer used, call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy it.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions *](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) | Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |

### OH_ArkUI_NativeModule_LineSpacingOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LineSpacingOptions_Destroy(OH_ArkUI_NativeModule_LineSpacingOptions *options)
```

**Description**

Destroys the line spacing options object.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | [in] Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |

### OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines(OH_ArkUI_NativeModule_LineSpacingOptions *options, bool onlyBetweenLines)
```

**Description**

Sets the onlyBetweenLines parameter for the line spacing options. When set to true, line spacing is only applied between lines, not for the first and last lines. When set to false, line spacing is applied uniformly to all lines.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | [in] Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |
| bool onlyBetweenLines | [in] Whether line spacing is only applied between lines. True means only between lines, false means uniformly to all lines. The default value is false. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <ul>      <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if the options parameter is null.</li>      </ul> |

### OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines(const OH_ArkUI_NativeModule_LineSpacingOptions *options, bool *onlyBetweenLines)
```

**Description**

Gets the onlyBetweenLines parameter from the line spacing options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | [in] Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |
| bool *onlyBetweenLines | [out] Output parameter. Pointer to a bool variable to receive the value. True means only between lines, false means uniformly to all lines. The default value is false. |

**Returns**:

| Type | Description |
| -- | -- |
| ArkUI_ErrorCode | Result code.      <ul>      <li>{@link ARKUI_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>    <li>{@link ARKUI_ERROR_CODE_PARAM_INVALID} if any parameter is null.</li>      </ul> |


