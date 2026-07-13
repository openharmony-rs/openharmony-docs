# text.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Zhang-Dong-hui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines enumerations and APIs related to **Text**.

**File to include:** <arkui/node_attributes/text.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | OH_ArkUI_TextDataDetectorConfig | Defines the configuration of text entity recognition. Text entities refer to special content entities such as addresses and phone numbers.|
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | ArkUI_TextMarqueeOptions | Defines text marquee options.|
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | OH_ArkUI_FontWeightConfigs | Defines the font weight configurations of text. [OH_ArkUI_FontWeightConfigs_Create](#oh_arkui_fontweightconfigs_create) can be used to create a text font weight configuration object. [OH_ArkUI_FontWeightConfigs_Destroy](#oh_arkui_fontweightconfigs_destroy) can be used to destroy the text font weight configuration object. [OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight](#oh_arkui_fontweightconfigs_setenablevariablefontweight) can be used to set whether to enable variable font weight adjustment after the object is created. [OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight](#oh_arkui_fontweightconfigs_getenablevariablefontweight) can be used to check whether variable font weight adjustment is enabled after the object is created. [OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) can be used to set whether the text font weight is updated with the font weight level of the device after the object is created. [OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) can be used to check whether the text font weight is updated with the font weight level of the device after the object is created. When the object is used and is not a null pointer, if the user does not explicitly make the configuration through the API, the default values are used. When the object is a null pointer, the default values are not used, and the text font weight behavior is the same as that of the parent component.|
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | OH_ArkUI_FontConfigs | Defines the font configurations of text. [OH_ArkUI_FontConfigs_Create](#oh_arkui_fontconfigs_create) can be used to create a text font configuration object. [OH_ArkUI_FontConfigs_Destroy](#oh_arkui_fontconfigs_destroy) can be used to destroy the text font configuration object. [OH_ArkUI_FontConfigs_SetFontWeightConfigs](#oh_arkui_fontconfigs_setfontweightconfigs) can be used to set the text font weight after the object is created. [OH_ArkUI_FontConfigs_GetFontWeightConfigs](#oh_arkui_fontconfigs_getfontweightconfigs) can be used to view the text font weight after the object is created.|
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | OH_ArkUI_TextController | Defines a text component controller. [OH_ArkUI_TextController_Create](#oh_arkui_textcontroller_create) can be used to create a text component controller object, and [OH_ArkUI_TextController_Destroy](#oh_arkui_textcontroller_destroy) can be used to destroy the text component controller object. After the controller is created, [OH_ArkUI_TextController_SetStyledString](capi-native-type-h.md#oh_arkui_textcontroller_setstyledstring) can be used to set the styled string of the text component.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_FontStyle](#arkui_fontstyle) | ArkUI_FontStyle | Enumerates font styles.|
| [ArkUI_FontWeight](#arkui_fontweight) | ArkUI_FontWeight | Enumerates font weights.|
| [ArkUI_TextHeightAdaptivePolicy](#arkui_textheightadaptivepolicy) | ArkUI_TextHeightAdaptivePolicy | Enumerates how the adaptive height is determined for the text.|
| [ArkUI_TextDataDetectorType](#arkui_textdatadetectortype) | ArkUI_TextDataDetectorType | Enumerates the entity types of text recognition.|
| [ArkUI_MarqueeStartPolicy](#arkui_marqueestartpolicy) | ArkUI_MarqueeStartPolicy | Enumerates marquee startup policies.|
| [ArkUI_MarqueeUpdatePolicy](#arkui_marqueeupdatepolicy) | ArkUI_MarqueeUpdatePolicy | Enumerates marquee update policies.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()](#oh_arkui_textmarqueeoptions_create) | Creates a text marquee option object.|
| [void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_dispose) | Disposes of the pointer to the text marquee option object.|
| [void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)](#oh_arkui_textmarqueeoptions_setstart) | Sets whether to play the text marquee option.|
| [bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstart) | Obtains whether the text marquee option is played.|
| [void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)](#oh_arkui_textmarqueeoptions_setstep) | Sets the step of the text marquee option.|
| [float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstep) | Obtains the step of the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)](#oh_arkui_textmarqueeoptions_setspacing) | Sets the distance between the start and end items of the text marquee option.|
| [float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getspacing) | Obtains the distance between the start and end items of the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)](#oh_arkui_textmarqueeoptions_setloop) | Sets the number of repetitions for looping the text marquee option. The value **0** or negative value indicates infinite looping.|
| [int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getloop) | Obtains the number of repetitions for looping the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)](#oh_arkui_textmarqueeoptions_setfromstart) | Sets the direction for scrolling the text marquee option.|
| [bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfromstart) | Obtains the direction for scrolling the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)](#oh_arkui_textmarqueeoptions_setdelay) | Sets the delay of each loop for the text marquee option.|
| [int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getdelay) | Obtains the delay of each loop for the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)](#oh_arkui_textmarqueeoptions_setfadeout) | Sets whether the text marquee option supports a fade-out effect when the text is too long. When this parameter is set to **true**: if the text content exceeds the display range, a fade-out effect is applied to the edges of the partially visible text; if text is partially visible at both ends, the fade-out effect is applied to both ends. When the fade-out effect is enabled, the **NODE_CLIP** attribute in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) is automatically locked to **true** and cannot be set to **false**.|
| [bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getfadeout) | Obtains whether the text marquee option supports a fade-out effect when the text is too long.|
| [void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)](#oh_arkui_textmarqueeoptions_setstartpolicy) | Sets the startup policy of the text marquee option.|
| [ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getstartpolicy) | Obtains the startup policy of the text marquee option.|
| [void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)](#oh_arkui_textmarqueeoptions_setupdatepolicy) | Sets the update policy of the text marquee option.|
| [ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)](#oh_arkui_textmarqueeoptions_getupdatepolicy) | Obtains the update policy of the text marquee option.|
| [OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()](#oh_arkui_textdatadetectorconfig_create) | Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it.|
| [void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)](#oh_arkui_textdatadetectorconfig_destroy) | Destroys the text entity recognition configuration object.|
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()](#oh_arkui_fontweightconfigs_create) | Creates a text font weight configuration object.|
| [void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_destroy) | Destroys the text font weight configuration object.|
| [void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenablevariablefontweight) | Sets whether to enable variable font weight adjustment.|
| [bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenablevariablefontweight) | Obtains whether variable weight adjustment is enabled for the text font weight configuration object.|
| [void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)](#oh_arkui_fontweightconfigs_setenabledevicefontweightcategory) | Sets whether to automatically update the text font weight when the font weight level of the device changes.|
| [bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)](#oh_arkui_fontweightconfigs_getenabledevicefontweightcategory) | Obtains whether the text font weight is updated along with the font weight level of the device.|
| [OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()](#oh_arkui_fontconfigs_create) | Creates a text font configuration object.|
| [void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_destroy) | Destroys the text font configuration object.|
| [void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)](#oh_arkui_fontconfigs_setfontweightconfigs) | Sets the text font weight configurations for the text font configuration object.|
| [OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)](#oh_arkui_fontconfigs_getfontweightconfigs) | Obtains the text font weight configurations of the text font configuration object.|
| [OH_ArkUI_TextController* OH_ArkUI_TextController_Create()](#oh_arkui_textcontroller_create) | Creates a text controller object.|
| [void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)](#oh_arkui_textcontroller_destroy) | Destroys the text controller object.|

## Enum Description

### ArkUI_FontStyle

```c
enum ArkUI_FontStyle
```

**Description**

Enumerates font styles.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_FONT_STYLE_NORMAL = 0 | Standard font style.|
| ARKUI_FONT_STYLE_ITALIC = 1 | Italic font style.|

### ArkUI_FontWeight

```c
enum ArkUI_FontWeight
```

**Description**

Enumerates font weights.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_FONT_WEIGHT_W100 = 0 | 100 |
| ARKUI_FONT_WEIGHT_W200 = 1 | 200 |
| ARKUI_FONT_WEIGHT_W300 = 2 | 300 |
| ARKUI_FONT_WEIGHT_W400 = 3 | 400 |
| ARKUI_FONT_WEIGHT_W500 = 4 | 500 |
| ARKUI_FONT_WEIGHT_W600 = 5 | 600 |
| ARKUI_FONT_WEIGHT_W700 = 6 | 700 |
| ARKUI_FONT_WEIGHT_W800 = 7 | 800 |
| ARKUI_FONT_WEIGHT_W900 = 8 | 900 |
| ARKUI_FONT_WEIGHT_BOLD = 9 | The font weight is bold.|
| ARKUI_FONT_WEIGHT_NORMAL = 10 | The font weight is normal.|
| ARKUI_FONT_WEIGHT_BOLDER = 11 | The font weight is bolder.|
| ARKUI_FONT_WEIGHT_LIGHTER = 12 | The font weight is lighter.|
| ARKUI_FONT_WEIGHT_MEDIUM = 13 | The font weight is medium.|
| ARKUI_FONT_WEIGHT_REGULAR = 14 | The font weight is normal.|

### ArkUI_TextHeightAdaptivePolicy

```c
enum ArkUI_TextHeightAdaptivePolicy
```

**Description**

Enumerates how the adaptive height is determined for the text.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MAX_LINES_FIRST = 0 | Prioritize the **maxLines** settings.|
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_MIN_FONT_SIZE_FIRST = 1 | Prioritize the **minFontSize** settings.|
| ARKUI_TEXT_HEIGHT_ADAPTIVE_POLICY_LAYOUT_CONSTRAINT_FIRST = 2 | Prioritize the layout constraint settings in terms of height.|

### ArkUI_TextDataDetectorType

```c
enum ArkUI_TextDataDetectorType
```

**Description**

Enumerates the entity types of text recognition.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_TEXT_DATA_DETECTOR_TYPE_PHONE_NUMBER = 0 | Phone number.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_URL = 1 | URL.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_EMAIL = 2 | Email address.|
| ARKUI_TEXT_DATA_DETECTOR_TYPE_ADDRESS = 3 | Address.|

### ArkUI_MarqueeStartPolicy

```c
enum ArkUI_MarqueeStartPolicy
```

**Description**

Enumerates marquee startup policies.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_MARQUEESTARTPOLICY_DEFAULT = 0 | The marquee scrolls continuously by default.|
| ARKUI_MARQUEESTARTPOLICY_ONFOCUS = 1 | The marquee starts scrolling when it has focus or when the mouse hovers over it.|

### ArkUI_MarqueeUpdatePolicy

```c
enum ArkUI_MarqueeUpdatePolicy
```

**Description**

Enumerates marquee update policies.

**Since:** 23

| Value| Description|
| -- | -- |
| ARKUI_MARQUEEUPDATEPOLICY_DEFAULT = 0 | Restarts the marquee from the start position after the attributes of the marquee component are updated.|
| ARKUI_MARQUEEUPDATEPOLICY_PRESERVEPOSITION = 1 | Resumes the marquee from the current position after the attributes of the marquee component are updated.|


## Function Description

### OH_ArkUI_TextMarqueeOptions_Create()

```c
ArkUI_TextMarqueeOptions* OH_ArkUI_TextMarqueeOptions_Create()
```

**Description**

Creates a text marquee option object.

**Since:** 23

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions*](capi-arkui-nativemodule-arkui-textmarqueeoptions.md) | Pointer to the text marquee option object.|

### OH_ArkUI_TextMarqueeOptions_Dispose()

```c
void OH_ArkUI_TextMarqueeOptions_Dispose(ArkUI_TextMarqueeOptions* option)
```

**Description**

Disposes of the pointer to the text marquee option object.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

### OH_ArkUI_TextMarqueeOptions_SetStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetStart(ArkUI_TextMarqueeOptions* option, bool start)
```

**Description**

Sets whether to play the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| bool start | Whether to play the text marquee option. **true** indicates to play; **false** otherwise.|

### OH_ArkUI_TextMarqueeOptions_GetStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether the text marquee option is played.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the text marquee option is played. **true** indicates the text marquee option is played; **false** indicates the text marquee option is not played.|

### OH_ArkUI_TextMarqueeOptions_SetStep()

```c
void OH_ArkUI_TextMarqueeOptions_SetStep(ArkUI_TextMarqueeOptions* option, float step)
```

**Description**

Sets the step of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| float step | Step. The unit is vp.|

### OH_ArkUI_TextMarqueeOptions_GetStep()

```c
float OH_ArkUI_TextMarqueeOptions_GetStep(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the step of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Step. The unit is vp.|

### OH_ArkUI_TextMarqueeOptions_SetSpacing()

```c
void OH_ArkUI_TextMarqueeOptions_SetSpacing(ArkUI_TextMarqueeOptions* option, float spacing)
```

**Description**

Sets the distance between the start and end items of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| float spacing | Spacing between the start and end items. The unit is vp.|

### OH_ArkUI_TextMarqueeOptions_GetSpacing()

```c
float OH_ArkUI_TextMarqueeOptions_GetSpacing(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the distance between the start and end items of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Spacing between the start and end items. The unit is vp.|

### OH_ArkUI_TextMarqueeOptions_SetLoop()

```c
void OH_ArkUI_TextMarqueeOptions_SetLoop(ArkUI_TextMarqueeOptions* option, int32_t loop)
```

**Description**

Sets the number of repetitions for looping the text marquee option. The value **0** or negative value indicates infinite looping.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| int32_t loop | Number of loops.|

### OH_ArkUI_TextMarqueeOptions_GetLoop()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetLoop(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the number of repetitions for looping the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Number of loops.|

### OH_ArkUI_TextMarqueeOptions_SetFromStart()

```c
void OH_ArkUI_TextMarqueeOptions_SetFromStart(ArkUI_TextMarqueeOptions* option, bool fromStart)
```

**Description**

Sets the direction for scrolling the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| bool fromStart | Direction for scrolling the text marquee option. **true** to scroll from the start; **false** to scroll in reverse.|

### OH_ArkUI_TextMarqueeOptions_GetFromStart()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFromStart(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the direction for scrolling the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Direction for scrolling the text marquee option. **true** to scroll from the start; **false** to scroll in reverse.|

### OH_ArkUI_TextMarqueeOptions_SetDelay()

```c
void OH_ArkUI_TextMarqueeOptions_SetDelay(ArkUI_TextMarqueeOptions* option, int32_t delay)
```

**Description**

Sets the delay of each loop for the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| int32_t delay | Delay of each loop, in milliseconds.|

### OH_ArkUI_TextMarqueeOptions_GetDelay()

```c
int32_t OH_ArkUI_TextMarqueeOptions_GetDelay(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the delay of each loop for the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Delay of each loop, in milliseconds.|

### OH_ArkUI_TextMarqueeOptions_SetFadeout()

```c
void OH_ArkUI_TextMarqueeOptions_SetFadeout(ArkUI_TextMarqueeOptions* option, bool fadeout)
```

**Description**

Sets whether the text marquee option supports a fade-out effect when the text is too long. When this parameter is set to **true**: if the text content exceeds the display range, a fade-out effect is applied to the edges of the partially visible text;<br> if text is partially visible at both ends, the fade-out effect is applied to both ends.<br> When the fade-out effect is enabled, the **NODE_CLIP** attribute in [ArkUI_NodeAttributeType](capi-native-node-h.md#arkui_nodeattributetype) is automatically locked to **true** and cannot be set to **false**.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| bool fadeout | Whether the text marquee option supports a fade-out effect when the text is too long.<br>**true** to apply a fade-out effect when the text is too long; **false** otherwise.|

### OH_ArkUI_TextMarqueeOptions_GetFadeout()

```c
bool OH_ArkUI_TextMarqueeOptions_GetFadeout(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains whether the text marquee option supports a fade-out effect when the text is too long.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the text marquee option supports a fade-out effect when the text is too long.|

### OH_ArkUI_TextMarqueeOptions_SetStartPolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetStartPolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeStartPolicy startPolicy)
```

**Description**

Sets the startup policy of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) startPolicy | Startup policy.|

### OH_ArkUI_TextMarqueeOptions_GetStartPolicy()

```c
ArkUI_MarqueeStartPolicy OH_ArkUI_TextMarqueeOptions_GetStartPolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the startup policy of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MarqueeStartPolicy](capi-text-h.md#arkui_marqueestartpolicy) | Startup policy.|

### OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy()

```c
void OH_ArkUI_TextMarqueeOptions_SetUpdatePolicy(ArkUI_TextMarqueeOptions* option, ArkUI_MarqueeUpdatePolicy updatePolicy)
```

**Description**

Sets the update policy of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) updatePolicy | Update policy.|

### OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy()

```c
ArkUI_MarqueeUpdatePolicy OH_ArkUI_TextMarqueeOptions_GetUpdatePolicy(ArkUI_TextMarqueeOptions* option)
```

**Description**

Obtains the update policy of the text marquee option.

**Since:** 23

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_TextMarqueeOptions](capi-arkui-nativemodule-arkui-textmarqueeoptions.md)* option | Pointer to the text marquee option object.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_MarqueeUpdatePolicy](capi-text-h.md#arkui_marqueeupdatepolicy) | Update policy.|

### OH_ArkUI_TextDataDetectorConfig_Create()

```c
OH_ArkUI_TextDataDetectorConfig* OH_ArkUI_TextDataDetectorConfig_Create()
```

**Description**

Creates a text entity recognition configuration object. When the object is no longer used, call [OH_ArkUI_TextDataDetectorConfig_Destroy](capi-text-h.md#oh_arkui_textdatadetectorconfig_destroy) to destroy it.

**Since:** 24

**Returns**

| Type| Description|
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig*](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) | Pointer to the [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) object.|

### OH_ArkUI_TextDataDetectorConfig_Destroy()

```c
void OH_ArkUI_TextDataDetectorConfig_Destroy(OH_ArkUI_TextDataDetectorConfig* config)
```

**Description**

Destroys the text entity recognition configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md)* config | Pointer to the [OH_ArkUI_TextDataDetectorConfig](capi-arkui-nativemodule-oh-arkui-textdatadetectorconfig.md) object.|

### OH_ArkUI_FontWeightConfigs_Create()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontWeightConfigs_Create()
```

**Description**

Creates a text font weight configuration object.

**Since:** 24

**Returns**

| Type| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | Pointer to the text font weight configuration object. If the creation fails, a null pointer is returned.|

### OH_ArkUI_FontWeightConfigs_Destroy()

```c
void OH_ArkUI_FontWeightConfigs_Destroy(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Destroys the text font weight configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be destroyed.|

### OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets whether to enable variable font weight adjustment.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be modified.|
| bool enable | Whether to enable variable font weight adjustment. **true** indicates to enable variable font weight adjustment. If the value of **weight** is any integer in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used. **false** indicates to disable variable font weight adjustment. If the value of **weight** is an integer multiple of 100 in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used. The default value is **false**.|

### OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableVariableFontWeight(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Obtains whether variable weight adjustment is enabled for the text font weight configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether variable font weight adjustment is enabled.<br>        **true** indicates variable font weight adjustment is enabled. If the value of **weight** is any integer in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used.<br>         **false** indicates variable font weight adjustment is disabled. If the value of **weight** is an integer multiple of 100 in the range of [100, 900], the value of **weight** is used. Otherwise, the default value **400** is used.<br>         The default value is **false**. If the value of **weight** is not within the range of [100, 900], the default value **400** is used.|

### OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory()

```c
void OH_ArkUI_FontWeightConfigs_SetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option, bool enable)
```

**Description**

Sets whether to automatically update the text font weight when the font weight level of the device changes.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object to be modified.|
| bool enable | Whether to enable the text font weight to be updated along with the font weight level of the device. **true** indicates that the text font weight is automatically updated when the font weight level of the device changes. **false** indicates that the text font weight is not automatically updated when the font weight level of the device changes. The default value is **true**.|

### OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory()

```c
bool OH_ArkUI_FontWeightConfigs_GetEnableDeviceFontWeightCategory(OH_ArkUI_FontWeightConfigs* option)
```

**Description**

Obtains whether the text font weight is updated along with the font weight level of the device.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* option | Pointer to the text font weight configuration object.|

**Returns**

| Type| Description|
| -- | -- |
| bool | Whether the text font weight is updated along with the font weight level of the device.<br>         **true** indicates that the text font weight is automatically updated when the font weight level of the device changes.<br>         **false** indicates that the text font weight is not automatically updated when the font weight level of the device changes.|

### OH_ArkUI_FontConfigs_Create()

```c
OH_ArkUI_FontConfigs* OH_ArkUI_FontConfigs_Create()
```

**Description**

Creates a text font configuration object.

**Since:** 24

**Returns**

| Type| Description|
| -- | -- |
| [OH_ArkUI_FontConfigs*](capi-arkui-nativemodule-oh-arkui-fontconfigs.md) | Pointer to the text font configuration object. If the creation fails, a null pointer is returned.|

### OH_ArkUI_FontConfigs_Destroy()

```c
void OH_ArkUI_FontConfigs_Destroy(OH_ArkUI_FontConfigs* option)
```

**Description**

Destroys the text font configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object to be destroyed.|

### OH_ArkUI_FontConfigs_SetFontWeightConfigs()

```c
void OH_ArkUI_FontConfigs_SetFontWeightConfigs(OH_ArkUI_FontConfigs* option, OH_ArkUI_FontWeightConfigs* fontWeightConfigs)
```

**Description**

Sets the text font weight configurations for the text font configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object to be modified.|
| [OH_ArkUI_FontWeightConfigs](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md)* fontWeightConfigs | Pointer to the text font weight configuration object. When the value is not a null pointer, if the user does not explicitly make configurations, the default values of the parameters are used (that is, variable font weight adjustment is disabled by default, and the text font weight is updated based on the device font weight level by default). When the value is a null pointer, the default values are not used, and the text font weight behavior is the same as that of the parent component.|

### OH_ArkUI_FontConfigs_GetFontWeightConfigs()

```c
OH_ArkUI_FontWeightConfigs* OH_ArkUI_FontConfigs_GetFontWeightConfigs(OH_ArkUI_FontConfigs* option)
```

**Description**

Obtains the text font weight configurations of the text font configuration object.

**Since:** 24

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_FontConfigs](capi-arkui-nativemodule-oh-arkui-fontconfigs.md)* option | Pointer to the text font configuration object.|

**Returns**

| Type| Description|
| -- | -- |
| [OH_ArkUI_FontWeightConfigs*](capi-arkui-nativemodule-oh-arkui-fontweightconfigs.md) | Pointer to the text font weight configuration object.|

### OH_ArkUI_TextController_Create()

```c
OH_ArkUI_TextController* OH_ArkUI_TextController_Create()
```

**Description**

Creates a text controller object.

**Since:** 26.0.0

**Returns**

| Type| Description|
| -- | -- |
| [OH_ArkUI_TextController*](capi-arkui-nativemodule-oh-arkui-textcontroller.md) | Pointer to the text component controller object. If the creation fails, a null pointer is returned.|

### OH_ArkUI_TextController_Destroy()

```c
void OH_ArkUI_TextController_Destroy(OH_ArkUI_TextController* controller)
```

**Description**

Destroys the text controller object.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [OH_ArkUI_TextController](capi-arkui-nativemodule-oh-arkui-textcontroller.md)* controller | Pointer to the text component controller object.|
