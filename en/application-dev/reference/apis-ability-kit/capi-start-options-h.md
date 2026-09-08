# start_options.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhu-feimo; @yangxuguang-huawei-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=d067d0e28903a909bd18e16fb4e6ef9702d944d0 translatedAt=2026-09-03T09:08:53.019Z pushedAt=2026-09-05T10:47:30.159Z -->

## Overview

Provides the application startup parameter data structure [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) and related set and get functions, used to configure window parameters when starting an Ability. It supports setting the window mode, position, size, display effect, and style, and supports scenarios such as different window modes, multi-screen display, animation effects, and custom window icons.

**File to include**: <AbilityKit/ability_runtime/start_options.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 17

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) | AbilityRuntime_StartOptions | StartOptions struct.|

### Functions

| Name| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)](#oh_abilityruntime_getstartoptionswindowmodevalue) | Obtains the window mode when starting an ability.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)](#oh_abilityruntime_getstartoptionsdisplayidvalue) | Obtains the display ID of the screen where the window is located when starting an ability.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)](#oh_abilityruntime_getstartoptionswithanimationvalue) | Obtains whether the window has an animation effect when starting an ability.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)](#oh_abilityruntime_getstartoptionswindowleftvalue) | Obtains the left position of the window when starting an ability. The unit is px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)](#oh_abilityruntime_getstartoptionswindowtopvalue) | Obtains the top position of the window when starting an ability. The unit is px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)](#oh_abilityruntime_getstartoptionswindowheightvalue) | Obtains the height of the window when starting an ability. The unit is px. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)](#oh_abilityruntime_getstartoptionswindowwidthvalue) | Obtains the width of the window when starting an ability. The unit is px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibilityvalue) | Obtains the display mode of the window and dock bar icon when starting an ability. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolorvalue) | Obtains the background color of the window when starting an ability. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)](#oh_abilityruntime_getstartoptionssupportedwindowmodesvalue) | Obtains the window modes supported by the component when starting an ability. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidthvalue) | Obtains the minimum width of the window when starting an ability. The unit is vp.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidthvalue) | Obtains the maximum width of the window when starting an ability. The unit is vp. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheightvalue) | Obtains the minimum height of the window when starting an ability. The unit is vp. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheightvalue) | Obtains the maximum height of the window when starting an ability. The unit is vp. |
| [AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)](#oh_abilityruntime_createstartoptions) | Creates an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)](#oh_abilityruntime_destroystartoptions) | Destroys an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_WindowMode windowMode)](#oh_abilityruntime_setstartoptionswindowmode) | Sets the window mode for starting an ability.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_WindowMode &windowMode)](#oh_abilityruntime_getstartoptionswindowmode) | Obtains the window mode when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)](#oh_abilityruntime_getstartoptionswindowmodevalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions,int32_t displayId)](#oh_abilityruntime_setstartoptionsdisplayid) | Sets the ID of the display where the window is launched when the ability is started.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions,int32_t &displayId)](#oh_abilityruntime_getstartoptionsdisplayid) | Obtains the display ID of the screen where the window is located when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)](#oh_abilityruntime_getstartoptionsdisplayidvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions,bool withAnimation)](#oh_abilityruntime_setstartoptionswithanimation) | Sets whether to use animation effects when an ability is started.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions,bool &withAnimation)](#oh_abilityruntime_getstartoptionswithanimation) | Obtains whether the window has an animation effect when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)](#oh_abilityruntime_getstartoptionswithanimationvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions,int32_t windowLeft)](#oh_abilityruntime_setstartoptionswindowleft) | Sets the left position of the window when the ability is started, in px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions,int32_t &windowLeft)](#oh_abilityruntime_getstartoptionswindowleft) | Obtains the left position of the window when starting an ability. The unit is px. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)](#oh_abilityruntime_getstartoptionswindowleftvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions,int32_t windowTop)](#oh_abilityruntime_setstartoptionswindowtop) | Sets the top position of the window when the ability is started, in px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions,int32_t &windowTop)](#oh_abilityruntime_getstartoptionswindowtop) | Obtains the top position of the window when starting an ability. The unit is px. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)](#oh_abilityruntime_getstartoptionswindowtopvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions,int32_t windowHeight)](#oh_abilityruntime_setstartoptionswindowheight) | Sets the height of the window when the ability is started, in px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions,int32_t &windowHeight)](#oh_abilityruntime_getstartoptionswindowheight) | Obtains the height of the window when starting an ability. The unit is px. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)](#oh_abilityruntime_getstartoptionswindowheightvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions,int32_t windowWidth)](#oh_abilityruntime_setstartoptionswindowwidth) | Sets the width of the window when the ability is started, in px.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions,int32_t &windowWidth)](#oh_abilityruntime_getstartoptionswindowwidth) | Obtains the width of the window when starting an ability. The unit is px. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)](#oh_abilityruntime_getstartoptionswindowwidthvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_StartVisibility startVisibility)](#oh_abilityruntime_setstartoptionsstartvisibility) | Sets the visibility of the window and dock bar icons when the ability is started.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_StartVisibility &startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibility) | Obtains the display mode of the window and dock bar icon when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibilityvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions,OH_PixelmapNative *startWindowIcon)](#oh_abilityruntime_setstartoptionsstartwindowicon) | Sets the window start icon when starting an ability. The image data size limit is 600 MB. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions,OH_PixelmapNative **startWindowIcon)](#oh_abilityruntime_getstartoptionsstartwindowicon) | Obtains the startup icon of the window when the ability is started.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)](#oh_abilityruntime_setstartoptionsstartwindowbackgroundcolor) | Sets the background color of the window when the ability is started. If this function is not called, the value of **startWindowBackground** configured under **abilities** in the **module.json5** file corresponding to the UIAbility is used by default.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t &size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolor) | Obtains the background color of the window when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolorvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes,size_t size)](#oh_abilityruntime_setstartoptionssupportedwindowmodes) | Sets the window modes supported by the ability when it is started. If this function is not called, the value of **supportWindowMode** configured under **abilities** in the **module.json5** file corresponding to the UIAbility is used by default.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes,size_t &size)](#oh_abilityruntime_getstartoptionssupportedwindowmodes) | Obtains the window modes supported by the component when starting an ability. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)](#oh_abilityruntime_getstartoptionssupportedwindowmodesvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)](#oh_abilityruntime_setstartoptionsminwindowwidth) | Sets the minimum width of the window when the ability is started, in vp.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t &minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidth) | Obtains the minimum width of the window when starting an ability. The unit is vp. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidthvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)](#oh_abilityruntime_setstartoptionsmaxwindowwidth) | Sets the maximum width of the window when the ability is started, in vp.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t &maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidth) | Obtains the maximum width of the window when starting an ability. The unit is vp. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidthvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)](#oh_abilityruntime_setstartoptionsminwindowheight) | Sets the minimum height of the window when the ability is started, in vp.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t &minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheight) | Obtains the minimum height of the window when starting an ability. The unit is vp. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheightvalue). |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)](#oh_abilityruntime_setstartoptionsmaxwindowheight) | Sets the maximum height of the window when the ability is started, in vp.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t &maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheight) | Obtains the maximum height of the window when starting an ability. The unit is vp. Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheightvalue). |

## Function Description

### OH_AbilityRuntime_GetStartOptionsWindowModeValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)
```

**Description**

Obtains the window mode when starting an Ability.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | AbilityRuntime_StartOptions object. |
| [AbilityRuntime_WindowMode](capi-context-constant-h.md#abilityruntime_windowmode) *windowMode | Pointer to the window mode when starting an Ability. For the value range, see AbilityRuntime_WindowMode. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or windowMode is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    AbilityRuntime_WindowMode windowMode = ABILITY_RUNTIME_WINDOW_MODE_UNDEFINED;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowModeValue(options, &windowMode);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsDisplayIdValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)
```

**Description**

Obtains the display ID of the screen where the window is located when the Ability is started.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to the AbilityRuntime_StartOptions object. |
| int32_t *displayId | Pointer to the display ID of the screen where the window is located when the Ability is started. |

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or displayId is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t displayId = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsDisplayIdValue(options, &displayId);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWithAnimationValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)
```

**Description**

Obtains whether there is an animation effect when starting an ability.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| bool *withAnimation | Pointer to the parameter indicating whether there is an animation effect when starting an ability. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR** if the API call is successful.<br>Returns **ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID** if StartOptions is null or withAnimation is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    bool withAnimation = false;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWithAnimationValue(options, &withAnimation);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowLeftValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)
```

