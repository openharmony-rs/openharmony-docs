# text.h

## Overview

Defines enumerations and APIs related to **Text** for configuring text styles, controlling marquee effects, implementing text entity recognition, and managing text controllers. It is applicable to scenarios such as customizing text display effects, implementing dynamic text interaction, recognizing special entities in text (such as addresses and phone numbers), and precisely controlling text font weight. With these configuration APIs, you can flexibly control the display effects and interaction behaviors of text components to improve user experience.

**Library**: libace_ndk.z.so

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | OH_ArkUI_TextDataDetectorConfig | Defines the configuration for text entity detection. By setting the entity types to be detected (such as phone numbers, URLs, emails, addresses, and dates), the corresponding entity detection feature is enabled in the text component, and the detected entities are presented in an interactive format. This applies to scenarios such as automatically recognizing contact information in chat messages and extracting links from documents. |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | ArkUI_TextMarqueeOptions | Defines text marquee mode options, which are used to configure the display parameters of the text marquee effect. It is suitable for scenarios where long text content needs to be displayed cyclically in limited space, such as scrolling notification messages and scrolling titles, effectively solving the display problem when text exceeds the display area. |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | OH_ArkUI_TextController | Defines a text component controller, which is used to control and interact with the text component on the native side. You can create a controller object through [OH_ArkUI_TextController_Create](capi-text-h.md#oh_arkui_textcontroller_create). When the object is created, you must call [OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy) to destroy it and release resources after use. The two must be used in pairs; otherwise, memory leaks will occur. After the controller is created, you can use APIs such as OH_ArkUI_TextController_SetStyledString to set the styled string of the text component, implementing dynamic management and style control of the text content. This is applicable to scenarios where the text component needs to be operated at the native layer. |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | OH_ArkUI_FontWeightConfigs | Defines the font weight configurations of text. It is suitable for scenarios that require precise control over text font weight or where the text font weight needs to follow device font setting changes. You can create a text font weight configuration object through [OH_ArkUI_FontWeightConfigs_Create](capi-text-h.md#oh_arkui_fontweightconfigs_create), and must call [OH_ArkUI_FontWeightConfigs_Destroy](capi-text-h.md#oh_arkui_fontweightconfigs_destroy) to destroy the object and release resources after use to avoid memory leaks. After the configuration object is created, you can set and query the information through the following APIs: use [OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](capi-text-h.md#oh_arkui_fontweightconfigs_setenablevariablefontweight) to set whether to enable variable font weight adjustment, use [OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](capi-text-h.md#oh_arkui_fontweightconfigs_getenablevariablefontweight) to check whether variable font weight adjustment is enabled, use [OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](capi-text-h.md#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) to set whether the text font weight is updated with the font weight level of the device, and use [OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](capi-text-h.md#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) to check whether the text font weight is updated with the font weight level of the device. When this configuration object is used and is not a null pointer, if the user does not explicitly make the configuration through the APIs, each configuration item uses its default value (variable font weight adjustment is disabled by default, and text font weight is updated with the font weight level of the device by default). When this configuration object is a null pointer, the default values are not used, and the text font weight behavior is the same as that of the parent component. |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | OH_ArkUI_FontConfigs | Defines the font configurations of text. Currently, it supports setting and obtaining the font weight configuration through related APIs, and is applicable to scenarios that require custom font weight display effects. You can create a font configuration object through the [OH_ArkUI_FontConfigs_Create](capi-text-h.md#oh_arkui_fontconfigs_create) API and destroy it through the [OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) API. After the configurations are created, you can set and query them through the following APIs: set the font weight configuration through the [OH_ArkUI_FontConfigs_SetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_setfontweightconfigs) API, and obtain the font weight configuration through the [OH_ArkUI_FontConfigs_GetFontWeightConfigs](capi-text-h.md#oh_arkui_fontconfigs_getfontweightconfigs) API. |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) | OH_ArkUI_NativeModule_LineSpacingOptions | Defines a text line spacing option object, which is used to set whether the text line spacing takes effect only between lines. You can create a line spacing option object by calling [OH_ArkUI_NativeModule_LineSpacingOptions_Create](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_create). After the object is used, you must call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy it and release resources. The two APIs must be used in pairs; otherwise, a memory leak occurs. After the object is created, you can call [OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_setonlybetweenlines) to set whether the line spacing takes effect only between lines, and call [OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_getonlybetweenlines) to obtain the line spacing configuration. This struct is applicable to scenarios that require precise control over the display effect of text line spacing, such as text display where no line spacing is added to the first and last lines. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_FontStyle](#arkui_fontstyle) | ArkUI_FontStyle | Enumerates font styles. |
| [ArkUI_FontWeight](#arkui_fontweight) | ArkUI_FontWeight | Enumerates font weights. |
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy) | ArkUI_TextHeightAdaptivePolicy | Enumerates how the adaptive height is determined for the text. |
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype) | ArkUI_TextDataDetectorType | Enumerates the entity types of text recognition. |
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy) | ArkUI_MarqueeStartPolicy | Enumerates marquee startup policies. |
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) | ArkUI_MarqueeUpdatePolicy | Enumerates marquee update policies. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()](#oh_arkui_textmarqueeoptions_create) | Creates a text marquee option object. When the object is no longer used, call [OH_ArkUI_TextMarqueeOptions_Dispose](capi-text-h.md#oh_arkui_textmarqueeoptions_dispose) to dispose of it and release resources to avoid memory leaks. |
| [void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_dispose) | Disposes of the text marquee option object. This API must be used in pair with [OH_ArkUI_TextMarqueeOptions_Create](capi-text-h.md#oh_arkui_textmarqueeoptions_create); otherwise, memory leaks will occur. |
| [void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)](#oh_arkui_textmarqueeoptions_setstart) | Sets whether to play the text marquee option. |
| [bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstart) | Obtains whether the text marquee option is played. |
| [void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)](#oh_arkui_textmarqueeoptions_setstep) | Sets the step of the text marquee option. |
| [float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstep) | Obtains the step of the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)](#oh_arkui_textmarqueeoptions_setspacing) | Sets the distance between the start and end items of the text marquee option. |
| [float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getspacing) | Obtains the spacing between the start and end items of the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)](#oh_arkui_textmarqueeoptions_setloop) | Sets the number of repetitions for looping the text marquee option. The value less than or equal to **0**<br>indicates infinite looping. |
| [int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getloop) | Obtains the number of repetitions for looping the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)](#oh_arkui_textmarqueeoptions_setfromstart) | Sets the direction for scrolling the text marquee option. |
| [bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfromstart) | Obtains the direction for scrolling the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)](#oh_arkui_textmarqueeoptions_setdelay) | Sets the delay of each loop for the text marquee option. |
| [int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getdelay) | Obtains the delay of each loop for the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)](#oh_arkui_textmarqueeoptions_setfadeout) | Sets whether the text marquee option supports a fade-out effect when the text is too long. When this parameter is set to **true**: if the text content exceeds the display range, a fade-out effect is applied to the edges of the partially visible text; <br>if text is partially visible at both ends, the fade-out effect is applied to both ends. <br>When the fade-out effect is enabled, the **NODE_CLIP** attribute in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) is automatically locked to **true** and cannot be set to **false**. |
| [bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfadeout) | Obtains whether the text marquee option supports a fade-out effect when the text is too long. |
| [void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)](#oh_arkui_textmarqueeoptions_setstartpolicy) | Sets the start policy of the text marquee option. |
| [ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstartpolicy) | Obtains the startup policy of the text marquee option. |
| [void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)](#oh_arkui_textmarqueeoptions_setupdatepolicy) | Sets the update policy of the text marquee option. |
| [ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getupdatepolicy) | Obtains the update policy of the text marquee option. |
| [OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()](#oh_arkui_textdatadetectorconfig_create) | Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it and release resources to avoid memory leaks. |
| [void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)](#oh_arkui_textdatadetectorconfig_destroy) | Destroys the text entity recognition configuration object. |
| [OH_ArkUI_TextController* OH_ArkUI_TextController_Create()](#oh_arkui_textcontroller_create) | Creates a text controller object. When the object is no longer used, call [OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy) to destroy it and release resources to avoid memory leaks. |
| [void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)](#oh_arkui_textcontroller_destroy) | Destroys the text controller object. This API must be used in pair with [OH_ArkUI_TextController_Create](capi-text-h.md#oh_arkui_textcontroller_create); otherwise, memory leaks will occur. |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()](#oh_arkui_fontweightconfigs_create) | Creates a text font weight configuration object. When the object is no longer used, call [OH_ArkUI_FontWeightConfigs_Destroy](capi-text-h.md#oh_arkui_fontweightconfigs_destroy) to destroy it and release resources to avoid memory leaks. |
| [void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_destroy) | Destroys the text font weight configuration object. This API must be used in pair with [OH_ArkUI_FontWeightConfigs_Create](capi-text-h.md#oh_arkui_fontweightconfigs_create); otherwise, memory leaks will occur. |
| [void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenablevariablefontweight) | Sets whether to enable variable font weight adjustment. Variable font weight adjustment allows the font to display weight at any integer value from 100 to 900, enabling finer control over font weight. |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenablevariablefontweight) | Obtains whether variable font weight adjustment is enabled for the text font weight configuration object. |
| [void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) | Sets whether to automatically update the text font weight when the font weight level of the device changes. The font weight level of the device refers to the global font weight configuration in system settings, which users can adjust in system settings. |
| [bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) | Obtains whether the text font weight is updated along with the font weight level of the device. |
| [OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()](#oh_arkui_fontconfigs_create) | Creates a text font configuration object. When the object is no longer used, call [OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) to destroy it and release resources to avoid memory leaks. |
| [void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_destroy) | Destroys the text font configuration object. This API must be used in pair with [OH_ArkUI_FontConfigs_Create](capi-text-h.md#oh_arkui_fontconfigs_create); otherwise, memory leaks will occur. |
| [void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)](#oh_arkui_fontconfigs_setfontweightconfigs) | Sets the text font weight configurations for the text font configuration object. |
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_getfontweightconfigs) | Obtains the text font weight configurations of the text font configuration object. |
| [OH_ArkUI_NativeModule_LineSpacingOptions *OH_ArkUI_NativeModule_LineSpacingOptions_Create()](#oh_arkui_nativemodule_linespacingoptions_create) | Creates a text line spacing option object. After use, call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy the object. |
| [void OH_ArkUI_NativeModule_LineSpacingOptions_Destroy(OH_ArkUI_NativeModule_LineSpacingOptions *options)](#oh_arkui_nativemodule_linespacingoptions_destroy) | Destroys a text line spacing option object. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines(OH_ArkUI_NativeModule_LineSpacingOptions *options, bool onlyBetweenLines)](#oh_arkui_nativemodule_linespacingoptions_setonlybetweenlines) | Sets the **onlyBetweenLines** parameter of the text line spacing options. When set to **true**, the line spacing is applied only between lines, with no extra line spacing above the first line or below the last line. When set to **false**, line spacing also exists above the first line and below the last line. |
| [ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines(const OH_ArkUI_NativeModule_LineSpacingOptions *options, bool *onlyBetweenLines)](#oh_arkui_nativemodule_linespacingoptions_getonlybetweenlines) | Obtains the **onlyBetweenLines** parameter of the text line spacing options. |

## Enum type description

### ArkUI_FontStyle

```c
enum ArkUI_FontStyle
```

**Description**

Enumerates font styles.

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

Enumerates font weights.

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

Enumerates how the adaptive height is determined for the text.

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

Enumerates the entity types of text recognition.

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

Enumerates marquee startup policies.

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

Enumerates marquee update policies.

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

Creates a text marquee option object. When the object is no longer used, call [OH_ArkUI_TextMarqueeOptions_Dispose](capi-text-h.md#oh_arkui_textmarqueeoptions_dispose) to dispose of it and release resources to avoid memory leaks.

**Since**: 23

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions*](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | Pointer to the text marquee option object. If creation fails, a null pointer is returned. You need to call [OH_ArkUI_TextMarqueeOptions_Dispose](capi-text-h.md#oh_arkui_textmarqueeoptions_dispose) to dispose of it after use. |

### OH_ArkUI_TextMarqueeOptions_Dispose()

```c
void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)
```

**Description**

Disposes of the text marquee option object. This API must be used in pair with [OH_ArkUI_TextMarqueeOptions_Create](capi-text-h.md#oh_arkui_textmarqueeoptions_create); otherwise, memory leaks will occur.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

### OH_ArkUI_TextMarqueeOptions_SetStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)
```

**Description**

Sets whether to play the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| bool start | Whether to play the text marquee option. **true** indicates to play; **false** otherwise. Default value: **true**. |

### OH_ArkUI_TextMarqueeOptions_GetStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether the text marquee option is played.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the text marquee option is played. **true** indicates the text marquee option is played; **false** indicates the text marquee option is not played. |

### OH_ArkUI_TextMarqueeOptions_SetStep()

```c
void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)
```

**Description**

Sets the step of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| float step | Step length. Unit: vp. Value range: (0, Text length]. If the value is out of range, **4.0vp** is used. Default value: **4.0vp**. After the step is set, the marquee moves by this step value each time. A larger step results in faster scrolling. |

### OH_ArkUI_TextMarqueeOptions_GetStep()

```c
float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the step of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Step. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_SetSpacing()

```c
void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)
```

**Description**

Sets the distance between the start and end items of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| float spacing | Spacing between the start and end items. Unit: vp. Value range: [0, +∞). If the value is less than 0, the default value **48.0vp** is used. Default value: **48.0vp**. After setting, when the marquee finishes one scroll cycle, the distance between the start and end text is this spacing value. It is recommended to set this value based on the width of the display area. |

### OH_ArkUI_TextMarqueeOptions_GetSpacing()

```c
float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the spacing between the start and end items of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Spacing between the start and end items. The unit is vp. |

### OH_ArkUI_TextMarqueeOptions_SetLoop()

```c
void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)
```

**Description**

Sets the number of repetitions for looping the text marquee option. The value less than or equal to **0**<br>indicates infinite looping.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| int32_t loop | Number of loops. The value less than or equal to **0** indicates infinite looping. |

### OH_ArkUI_TextMarqueeOptions_GetLoop()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the number of repetitions for looping the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Number of loops. |

### OH_ArkUI_TextMarqueeOptions_SetFromStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)
```

**Description**

Sets the direction for scrolling the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| bool fromStart | Whether to scroll the text marquee option from the start. **true** to scroll from the start; **<br>false** to scroll in reverse. Default value: **true**. |

### OH_ArkUI_TextMarqueeOptions_GetFromStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the direction for scrolling the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the text marquee option is scrolled from the start. **true** to scroll from the start; **false** to scroll in reverse. |

### OH_ArkUI_TextMarqueeOptions_SetDelay()

```c
void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)
```

**Description**

Sets the delay of each loop for the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| int32_t delay | Delay of each loop, in milliseconds. Value range: [0, +∞). Default value: **0**. |

### OH_ArkUI_TextMarqueeOptions_GetDelay()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the delay of each loop for the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Delay of each loop, in milliseconds. |

### OH_ArkUI_TextMarqueeOptions_SetFadeout()

```c
void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)
```

**Description**

Sets whether the text marquee option supports a fade-out effect when the text is too long. When this parameter is set to **true**: if the text content exceeds the display range, a fade-out effect is applied to the edges of the partially visible text; <br>if text is partially visible at both ends, the fade-out effect is applied to both ends. <br>When the fade-out effect is enabled, the **NODE_CLIP** attribute in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) is automatically locked to **true** and cannot be set to **false**.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| bool fadeout | Whether the text marquee option supports a fade-out effect when the text is too long. <br>The value **true** means to apply a fade-out effect when the text is too long, in which case the **NODE_CLIP** attribute is automatically locked to **true** and cannot be set to **false**. <br>The value **false** means not to apply a fade-out effect. |

### OH_ArkUI_TextMarqueeOptions_GetFadeout()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether the text marquee option supports a fade-out effect when the text is too long.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the text marquee option supports a fade-out effect when the text is too long. The value **true** means the fade-out effect is supported, and **false** means the opposite. |

### OH_ArkUI_TextMarqueeOptions_SetStartPolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)
```

**Description**

Sets the start policy of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) startPolicy | Start policy. |

### OH_ArkUI_TextMarqueeOptions_GetStartPolicy()

```c
ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the startup policy of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) | Start policy. |

### OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)
```

**Description**

Sets the update policy of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) updatePolicy | Update policy. |

### OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy()

```c
ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the update policy of the text marquee option.

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) | Update policy. |

### OH_ArkUI_TextDataDetectorConfig_Create()

```c
OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()
```

**Description**

Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it and release resources to avoid memory leaks.

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig*](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | Pointer to the [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) object.<br> If creation fails, a null pointer is returned.<br> This object must be destroyed by calling [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) after use. |

### OH_ArkUI_TextDataDetectorConfig_Destroy()

```c
void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)
```

**Description**

Destroys the text entity recognition configuration object.

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

Creates a text controller object. When the object is no longer used, call [OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy) to destroy it and release resources to avoid memory leaks.

**Since**: 26.0.0

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_TextController*](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | Pointer to the text controller object. If creation fails, a null pointer is returned. After use, call [OH_ArkUI_TextController_Destroy](capi-text-h.md#oh_arkui_textcontroller_destroy) to destroy it. |

### OH_ArkUI_TextController_Destroy()

```c
void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)
```

**Description**

Destroys the text controller object. This API must be used in pair with [OH_ArkUI_TextController_Create](capi-text-h.md#oh_arkui_textcontroller_create); otherwise, memory leaks will occur.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | Pointer to the text component controller object. |

### OH_ArkUI_FontWeightConfigs_Create()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()
```

**Description**

Creates a text font weight configuration object. When the object is no longer used, call [OH_ArkUI_FontWeightConfigs_Destroy](capi-text-h.md#oh_arkui_fontweightconfigs_destroy) to destroy it and release resources to avoid memory leaks.

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | Pointer to the text font weight configuration object. If creation fails, a null pointer is returned. You need to call [OH_ArkUI_FontWeightConfigs_Destroy](capi-text-h.md#oh_arkui_fontweightconfigs_destroy) to destroy it after use. When the configuration object is a null pointer, no default value is applied, and the text font weight behavior remains consistent with that of the parent component. |

### OH_ArkUI_FontWeightConfigs_Destroy()

```c
void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Destroys the text font weight configuration object. This API must be used in pair with [OH_ArkUI_FontWeightConfigs_Create](capi-text-h.md#oh_arkui_fontweightconfigs_create); otherwise, memory leaks will occur.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be destroyed. |

### OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets whether to enable variable font weight adjustment. Variable font weight adjustment allows the font to display weight at any integer value from 100 to 900, enabling finer control over font weight.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be modified. |
| bool enable | Whether to enable variable font weight adjustment. The default value is **false**. The value true means to enable variable font weight adjustment. In this case, if the value of **weight** is any integer in the range [100, 900], the value is used; otherwise, the default value **400** is used. The value **false** means to disable variable font weight adjustment. In this case, the value of **weight** can only be multiples of 100 in the range [100, 900]; for a non-multiple of 100, the default value **400** is used. |

### OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Obtains whether variable font weight adjustment is enabled for the text font weight configuration object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether variable font weight adjustment is enabled. <br>**true** indicates variable font weight adjustment is enabled. If the value of **weight** is any integer in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used. <br>**false** indicates variable font weight adjustment is disabled. If the value of **weight** is an integer multiple of 100 in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used. <br>If the value of **weight** is not within the range of [100, 900], the default value **400** is used. |

### OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets whether to automatically update the text font weight when the font weight level of the device changes. The font weight level of the device refers to the global font weight configuration in system settings, which users can adjust in system settings.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be modified. |
| bool enable | Whether to enable the text font weight to be updated along with the font weight level of the device. **<br>true** indicates that the text font weight is automatically updated when the font weight level of the device changes. **false** indicates that the text font weight is not automatically updated when the font weight level of the device changes. The default value is **true**. |

### OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Obtains whether the text font weight is updated along with the font weight level of the device.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object. |

**Returns**:

| Type | Description |
| -- | -- |
| bool | Whether the text font weight is updated along with the font weight level of the device. <br>**true** indicates that the text font weight is automatically updated when the font weight level of the device changes. <br>**false** indicates that the text font weight is not automatically updated when the font weight level of the device changes. |

### OH_ArkUI_FontConfigs_Create()

```c
OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()
```

**Description**

Creates a text font configuration object. When the object is no longer used, call [OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) to destroy it and release resources to avoid memory leaks.

**Since**: 24

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs*](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | Pointer to the text font configuration object. If creation fails, a null pointer is returned. After use, call [OH_ArkUI_FontConfigs_Destroy](capi-text-h.md#oh_arkui_fontconfigs_destroy) to destroy it. |

### OH_ArkUI_FontConfigs_Destroy()

```c
void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)
```

**Description**

Destroys the text font configuration object. This API must be used in pair with [OH_ArkUI_FontConfigs_Create](capi-text-h.md#oh_arkui_fontconfigs_create); otherwise, memory leaks will occur.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object to be destroyed. |

### OH_ArkUI_FontConfigs_SetFontWeightConfigs()

```c
void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)
```

**Description**

Sets the text font weight configurations for the text font configuration object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object to be modified. |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* fontWeightConfigs | Pointer to the text font weight configuration. When this parameter is not a null pointer, if the user does not explicitly set it, each configuration item uses the default value (variable font weight adjustment is disabled by default, and the text font weight following the device font weight level update is enabled by default). When this parameter is a null pointer, the above default values are not applied, and the text font weight behavior keeps consistent with that of the parent component. |

### OH_ArkUI_FontConfigs_GetFontWeightConfigs()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)
```

**Description**

Obtains the text font weight configurations of the text font configuration object.

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object. If not set or set to a null pointer, a null pointer is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | Pointer to the text font weight configuration object. |

### OH_ArkUI_NativeModule_LineSpacingOptions_Create()

```c
OH_ArkUI_NativeModule_LineSpacingOptions *OH_ArkUI_NativeModule_LineSpacingOptions_Create()
```

**Description**

Creates a text line spacing option object. After use, call [OH_ArkUI_NativeModule_LineSpacingOptions_Destroy](capi-text-h.md#oh_arkui_nativemodule_linespacingoptions_destroy) to destroy the object.

**Since**: 26.0.1

**Resource release**: OH_ArkUI_NativeModule_LineSpacingOptions_Destroy {return}

**Returns**:

| Type | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions *](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) | Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |

### OH_ArkUI_NativeModule_LineSpacingOptions_Destroy()

```c
void OH_ArkUI_NativeModule_LineSpacingOptions_Destroy(OH_ArkUI_NativeModule_LineSpacingOptions *options)
```

**Description**

Destroys a text line spacing option object.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |

### OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_SetOnlyBetweenLines(OH_ArkUI_NativeModule_LineSpacingOptions *options, bool onlyBetweenLines)
```

**Description**

Sets the **onlyBetweenLines** parameter of the text line spacing options. When set to **true**, the line spacing is applied only between lines, with no extra line spacing above the first line or below the last line. When set to **false**, line spacing also exists above the first line and below the last line.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |
| bool onlyBetweenLines | Whether the line spacing is applied only between lines. The value **true** indicates that the line spacing is applied only between lines, and **false** indicates that line spacing also exists above the first line and below the last line. The default value is **false**. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.<br> Returns ARKUI_ERROR_CODE_PARAM_INVALID if the **options** parameter is a null pointer. |

### OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines()

```c
ArkUI_ErrorCode OH_ArkUI_NativeModule_LineSpacingOptions_GetOnlyBetweenLines(const OH_ArkUI_NativeModule_LineSpacingOptions *options, bool *onlyBetweenLines)
```

**Description**

Obtains the **onlyBetweenLines** parameter of the text line spacing options.

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) *options | Pointer to the [OH_ArkUI_NativeModule_LineSpacingOptions](capi-arkui-nativemodule-oh-arkui-nativemodule-linespacingoptions.md) object. |
| bool *onlyBetweenLines | Output parameter, which is a pointer to a variable of the bool type, used to receive the value. The value **true** indicates that the line spacing is applied only between lines, and the value **false**<br>indicates that the line spacing also exists above the first line and below the last line. The default value is **<br>false**. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_ErrorCode](capi-error-code-h.md#arkui_errorcode) | Returns ARKUI_ERROR_CODE_NO_ERROR if the operation is successful.<br> Returns ARKUI_ERROR_CODE_PARAM_INVALID if any parameter is a null pointer. |


