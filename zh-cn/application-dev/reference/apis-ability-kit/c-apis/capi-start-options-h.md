# start_options.h

## 概述

提供应用启动参数数据结构{@link AbilityRuntime_StartOptions}以及设置和获取相关函数，用于启动Ability时配置窗口参数，支持设置窗口模式、位置、大小、显示效果和样式，支持不同窗口模式、多屏显示、动画效果和自定义窗口图标等场景。

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 17

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)](#oh_abilityruntime_createstartoptions) | 创建{@link AbilityRuntime_StartOptions}对象。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)](#oh_abilityruntime_destroystartoptions) | 销毁{@link AbilityRuntime_StartOptions}对象。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode windowMode)](#oh_abilityruntime_setstartoptionswindowmode) | 设置启动Ability时的窗口模式。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions, int32_t displayId)](#oh_abilityruntime_setstartoptionsdisplayid) | 设置启动Ability时窗口所在的屏幕ID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions, bool withAnimation)](#oh_abilityruntime_setstartoptionswithanimation) | 设置启动Ability时是否具有动画效果。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions, int32_t windowLeft)](#oh_abilityruntime_setstartoptionswindowleft) | 设置启动Ability时的窗口左侧位置，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions, int32_t windowTop)](#oh_abilityruntime_setstartoptionswindowtop) | 设置启动Ability时的窗口顶部位置，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t windowHeight)](#oh_abilityruntime_setstartoptionswindowheight) | 设置启动Ability时的窗口高度，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t windowWidth)](#oh_abilityruntime_setstartoptionswindowwidth) | 设置启动Ability时的窗口宽度，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility startVisibility)](#oh_abilityruntime_setstartoptionsstartvisibility) | 设置启动Ability时窗口和dock栏图标的显示模式。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative *startWindowIcon)](#oh_abilityruntime_setstartoptionsstartwindowicon) | 设置启动Ability时的窗口启动图标。图片数据大小限制为600MB。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative **startWindowIcon)](#oh_abilityruntime_getstartoptionsstartwindowicon) | 获取启动Ability时的窗口启动图标。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)](#oh_abilityruntime_setstartoptionsstartwindowbackgroundcolor) | 设置启动Ability时的窗口背景颜色。如果未设置，则默认采用{@link module.json5配置文件}中{@link abilities标签}的startWindowBackground字段的配置。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes, size_t size)](#oh_abilityruntime_setstartoptionssupportedwindowmodes) | 设置启动Ability时的组件所支持的窗口模式。如果未配置该字段，则默认采用该UIAbility对应的module.json5配置文件中，abilities标签的supportWindowMode字段的取值。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)](#oh_abilityruntime_setstartoptionsminwindowwidth) | 设置启动Ability时的窗口最小宽度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)](#oh_abilityruntime_setstartoptionsmaxwindowwidth) | 设置启动Ability时的窗口最大宽度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)](#oh_abilityruntime_setstartoptionsminwindowheight) | 设置启动Ability时的窗口最小高度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)](#oh_abilityruntime_setstartoptionsmaxwindowheight) | 设置启动Ability时的窗口最大高度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)](#oh_abilityruntime_getstartoptionswindowmodevalue) | 获取启动Ability时的窗口模式。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)](#oh_abilityruntime_getstartoptionsdisplayidvalue) | 获取启动Ability时窗口所在的屏幕ID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)](#oh_abilityruntime_getstartoptionswithanimationvalue) | 获取启动Ability时是否具有动画效果。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)](#oh_abilityruntime_getstartoptionswindowleftvalue) | 获取启动Ability时的窗口左侧位置，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)](#oh_abilityruntime_getstartoptionswindowtopvalue) | 获取启动Ability时的窗口顶部位置，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)](#oh_abilityruntime_getstartoptionswindowheightvalue) | 获取启动Ability时的窗口高度，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)](#oh_abilityruntime_getstartoptionswindowwidthvalue) | 获取启动Ability时的窗口宽度，单位为px。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)](#oh_abilityruntime_getstartoptionsstartvisibilityvalue) | 获取启动Ability时窗口和dock栏图标的显示模式。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)](#oh_abilityruntime_getstartoptionsstartwindowbackgroundcolorvalue) | 获取启动Ability时的窗口背景颜色。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)](#oh_abilityruntime_getstartoptionssupportedwindowmodesvalue) | 获取启动Ability时的组件所支持的窗口模式。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)](#oh_abilityruntime_getstartoptionsminwindowwidthvalue) | 获取启动Ability时的窗口最小宽度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)](#oh_abilityruntime_getstartoptionsmaxwindowwidthvalue) | 获取启动Ability时的窗口最大宽度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)](#oh_abilityruntime_getstartoptionsminwindowheightvalue) | 获取启动Ability时的窗口最小高度，单位为vp。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)](#oh_abilityruntime_getstartoptionsmaxwindowheightvalue) | 获取启动Ability时的窗口最大高度，单位为vp。 |

## 函数说明

### OH_AbilityRuntime_CreateStartOptions()

```c
AbilityRuntime_StartOptions* OH_AbilityRuntime_CreateStartOptions(void)
```

**描述**

创建{@link AbilityRuntime_StartOptions}对象。

**起始版本：** 17

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_StartOptions* | 返回指针类型AbilityRuntime_StartOptions对象。 |

### OH_AbilityRuntime_DestroyStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_DestroyStartOptions(AbilityRuntime_StartOptions **startOptions)
```

**描述**

销毁{@link AbilityRuntime_StartOptions}对象。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions **startOptions | 需要销毁的AbilityRuntime_StartOptions对象。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWindowMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowMode(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode windowMode)
```

**描述**

设置启动Ability时的窗口模式。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [AbilityRuntime_WindowMode](capi-context-constant-h.md#abilityruntime_windowmode) windowMode | 启动Ability时的窗口模式。取值范围参见AbilityRuntime_WindowMode。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空或者WindowMode无效。 |

### OH_AbilityRuntime_SetStartOptionsDisplayId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsDisplayId(AbilityRuntime_StartOptions *startOptions, int32_t displayId)
```

**描述**

设置启动Ability时窗口所在的屏幕ID。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t displayId | 启动Ability时窗口所在的屏幕ID。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWithAnimation()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWithAnimation(AbilityRuntime_StartOptions *startOptions, bool withAnimation)
```

**描述**

设置启动Ability时是否具有动画效果。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| bool withAnimation | 启动Ability时是否具有动画效果。<br>true表示启动Ability时具有动画效果；false表示启动Ability时不具有动画效果。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWindowLeft()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowLeft(AbilityRuntime_StartOptions *startOptions, int32_t windowLeft)
```

**描述**

设置启动Ability时的窗口左侧位置，单位为px。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t windowLeft | 启动Ability时的窗口左侧位置，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWindowTop()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowTop(AbilityRuntime_StartOptions *startOptions, int32_t windowTop)
```

**描述**

设置启动Ability时的窗口顶部位置，单位为px。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t windowTop | 启动Ability时的窗口顶部位置，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t windowHeight)
```

**描述**

设置启动Ability时的窗口高度，单位为px。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t windowHeight | 启动Ability时的窗口高度，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t windowWidth)
```

**描述**

设置启动Ability时的窗口宽度，单位为px。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t windowWidth | 启动Ability时的窗口宽度，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsStartVisibility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartVisibility(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility startVisibility)
```

**描述**

设置启动Ability时窗口和dock栏图标的显示模式。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象，包含启动Ability时的显示模式配置信息。 |
| [AbilityRuntime_StartVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) startVisibility | 需要设置的显示模式。取值范围参见AbilityRuntime_StartVisibility。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示设置成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，      或startVisibility取值不在枚举类AbilityRuntime_StartVisibility中。 |

### OH_AbilityRuntime_SetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative *startWindowIcon)
```

**描述**

设置启动Ability时的窗口启动图标。图片数据大小限制为600MB。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [OH_PixelmapNative](../ImageKit/capi-image-nativemodule-oh-pixelmapnative.md) *startWindowIcon | 启动Ability时的窗口启动图标。图片数据大小限制为600MB。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者startWindowIcon为空指针。 |

### OH_AbilityRuntime_GetStartOptionsStartWindowIcon()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowIcon(AbilityRuntime_StartOptions *startOptions, OH_PixelmapNative **startWindowIcon)
```

**描述**

获取启动Ability时的窗口启动图标。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [OH_PixelmapNative](../ImageKit/capi-image-nativemodule-oh-pixelmapnative.md) **startWindowIcon | 用于获取启动Ability时的窗口启动图标。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者startWindowIcon没有设置为空指针。 |

### OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsStartWindowBackgroundColor(AbilityRuntime_StartOptions *startOptions, const char *startWindowBackgroundColor)
```

**描述**

设置启动Ability时的窗口背景颜色。如果未设置，则默认采用{@link module.json5配置文件}中{@link abilities标签}的startWindowBackground字段的配置。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| const char *startWindowBackgroundColor | 启动Ability时的窗口背景颜色。固定为ARGB格式，如：`#E5FFFFFF`。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者startWindowBackgroundColor为空指针。 |

### OH_AbilityRuntime_SetStartOptionsSupportedWindowModes()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsSupportedWindowModes(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode *supportedWindowModes, size_t size)
```

**描述**

设置启动Ability时的组件所支持的窗口模式。如果未配置该字段，则默认采用该UIAbility对应的module.json5配置文件中，abilities标签的supportWindowMode字段的取值。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [AbilityRuntime_SupportedWindowMode](capi-context-constant-h.md#abilityruntime_supportedwindowmode) *supportedWindowModes | 启动Ability时的组件所支持的窗口模式。取值范围参见AbilityRuntime_SupportedWindowMode。 |
| size_t size | 组件所支持的窗口模式大小。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions或者SupportedWindowModes为空，或者size为0。 |

### OH_AbilityRuntime_SetStartOptionsMinWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t minWindowWidth)
```

**描述**

设置启动Ability时的窗口最小宽度，单位为vp。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t minWindowWidth | 启动Ability时的窗口最小宽度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsMaxWindowWidth()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowWidth(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowWidth)
```

**描述**

设置启动Ability时的窗口最大宽度，单位为vp。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t maxWindowWidth | 启动Ability时的窗口最大宽度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsMinWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMinWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t minWindowHeight)
```

**描述**

设置启动Ability时的窗口最小高度，单位为vp。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t minWindowHeight | 启动Ability时的窗口最小高度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_SetStartOptionsMaxWindowHeight()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_SetStartOptionsMaxWindowHeight(AbilityRuntime_StartOptions *startOptions, int32_t maxWindowHeight)
```

**描述**

设置启动Ability时的窗口最大高度，单位为vp。

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t maxWindowHeight | 启动Ability时的窗口最大高度，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空。 |

### OH_AbilityRuntime_GetStartOptionsWindowModeValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowModeValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_WindowMode *windowMode)
```

**描述**

获取启动Ability时的窗口模式。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [AbilityRuntime_WindowMode](capi-context-constant-h.md#abilityruntime_windowmode) *windowMode | 指向启动Ability时窗口模式的指针。取值范围参见AbilityRuntime_WindowMode。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者windowMode为空指针。 |

### OH_AbilityRuntime_GetStartOptionsDisplayIdValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsDisplayIdValue(AbilityRuntime_StartOptions *startOptions, int32_t *displayId)
```

**描述**

获取启动Ability时窗口所在的屏幕ID。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *displayId | 指向启动Ability时窗口所在屏幕ID的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者displayId为空指针。 |

### OH_AbilityRuntime_GetStartOptionsWithAnimationValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWithAnimationValue(AbilityRuntime_StartOptions *startOptions, bool *withAnimation)
```

**描述**

获取启动Ability时是否具有动画效果。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| bool *withAnimation | 指向启动Ability时是否具有动画效果的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者withAnimation为空指针。 |

### OH_AbilityRuntime_GetStartOptionsWindowLeftValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowLeftValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowLeft)
```

**描述**

获取启动Ability时的窗口左侧位置，单位为px。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *windowLeft | 指向启动Ability时窗口左侧位置的指针，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者windowLeft为空指针。 |

### OH_AbilityRuntime_GetStartOptionsWindowTopValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowTopValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowTop)
```

**描述**

获取启动Ability时的窗口顶部位置，单位为px。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *windowTop | 指向启动Ability时窗口顶部位置的指针，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者windowTop为空指针。 |

### OH_AbilityRuntime_GetStartOptionsWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowHeight)
```

**描述**

获取启动Ability时的窗口高度，单位为px。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *windowHeight | 指向启动Ability时窗口高度的指针，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者windowHeight为空指针。 |

### OH_AbilityRuntime_GetStartOptionsWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *windowWidth)
```

**描述**

获取启动Ability时的窗口宽度，单位为px。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *windowWidth | 指向启动Ability时窗口宽度的指针，单位为px。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者windowWidth为空指针。 |

### OH_AbilityRuntime_GetStartOptionsStartVisibilityValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartVisibilityValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_StartVisibility *startVisibility)
```

**描述**

获取启动Ability时窗口和dock栏图标的显示模式。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [AbilityRuntime_StartVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) *startVisibility | 指向启动Ability时窗口和dock栏图标显示模式的指针。取值范围参见AbilityRuntime_StartVisibility。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者startVisibility为空指针。 |

### OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsStartWindowBackgroundColorValue(AbilityRuntime_StartOptions *startOptions, char **startWindowBackgroundColor, size_t *size)
```

**描述**

获取启动Ability时的窗口背景颜色。

>**说明：** 
>If the background color is not set, [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned,
 *     *startWindowBackgroundColor remains NULL, and *size is set to 0.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| char **startWindowBackgroundColor | 指向获取到的窗口背景颜色UTF-8字符串指针的二级指针，不能为空，且调用前必须指向空指针。固定为ARGB格式，如：`#E5FFFFFF`。使用完毕后，需要调用free释放。 |
| size_t *size | 指向获取到的窗口背景颜色字符串长度的指针，不能为空，不包含字符串结尾的空字符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示任意参数无效。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_INTERNAL时，表示开发者无法恢复的内部错误，比如内部调用malloc错误。 |

### OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsSupportedWindowModesValue(AbilityRuntime_StartOptions *startOptions, AbilityRuntime_SupportedWindowMode **supportedWindowModes, size_t *size)
```

**描述**

获取启动Ability时的组件所支持的窗口模式。

>**说明：** 
>If no supported window modes are set, [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned,
 *     *supportedWindowModes remains NULL, and *size is set to 0.

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| [AbilityRuntime_SupportedWindowMode](capi-context-constant-h.md#abilityruntime_supportedwindowmode) **supportedWindowModes | 指向获取到的组件所支持窗口模式数组指针的二级指针，不能为空，且调用前必须指向空指针。取值范围参见AbilityRuntime_SupportedWindowMode。使用完毕后，需要调用free释放。 |
| size_t *size | 指向获取到的组件所支持窗口模式数量的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示任意参数无效。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_INTERNAL时，表示开发者无法恢复的内部错误，比如内部调用malloc错误。 |

### OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowWidth)
```

**描述**

获取启动Ability时的窗口最小宽度，单位为vp。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *minWindowWidth | 指向启动Ability时窗口最小宽度的指针，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者minWindowWidth为空指针。 |

### OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowWidthValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowWidth)
```

**描述**

获取启动Ability时的窗口最大宽度，单位为vp。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *maxWindowWidth | 指向启动Ability时窗口最大宽度的指针，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者maxWindowWidth为空指针。 |

### OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMinWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *minWindowHeight)
```

**描述**

获取启动Ability时的窗口最小高度，单位为vp。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *minWindowHeight | 指向启动Ability时窗口最小高度的指针，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者minWindowHeight为空指针。 |

### OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetStartOptionsMaxWindowHeightValue(AbilityRuntime_StartOptions *startOptions, int32_t *maxWindowHeight)
```

**描述**

获取启动Ability时的窗口最大高度，单位为vp。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| AbilityRuntime_StartOptions *startOptions | AbilityRuntime_StartOptions对象。 |
| int32_t *maxWindowHeight | 指向启动Ability时窗口最大高度的指针，单位为vp。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | 在返回ABILITY_RUNTIME_ERROR_CODE_NO_ERROR时，表示接口调用成功。      <br>在返回ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID时，表示StartOptions为空，或者maxWindowHeight为空指针。 |