**Description**

Obtains the left position of the window when starting an ability, in px.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t *windowLeft | Pointer to the left position of the window when starting an ability, in px.|

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or windowLeft is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t windowLeft = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowLeftValue(options, &windowLeft);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowTopValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)
```

**Description**

Obtains the top position of the window when the ability is started, in px.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| int32_t *windowTop | Pointer to the top position of the window when the ability is started, in px. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or windowTop is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t windowTop = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowTopValue(options, &windowTop);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)
```

**Description**

Obtains the window height when the ability is started, in px.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t *windowHeight | Pointer to the window height when the ability is started, in px. |

**Returns:**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: StartOptions is null, or windowHeight is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t windowHeight = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowHeightValue(options, &windowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)
```

**Description**

Obtains the window width when an ability is started, in px.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| int32_t *windowWidth | Pointer to the window width when an ability is started, in px. |

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API is called successfully.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or windowWidth is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t windowWidth = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowWidthValue(options, &windowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsStartVisibilityValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)
```

**Description**

Obtains the display mode of the window and dock bar icon when an ability is started.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_StartVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) *startVisibility | Pointer to the display mode of the window and dock bar icon when an ability is started. For the value range, see AbilityRuntime_StartVisibility.|

**Return**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or startVisibility is a null pointer.|

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    AbilityRuntime_StartVisibility visibility = ABILITY_RUNTIME_HIDE_UPON_START;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(options, &visibility);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)
```

**Description**

Obtains the window background color when the ability is started.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | AbilityRuntime_StartOptions object. |
| char **startWindowBackgroundColor | Pointer to the secondary pointer to the UTF-8 string of the obtained window background color. It must not be null and must point to a null pointer before the call. The color is in ARGB format, for example, `#E5FFFFFF`. After use, call free to release it. |
| size_t *size | Pointer to the length of the obtained window background color string. It must not be null and does not include the terminating null character. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | When **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR** is returned, it indicates that the interface call is successful.<br>When **ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID** is returned, it indicates that any parameter is invalid.<br>When **ABILITY_RUNTIME_ERROR_CODE_INTERNAL** is returned, it indicates an internal error that the developer cannot recover, such as an internal malloc error. |

