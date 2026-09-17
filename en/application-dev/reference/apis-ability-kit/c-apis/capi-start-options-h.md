# start_options.h

## Overview

Defines the start options APIs.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)](#oh_abilityruntime_createstartoptions) | Create start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)](#oh_abilityruntime_destroystartoptions) | Destroy input start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode windowMode)](#oh_abilityruntime_setstartoptionswindowmode) | Set window mode for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions, int32_t displayId)](#oh_abilityruntime_setstartoptionsdisplayid) | Set display id for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions, bool withAnimation)](#oh_abilityruntime_setstartoptionswithanimation) | Set with animation flag for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions, int32_t windowLeft)](#oh_abilityruntime_setstartoptionswindowleft) | Set window left for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions, int32_t windowTop)](#oh_abilityruntime_setstartoptionswindowtop) | Set window top for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t windowHeight)](#oh_abilityruntime_setstartoptionswindowheight) | Set window height for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t windowWidth)](#oh_abilityruntime_setstartoptionswindowwidth) | Set window width for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility startVisibility)](#oh_abilityruntime_setstartoptionsstartvisibility) | Set start visibility for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative *startWindowIcon)](#oh_abilityruntime_setstartoptionsstartwindowicon) | Set start window icon for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative **startWindowIcon)](#oh_abilityruntime_getstartoptionsstartwindowicon) | Get start window icon from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)](#oh_abilityruntime_setstartoptionsstartwindowbackgroundcolor) | Set start window background color for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes, size_t size)](#oh_abilityruntime_setstartoptionssupportedwindowmodes) | Set start window modes for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)](#oh_abilityruntime_setstartoptionsminwindowwidth) | Set min window width for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)](#oh_abilityruntime_setstartoptionsmaxwindowwidth) | Set max window width for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)](#oh_abilityruntime_setstartoptionsminwindowheight) | Set min window height for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)](#oh_abilityruntime_setstartoptionsmaxwindowheight) | Set max window height for start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)](#oh_abilityruntime_getstartoptionswindowmodevalue) | Get the window mode from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)](#oh_abilityruntime_getstartoptionsdisplayidvalue) | Get the display ID from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)](#oh_abilityruntime_getstartoptionswithanimationvalue) | Get whether animation is enabled from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)](#oh_abilityruntime_getstartoptionswindowleftvalue) | Get the window left position from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)](#oh_abilityruntime_getstartoptionswindowtopvalue) | Get the window top position from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)](#oh_abilityruntime_getstartoptionswindowheightvalue) | Get the window height from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)](#oh_abilityruntime_getstartoptionswindowwidthvalue) | Get the window width from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibilityvalue) | Get the start visibility from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolorvalue) | Get the start window background color from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)](#oh_abilityruntime_getstartoptionssupportedwindowmodesvalue) | Get the supported start window modes from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidthvalue) | Get the minimum window width from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidthvalue) | Get the maximum window width from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheightvalue) | Get the minimum window height from start options. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheightvalue) | Get the maximum window height from start options. |

## Function description

### OH_AbilityRuntime_CreateStartOptions()

```c
AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)
```

**Description**

Create start options.

**Since**: 17

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_StartOptions* | Returns the newly created AbilityRuntime_StartOptions object. |

### OH_AbilityRuntime_DestroyStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)
```

**Description**

Destroy input start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions **startOptions | The options to be deleted. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWindowMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode windowMode)
```

**Description**

Set window mode for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set window mode for. |
| AbilityRuntime_WindowMode windowMode | The window mode. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions or windowMode is invalid. |

### OH_AbilityRuntime_SetStartOptionsDisplayId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions, int32_t displayId)
```

**Description**

Set display id for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set display id for. |
| int32_t displayId | The display id. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWithAnimation()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions, bool withAnimation)
```

**Description**

Set with animation flag for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set with animation for. |
| bool withAnimation | The with animation. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWindowLeft()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions, int32_t windowLeft)
```

**Description**

Set window left for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set window left for. |
| int32_t windowLeft | The window left. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWindowTop()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions, int32_t windowTop)
```

**Description**

Set window top for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set window top for. |
| int32_t windowTop | The window top. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t windowHeight)
```

**Description**

Set window height for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set window height for. |
| int32_t windowHeight | The window height. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t windowWidth)
```

**Description**