**Example:**

```c
#include <stdlib.h>

#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    char *startWindowBackgroundColor = NULL;
    size_t size = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(options,
        &startWindowBackgroundColor, &size);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    if (startWindowBackgroundColor != NULL) {
        // Destroy startWindowBackgroundColor to prevent memory leaks.
        free(startWindowBackgroundColor);
        startWindowBackgroundColor = NULL;
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)
```

**Description**

Obtains the window modes supported by the component when the ability is started.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | AbilityRuntime_StartOptions object. |
| [AbilityRuntime_SupportedWindowMode](capi-context-constant-h.md#abilityruntime_supportedwindowmode) **supportedWindowModes | Double pointer to the pointer to the array of window modes supported by the component. It must not be null and must point to a null pointer before the call. For the value range, see AbilityRuntime_SupportedWindowMode. After use, call free to release it. |
| size_t *size | Pointer to the number of window modes supported by the component. It must not be null. |

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | When ABILITY_RUNTIME_ERROR_CODE_NO_ERROR is returned, it indicates that the interface call is successful.<br>When ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID is returned, it indicates that any parameter is invalid.<br>When ABILITY_RUNTIME_ERROR_CODE_INTERNAL is returned, it indicates an internal error that the developer cannot recover from, such as an internal malloc call error. |

**Example:**

```c
#include <stdlib.h>

#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    AbilityRuntime_SupportedWindowMode *supportedWindowModes = NULL;
    size_t size = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(options,
        &supportedWindowModes, &size);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    if (supportedWindowModes != NULL) {
        // Destroy supportedWindowModes to prevent memory leaks.
        free(supportedWindowModes);
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)
```

**Description**

Obtains the minimum width of the window when the ability is started, in vp.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| int32_t *minWindowWidth | Pointer to the minimum width of the window when the ability is started, in vp. |

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or minWindowWidth is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t minWindowWidth = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(options, &minWindowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)
```

**Description**

Obtains the maximum width of the window when the ability is started, in vp.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| int32_t *maxWindowWidth | Pointer to the maximum width of the window when the ability is started, in vp. |

**Returns**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or maxWindowWidth is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t maxWindowWidth = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(options, &maxWindowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)
```

**Description**

Obtains the minimum height of the window when the ability is started, in vp.

**Since:** 26.0.0

**Parameters**

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object. |
| int32_t *minWindowHeight | Pointer to the minimum height of the window when the ability is started, in vp. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or minWindowHeight is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t minWindowHeight = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(options, &minWindowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)
```

**Description**

Obtains the maximum height of the window when the ability is started, in vp.

**Since:** 26.0.0

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t *maxWindowHeight | Pointer to the maximum height of the window when the ability is started, in vp. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: StartOptions is null, or maxWindowHeight is a null pointer. |

**Example:**

```c
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == NULL) {
        // Record the error log and perform other business processing.
        return;
    }

    int32_t maxWindowHeight = 0;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(options, &maxWindowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
    }

    // Destroy options to prevent memory leaks.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_CreateStartOptions()

```c
AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)
```

**Description**

Creates an [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) object.

**Since**: 17

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md)* | Pointer to the AbilityRuntime_StartOptions object created.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void createStartOptionsTest()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_DestroyStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)
```

**Description**

Destroys an [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) object.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) **startOptions | Double pointer to the AbilityRuntime_StartOptions object.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void destroyStartOptionsTest()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWindowMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_WindowMode windowMode)
```

**Description**

Sets the window mode for starting an ability.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_WindowMode](capi-context-constant-h.md#abilityruntime_windowmode) windowMode | Window mode. For details about the available options, see **AbilityRuntime_WindowMode**.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr, or **WindowMode** is invalid.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window mode when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWindowMode(options,
        ABILITY_RUNTIME_WINDOW_MODE_FULL_SCREEN);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowMode()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_WindowMode &windowMode)
```

**Description**

Obtains the window mode for starting an ability.

> **NOTE**
>
> This API is supported only for C++ compilation. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)](#oh_abilityruntime_getstartoptionswindowmodevalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_WindowMode](capi-context-constant-h.md#abilityruntime_windowmode) windowMode | Used to obtain the set window mode. For the value range, see AbilityRuntime_WindowMode. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    AbilityRuntime_WindowMode windowMode = ABILITY_RUNTIME_WINDOW_MODE_UNDEFINED;
    // Obtain the window mode when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowMode(options, windowMode);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsDisplayId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions,int32_t displayId)
```

**Description**

Sets the ID of the display where the window is launched when the ability is started.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t displayId | Display ID.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the display ID of the screen where the window is located when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsDisplayId(options, 1);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsDisplayId()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions,int32_t &displayId)
```

**Description**

Obtains the ID of the display where the window is launched when the ability is started.

> **NOTE**
>
> This API is supported only for C++ compilation. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)](#oh_abilityruntime_getstartoptionsdisplayidvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &displayId | Used to obtain the set display ID. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t displayId = 0;
    // Obtain the display ID of the screen where the window is located when starting the Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsDisplayId(options, displayId);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWithAnimation()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions,bool withAnimation)
```

**Description**

Sets whether to use animation effects when an ability is started.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| bool withAnimation | Whether to use animation effects.<br>**true** to use, **false** otherwise.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the animation effect when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWithAnimation(options, true);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWithAnimation()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions,bool &withAnimation)
```

**Description**

Checks whether animation effects are used when an ability is started.

> **NOTE**
>
> This API is supported only for C++ compilation. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)](#oh_abilityruntime_getstartoptionswithanimationvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| bool &withAnimation | Whether animation effects are used.<br>**true** if used, **false** otherwise. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    bool withAnimation = false;
    // Obtain whether it has an animation effect when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWithAnimation(options, withAnimation);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWindowLeft()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions,int32_t windowLeft)
```

**Description**