Set window width for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set window width for. |
| int32_t windowWidth | The window width. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsStartVisibility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility startVisibility)
```

**Description**

Set start visibility for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set start visibility for. |
| AbilityRuntime_StartVisibility startVisibility | The start visibility. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative *startWindowIcon)
```

**Description**

Set start window icon for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set start window icon for. |
| OH_PixelmapNative *startWindowIcon | The start window icon. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid               or startWindowIcon is nullptr. |

### OH_AbilityRuntime_GetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative **startWindowIcon)
```

**Description**

Get start window icon from start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to get start window icon from. |
| OH_PixelmapNative **startWindowIcon | The obtained start window icon. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid               or startWindowIcon is NOT nullptr. |

### OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)
```

**Description**

Set start window background color for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set start window background color for. |
| const char *startWindowBackgroundColor | The start window background color. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid               or startWindowBackgroundColor is nullptr. |

### OH_AbilityRuntime_SetStartOptionsSupportedWindowModes()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes, size_t size)
```

**Description**

Set start window modes for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set start window modes for. |
| AbilityRuntime_SupportedWindowMode *supportedWindowModes | The start window modes. |
| size_t size | The size of start window modes. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions or supportWindowMode               or size is invalid. |

### OH_AbilityRuntime_SetStartOptionsMinWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)
```

**Description**

Set min window width for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set min window width for. |
| int32_t minWindowWidth | The min window width. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsMaxWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)
```

**Description**

Set max window width for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set max window width for. |
| int32_t maxWindowWidth | The max window width. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsMinWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)
```

**Description**

Set min window height for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set min window height for. |
| int32_t minWindowHeight | The min window height. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_SetStartOptionsMaxWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)
```

**Description**

Set max window height for start options.

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | The options to set max window height for. |
| int32_t maxWindowHeight | The max window height. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.<br>        {@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the startOptions is invalid. |

### OH_AbilityRuntime_GetStartOptionsWindowModeValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)
```

**Description**

Get the window mode from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| AbilityRuntime_WindowMode *windowMode | [out] The obtained window mode. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsDisplayIdValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)
```

**Description**

Get the display ID from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *displayId | [out] The obtained display ID. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsWithAnimationValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)
```

**Description**

Get whether animation is enabled from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| bool *withAnimation | [out] The obtained animation flag. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsWindowLeftValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)
```

**Description**

Get the window left position from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *windowLeft | [out] The obtained window left position. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsWindowTopValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)
```

**Description**

Get the window top position from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *windowTop | [out] The obtained window top position. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)
```

**Description**

Get the window height from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *windowHeight | [out] The obtained window height. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)
```

**Description**

Get the window width from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *windowWidth | [out] The obtained window width. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsStartVisibilityValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)
```

**Description**

Get the start visibility from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| AbilityRuntime_StartVisibility *startVisibility | [out] The obtained start visibility. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)
```

**Description**

Get the start window background color from start options.

> **Note**:
>
> If the background color is not set, {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} is returned, *startWindowBackgroundColor remains NULL, and *size is set to 0.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| char **startWindowBackgroundColor | [out] The pointer used to receive the UTF-8 background color string. It must not be NULL and must point to NULL before the call. |
| size_t *size | [out] The length of the background color string, excluding the trailing NUL. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if error occurred in malloc.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)
```

**Description**

Get the supported start window modes from start options.

> **Note**:
>
> If no supported window modes are set, {@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} is returned, *supportedWindowModes remains NULL, and *size is set to 0.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| AbilityRuntime_SupportedWindowMode **supportedWindowModes | [out] The pointer used to receive the supported start window modes. It must not be NULL and must point to NULL before the call. |
| size_t *size | [out] The number of returned supported start window modes. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if error occurred in malloc.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)
```

**Description**

Get the minimum window width from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *minWindowWidth | [out] The obtained minimum window width. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)
```

**Description**

Get the maximum window width from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *maxWindowWidth | [out] The obtained maximum window width. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)
```

**Description**

Get the minimum window height from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *minWindowHeight | [out] The obtained minimum window height. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |

### OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)
```

**Description**

Get the maximum window height from start options.

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | [in] The start options to read. |
| int32_t *maxWindowHeight | [out] The obtained maximum window height. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>          <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>        <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if any parameter is invalid.</li>          </ul> |