Sets the left position of the window when the ability is started, in px.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t windowLeft | Left position of the window, in px.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the left position of the window when starting the Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWindowLeft(options, 200);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowLeft()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions,int32_t &windowLeft)
```

**Description**

Obtains the left position of the window when the ability is started, in px.

> **NOTE**
>
> This API is supported only for C++ compilation. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)](#oh_abilityruntime_getstartoptionswindowleftvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &windowLeft | Used to obtain the set window left position, in px. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t windowLeft = 0;
    // Obtain the left position of the window when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowLeft(options, windowLeft);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWindowTop()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions,int32_t windowTop)
```

**Description**

Sets the top position of the window when the ability is started, in px.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t windowTop | Top position of the window, in px.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the top position of the window when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWindowTop(options, 500);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowTop()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions,int32_t &windowTop)
```

**Description**

Obtains the top position of the window when the ability is started, in px.

> **NOTE**
>
> This API is supported only for C++ compilation. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)](#oh_abilityruntime_getstartoptionswindowtopvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &windowTop | used to obtain the set window top position, unit is px. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t windowTop = 0;
    // Obtain the top position of the window when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowTop(options, windowTop);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions,int32_t windowHeight)
```

**Description**

Sets the height of the window when the ability is started, in px.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t windowHeight | Window height, in px.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window height when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWindowHeight(options, 500);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowHeight()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions,int32_t &windowHeight)
```

**Description**

Obtains the height of the window when the ability is started, in px.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)](#oh_abilityruntime_getstartoptionswindowheightvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &windowHeight | Used to obtain the set window height, in px. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t windowHeight = 0;
    // Obtain the window height when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowHeight(options, windowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions,int32_t windowWidth)
```

**Description**

Sets the width of the window when the ability is started, in px.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t windowWidth | Window width, in px.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window width when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsWindowWidth(options, 500);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsWindowWidth()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions,int32_t &windowWidth)
```

**Description**

Obtains the width of the window when the ability is started, in px.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)](#oh_abilityruntime_getstartoptionswindowwidthvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &windowWidth | Used to obtain the set window width, in px. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t windowWidth = 0;
    // Obtain the window width when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsWindowWidth(options, windowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsStartVisibility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_StartVisibility startVisibility)
```

**Description**

Sets the visibility of the window and dock bar icons when the ability is started.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to the AbilityRuntime_StartOptions object, which contains the display mode configuration information when starting an ability. |
| [AbilityRuntime_StartVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) startVisibility | Visibility. For details about the available options, see **AbilityRuntime_StartVisibility**.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The setting is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr, or **startVisibility** is not an enumerated value of **AbilityRuntime_StartVisibility**.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the display mode of the window and dock bar icon when starting an ability.
    AbilityRuntime_StartVisibility visibility = AbilityRuntime_StartVisibility::ABILITY_RUNTIME_SHOW_UPON_START;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsStartVisibility(options, visibility);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsStartVisibility()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions,AbilityRuntime_StartVisibility &startVisibility)
```

**Description**

Obtains the visibility of the window and dock bar icons when the ability is started.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibilityvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to the AbilityRuntime_StartOptions object. |
| [AbilityRuntime_StartVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) &startVisibility | Used to obtain the set display mode of the window and dock bar icon. For the value range, see AbilityRuntime_StartVisibility. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The retrieval is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr, or **startVisibility** is empty.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    AbilityRuntime_StartVisibility visibility;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsStartVisibility(options, visibility);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions,OH_PixelmapNative *startWindowIcon)
```

**Description**

Sets the window start icon when starting an Ability. The image data size limit is 600 MB.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| OH_PixelmapNative *startWindowIcon | Window start icon when starting an Ability. The image data size limit is 600 MB. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API call is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or startWindowIcon is a null pointer. |

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    uint8_t data[96];
    size_t dataSize = 96;
    for (int i = 0; i < dataSize; i++) {
        data[i] = i + 1;
    }

    // Create a parameter structure instance and set parameters.
    OH_Pixelmap_InitializationOptions *createOpts = nullptr;
    OH_PixelmapInitializationOptions_Create(&createOpts);
    OH_PixelmapInitializationOptions_SetWidth(createOpts, 6);
    OH_PixelmapInitializationOptions_SetHeight(createOpts, 4);
    OH_PixelmapInitializationOptions_SetPixelFormat(createOpts, PIXEL_FORMAT_RGBA_8888);
    OH_PixelmapInitializationOptions_SetAlphaType(createOpts, PIXELMAP_ALPHA_TYPE_UNKNOWN);

    // Create a PixelMap instance.
    OH_PixelmapNative *startWindowIcon = nullptr;
    Image_ErrorCode errCode = OH_PixelmapNative_CreatePixelmap(data, dataSize, createOpts, &startWindowIcon);
    if (errCode != IMAGE_SUCCESS) {
        // Record error logs and other service processing.

        // Destroy createOpts to prevent memory leakage.
        OH_PixelmapInitializationOptions_Release(createOpts);
        return;
    }

    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.

        // Destroy createOpts to prevent memory leakage.
        OH_PixelmapInitializationOptions_Release(createOpts);

        // Destroy startWindowIcon to prevent memory leakage.
        OH_PixelmapNative_Release(startWindowIcon);
        return;
    }

    // Set the window start icon when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsStartWindowIcon(options, startWindowIcon);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy createOpts to prevent memory leakage.
    OH_PixelmapInitializationOptions_Release(createOpts);

    // Destroy startWindowIcon to prevent memory leakage.
    OH_PixelmapNative_Release(startWindowIcon);

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions,OH_PixelmapNative **startWindowIcon)
```

**Description**

Obtains the startup icon of the window when the ability is started.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| OH_PixelmapNative **startWindowIcon | Used to obtain the window start icon when starting an Ability. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API is called successfully.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null, or startWindowIcon is not set to a null pointer. |

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    OH_PixelmapNative *startWindowIcon = nullptr;
    // Obtain the window start icon when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsStartWindowIcon(options, &startWindowIcon);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy startWindowIcon to prevent memory leakage.
    OH_PixelmapNative_Release(startWindowIcon);

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)
```

**Description**

Sets the window background color when starting an Ability. If not set, the startWindowBackground field of the [abilities tag](../../quick-start/module-configuration-file.md#abilities) in the [module.json5 configuration file](../../quick-start/module-configuration-file.md) is used by default.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| const char *startWindowBackgroundColor | Window background color when the Ability is started. Fixed in ARGB format, for example, `#E5FFFFFF`. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | When ABILITY_RUNTIME_ERROR_CODE_NO_ERROR is returned, it indicates that the interface call is successful.<br>When ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID is returned, it indicates that StartOptions is null, or startWindowBackgroundColor is a null pointer. |

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window background color when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(options, "#00000000");
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColor()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t &size)
```

**Description**

Obtains the window background color when starting an Ability. When starting a UIAbility, if this field is not set, the startWindowBackground field of the abilities tag in the module.json5 configuration file is used by default for the background color displayed on the startup page.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolorvalue)

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| char **startWindowBackgroundColor | Used to obtain the window background color when starting an Ability. Fixed in ARGB format, for example, `#E5FFFFFF`. |
| size_t &size | Size of the background color.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | When ABILITY_RUNTIME_ERROR_CODE_NO_ERROR is returned, it indicates that the interface call succeeds.<br>When ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID is returned, it indicates that startOptions is null, or startWindowBackgroundColor is not set to a null pointer.<br>When ABILITY_RUNTIME_ERROR_CODE_INTERNAL is returned, it indicates an internal error that the developer cannot recover from, such as an internal malloc error or a string copy function error. |

**Example**

```cpp
#include <cstdlib>

#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    char *startWindowBackgroundColor = nullptr;
    size_t size = 0;
    // Obtain the window background color when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColor(options,
        &startWindowBackgroundColor, size);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    if (startWindowBackgroundColor != nullptr) {
        // Destroy startWindowBackgroundColor to prevent memory leakage.
        free(startWindowBackgroundColor);
        startWindowBackgroundColor = nullptr;
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsSupportedWindowModes()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes,size_t size)
```

**Description**

Sets the window modes supported by the component when starting an Ability. If this field is not configured, the value of the supportWindowMode field of the abilities tag in the module.json5 configuration file corresponding to the UIAbility is used by default.


**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_SupportedWindowMode](capi-context-constant-h.md#abilityruntime_supportedwindowmode) *supportedWindowModes | Pointer to the window modes supported. For details about the available options, see **AbilityRuntime_SupportedWindowMode**.|
| size_t size | Size of the window modes supported.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API is called successfully.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions or SupportedWindowModes is null, or size is 0. |

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    size_t supportedWindowModesSize = 3;
    AbilityRuntime_SupportedWindowMode supportedWindowModes[3] = {
        ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FULL_SCREEN,
        ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_SPLIT,
        ABILITY_RUNTIME_SUPPORTED_WINDOW_MODE_FLOATING,
    };
    // Set the window mode supported by the component when starting the ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(options,
        supportedWindowModes, supportedWindowModesSize);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsSupportedWindowModes()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes,size_t &size)
```

**Description**

Obtains the window modes supported by the component when starting an Ability. If this field is not configured, the value of the supportWindowMode field of the abilities tag in the module.json5 configuration file corresponding to the UIAbility is used by default.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)](#oh_abilityruntime_getstartoptionssupportedwindowmodesvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| [AbilityRuntime_SupportedWindowMode](capi-context-constant-h.md#abilityruntime_supportedwindowmode) **supportedWindowModes | Double pointer to the window modes supported. For details about the available options, see **AbilityRuntime_SupportedWindowMode**.|
| size_t &size | Size of the window modes supported by the component. |

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the API is called successfully.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if StartOptions is null or supportedWindowModes is a non-null pointer.<br>Returns ABILITY_RUNTIME_ERROR_CODE_INTERNAL if an internal error that the developer cannot recover from occurs, such as an internal malloc error. |

**Example**

```cpp
#include <cstdlib>

#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    AbilityRuntime_SupportedWindowMode *supportedWindowModes = nullptr;
    size_t size = 0;
    // Obtain the window mode supported by the component when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsSupportedWindowModes(options,
        &supportedWindowModes, size);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    if (supportedWindowModes != nullptr) {
        // Destroy supportedWindowModes to prevent memory leakage.
        free(supportedWindowModes);
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsMinWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)
```

**Description**

Sets the minimum width of the window when the ability is started, in vp.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t minWindowWidth | Minimum width of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the minimum width of the window when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsMinWindowWidth(options, 100);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMinWindowWidth()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t &minWindowWidth)
```

**Description**

Obtains the minimum width of the window when the ability is started, in vp.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidthvalue)

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &minWindowWidth | Minimum width of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t minWindowWidth = 0;
    // Obtain the minimum width of the window when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMinWindowWidth(options, minWindowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsMaxWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)
```

**Description**

Sets the maximum width of the window when the ability is started, in vp.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t maxWindowWidth | Maximum width of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window maximum width when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(options, 100);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMaxWindowWidth()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t &maxWindowWidth)
```

**Description**

Obtains the maximum width of the window when the ability is started, in vp.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidthvalue)

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &maxWindowWidth | Maximum width of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t maxWindowWidth = 0;
    // Obtain the window maximum width when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMaxWindowWidth(options, maxWindowWidth);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsMinWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)
```

**Description**

Sets the minimum height of the window when the ability is started, in vp.

**Since**: 17

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t minWindowHeight | Minimum height of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the minimum window height when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsMinWindowHeight(options, 100);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMinWindowHeight()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t &minWindowHeight)
```

**Description**

Obtains the minimum height of the window when the ability is started, in vp.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheightvalue)

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &minWindowHeight | Minimum height of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t minWindowHeight = 0;
    // Obtain the minimum height of the window when starting an ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMinWindowHeight(options, minWindowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_SetStartOptionsMaxWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)
```

**Description**

Sets the maximum height of the window when the ability is started, in vp.

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t maxWindowHeight | Maximum height of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    // Set the window maximum height when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(options, 100);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_GetStartOptionsMaxWindowHeight()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t &maxWindowHeight)
```

**Description**

Obtains the maximum height of the window when the ability is started, in vp.

> **NOTE**
>
> Only C++ compilation is supported. To call it in a C environment, use [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheightvalue)

**Since**: 17


**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *startOptions | Pointer to an AbilityRuntime_StartOptions object.|
| int32_t &maxWindowHeight | Maximum height of the window, in vp.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The call is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The input parameter **StartOptions** is nullptr.|

**Example**

```cpp
#include <AbilityKit/ability_runtime/start_options.h>

void demo()
{
    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    int32_t maxWindowHeight = 0;
    // Obtain the window maximum height when starting an Ability.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetStartOptionsMaxWindowHeight(options, maxWindowHeight);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```
