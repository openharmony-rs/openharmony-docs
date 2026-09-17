# swiper.h

## Overview

Defines a set of Swiper enum and interface.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) | ArkUI_SwiperIndicator | Defines the navigation indicator style for the swiper. |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | ArkUI_SwiperDigitIndicator | Defines the digital indicator style for the swiper. |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | ArkUI_SwiperArrowStyle | Defines the arrow style for the swiper. |

### Enum

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_SwiperArrow](#arkui_swiperarrow) | ArkUI_SwiperArrow | Enumerates arrow styles of the navigation point indicator. |
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) | ArkUI_SwiperNestedScrollMode | Nested scrolling mode for Swiper components and parent components. |
| [ArkUI_PageFlipMode](#arkui_pageflipmode) | ArkUI_PageFlipMode | Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component. |
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode) | ArkUI_SwiperAnimationMode | Enumerates the animation modes for {@link NODE_SWIPER_INDEX}. |
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) | ArkUI_SwiperIndicatorType | Define the navigation indicator type of the swiper. |

### Function

| Name | Description |
| -- | -- |
| [ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)](#oh_arkui_swiperindicator_create) | Creates a navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_dispose) | Destroys the pointer to the indicator. |
| [void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setstartposition) | Sets the distance between the navigation point and the start of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getstartposition) | Obtains the distance between the navigation point and the start of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_settopposition) | Sets the distance between the navigation point and the top of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_gettopposition) | Obtains the distance between the navigation point and the top of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setendposition) | Sets the distance between the navigation point and the right of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getendposition) | Obtains the distance between the navigation point and the end of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setbottomposition) | Sets the distance between the navigation point and the bottom of the swiper. |
| [float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getbottomposition) | Obtains the distance between the navigation point and the bottom of the swiper. |
| [void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemwidth) | Sets the width of the dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemwidth) | Obtains the width of the dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemheight) | Sets the height of the dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemheight) | Obtains the height of the dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemwidth) | Sets the width of the selected dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemwidth) | Obtains the width of the selected dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemheight) | Sets the height of the selected dot for the dot indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemheight) | Obtains the height of the selected dot for the dot indicator. |
| [void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)](#oh_arkui_swiperindicator_setmask) | Sets whether to display the mask style of the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmask) | Obtains whether to display the mask style of the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)](#oh_arkui_swiperindicator_setcolor) | Sets the color of the dot navigation indicator. |
| [uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getcolor) | Obtains the color of the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperindicator_setselectedcolor) | Sets the color of the selected dot for the navigation indicator. |
| [uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselectedcolor) | Obtains the color of the selected dot for the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)](#oh_arkui_swiperindicator_setmaxdisplaycount) | Sets the number of maxDisplayCount for the dot navigation indicator. |
| [int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmaxdisplaycount) | Obtains the number of maxDisplayCount for the dot navigation indicator. |
| [void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperindicator_setignoresizeofbottom) | Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperindicator_setbottomposition). |
| [int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getignoresizeofbottom) | Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperindicator_setbottomposition). |
| [void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)](#oh_arkui_swiperindicator_setspace) | Sets the space between the dots of the navigation indicator. |
| [float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getspace) | Obtains the space between the dots of the navigation indicator. |
| [ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()](#oh_arkui_swiperdigitindicator_create) | Creates a digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setstartposition) | Sets the distance between the digital indicator and the start of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getstartposition) | Gets the distance between the digital indicator and the start of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_settopposition) | Sets the distance between the digital indicator and the top of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_gettopposition) | Gets the distance between the digital indicator and the top of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setendposition) | Sets the distance between the digital indicator and the end of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getendposition) | Gets the distance between the digital indicator and the end of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setbottomposition) | Sets the distance between the digital indicator and the bottom of the swiper. |
| [float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getbottomposition) | Gets the distance between the digital indicator and the bottom of the swiper. |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)](#oh_arkui_swiperdigitindicator_setfontcolor) | Sets the font color of total count in the digital indicator. |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontcolor) | Gets the font color of total count in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperdigitindicator_setselectedfontcolor) | Sets the font color of selected index in the digital indicator. |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontcolor) | Gets the font color of selected index in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setfontsize) | Sets the font size of total count in the digital indicator. |
| [float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontsize) | Gets the font size of total count in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setselectedfontsize) | Sets the font size of selected index in the digital indicator. |
| [float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontsize) | Gets the font size of selected index in the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator *indicator)](#oh_arkui_swiperdigitindicator_destroy) | Destroys the digital indicator. |
| [void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperdigitindicator_setignoresizeofbottom) | Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperdigitindicator_setbottomposition). |
| [int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getignoresizeofbottom) | Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperdigitindicator_setbottomposition). |
| [ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()](#oh_arkui_swiperarrowstyle_create) | Creates a arrow style for swiper. |
| [void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showBackground)](#oh_arkui_swiperarrowstyle_setshowbackground) | Sets whether to show the background for the arrow. |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowbackground) | Gets whether to show the background for the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle) | Sets the display position of the arrow. |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle) | Gets the display position of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)](#oh_arkui_swiperarrowstyle_setbackgroundsize) | Sets the background size of the arrow. |
| [float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle *arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundsize) | Gets the background size of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle *arrowStyle)](#oh_arkui_swiperarrowstyle_destroy) | Destroys the arrow style. |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle *arrowStyle, uint32_t backgroundColor)](#oh_arkui_swiperarrowstyle_setbackgroundcolor) | Sets the background color of the arrow. |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundcolor) | Gets the background color of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)](#oh_arkui_swiperarrowstyle_setarrowsize) | Sets the size of the arrow. |
| [float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowsize) | Gets the size of the arrow. |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)](#oh_arkui_swiperarrowstyle_setarrowcolor) | Sets the color of the arrow. |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowcolor) | Gets the color of the arrow. |

## Enum type description

### ArkUI_SwiperArrow

```c
enum ArkUI_SwiperArrow
```

**Description**

Enumerates arrow styles of the navigation point indicator.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SWIPER_ARROW_HIDE = 0 |  |
| ARKUI_SWIPER_ARROW_SHOW |  |
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER |  |

### ArkUI_SwiperNestedScrollMode

```c
enum ArkUI_SwiperNestedScrollMode
```

**Description**

Nested scrolling mode for Swiper components and parent components.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0 |  |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST |  |

### ArkUI_PageFlipMode

```c
enum ArkUI_PageFlipMode
```

**Description**

Enumerates the page flipping modes using the mouse wheel for the <b>Swiper</b> component.

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0 |  |
| ARKUI_PAGE_FLIP_MODE_SINGLE |  |

### ArkUI_SwiperAnimationMode

```c
enum ArkUI_SwiperAnimationMode
```

**Description**

Enumerates the animation modes for {@link NODE_SWIPER_INDEX}.

**Since**: 15

| Enum item | Description |
| -- | -- |
| ARKUI_SWIPER_NO_ANIMATION = 0 |  |
| ARKUI_SWIPER_DEFAULT_ANIMATION = 1 |  |
| ARKUI_SWIPER_FAST_ANIMATION = 2 |  |

### ArkUI_SwiperIndicatorType

```c
enum ArkUI_SwiperIndicatorType
```

**Description**

Define the navigation indicator type of the swiper.

**Since**: 12

| Enum item | Description |
| -- | -- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT |  |
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT |  |


## Function description

### OH_ArkUI_SwiperIndicator_Create()

```c
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)
```

**Description**

Creates a navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype) type | Indicates the type of the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_SwiperIndicator*](capi-arkui-nativemodule-arkui-swiperindicator.md) | Returns the pointer to the new indicator. |

### OH_ArkUI_SwiperIndicator_Dispose()

```c
void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)
```

**Description**

Destroys the pointer to the indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

### OH_ArkUI_SwiperIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between the navigation point and the start of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the start of the swiper. |

### OH_ArkUI_SwiperIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation point and the start of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the navigation point and the start of the swiper. |

### OH_ArkUI_SwiperIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between the navigation point and the top of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the top of the swiper. |

### OH_ArkUI_SwiperIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation point and the top of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the navigation point and the top of the swiper. |

### OH_ArkUI_SwiperIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between the navigation point and the right of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the right of the swiper. |

### OH_ArkUI_SwiperIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation point and the end of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the navigation point and the end of the swiper. |

### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between the navigation point and the bottom of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the distance between the navigation point and the bottom of the swiper. |

### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation point and the bottom of the swiper.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the navigation point and the bottom of the swiper. |

### OH_ArkUI_SwiperIndicator_SetItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the width of the dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the width of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the width of the dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the width of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the height of the dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the height of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the height of the dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the height of the dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the width of the selected dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the width of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the width of the selected dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the width of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the height of the selected dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float value | Indicates the height of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the height of the selected dot for the dot indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the height of the selected dot for the dot indicator. |

### OH_ArkUI_SwiperIndicator_SetMask()

```c
void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)
```

**Description**

Sets whether to display the mask style of the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t mask | Whether to display the mask style. True means to display. |

### OH_ArkUI_SwiperIndicator_GetMask()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains whether to display the mask style of the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns whether to display the mask style. True means to display. |

### OH_ArkUI_SwiperIndicator_SetColor()

```c
void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)
```

**Description**

Sets the color of the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| uint32_t color | the color of the dot navigation indicator, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_GetColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the color of the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the color of the dot navigation indicator, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)
```

**Description**

Sets the color of the selected dot for the navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| uint32_t selectedColor | the color of the selected dot, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the color of the selected dot for the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the color of the selected dot, in 0xARGB format. |

### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)
```

**Description**

Sets the number of maxDisplayCount for the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t maxDisplayCount | the maxDisplayCount of the navigation dot, span is 6-9. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | {@link ARKUI_ERROR_CODE_NO_ERROR} Success.<br>        {@link ARKUI_ERROR_CODE_PARAM_INVALID} indicator is null or maxDisplayCount less then 6 or          maxDisplayCount more then 9 |

### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the number of maxDisplayCount for the dot navigation indicator.

**Since**: 12

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns the number of the maxDisplayCount, span is 6-9.          0 - indicator is null |

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)
```

**Description**

Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperindicator_setbottomposition).

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| int32_t ignoreSize | Whether to ignore the size of the indicator. The value 1 means to ignore, and 0 means the opposite. The default value is 0. |

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperindicator_setbottomposition).

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns whether to ignore the size of the indicator. |

### OH_ArkUI_SwiperIndicator_SetSpace()

```c
void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)
```

**Description**

Sets the space between the dots of the navigation indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |
| float space | the space between the dots of the navigation indicator, the default value is 8vp. |

### OH_ArkUI_SwiperIndicator_GetSpace()

```c
float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the space between the dots of the navigation indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Indicates the pointer to the indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | the space between the dots of the navigation indicator |

### OH_ArkUI_SwiperDigitIndicator_Create()

```c
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```

**Description**

Creates a digital indicator.

**Since**: 19

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator *](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | Returns the pointer to the new indicator. |

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance between the digital indicator and the start of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the start of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the distance between the digital indicator and the start of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the digital indicator and the start of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance between the digital indicator and the top of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the top of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the distance between the digital indicator and the top of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the digital indicator and the top of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance between the digital indicator and the end of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Indicates the distance between the digital indicator and the end of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the distance between the digital indicator and the end of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the digital indicator and the end of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance between the digital indicator and the bottom of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float value | Returns the distance between the digital indicator and the bottom of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the distance between the digital indicator and the bottom of the swiper.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the distance between the digital indicator and the bottom of the swiper. |

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```

**Description**

Sets the font color of total count in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| uint32_t color | font color, in 0xARGB format. Default value: 0xFF182431. |

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the font color of total count in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | font color, in 0xARGB format. |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```

**Description**

Sets the font color of selected index in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| uint32_t selectedColor | font color, in 0xARGB format. Default value: 0xFF182431. |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the font color of selected index in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | font color, in 0xARGB format. |

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**

Sets the font size of total count in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float size | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the font size of total count in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**

Sets the font size of selected index in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| float size | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Gets the font size of selected index in the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| float | font size, in fp. |

### OH_ArkUI_SwiperDigitIndicator_Destroy()

```c
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator *indicator)
```

**Description**

Destroys the digital indicator.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) *indicator | The pointer to the digital indicator. |

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```

**Description**

Sets whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperdigitindicator_setbottomposition).

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |
| int32_t ignoreSize | Whether to ignore the size of the indicator. The value 1 means to ignore, and 0 means the opposite. The default value is 0. |

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains whether to ignore the size of the indicator for [OH_ArkUI_SwiperDigitIndicator_SetBottomPosition](capi-swiper-h.md#oh_arkui_swiperdigitindicator_setbottomposition).

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | The pointer to the digital indicator. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | Returns whether to ignore the size of the indicator. |

### OH_ArkUI_SwiperArrowStyle_Create()

```c
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```

**Description**

Creates a arrow style for swiper.

**Since**: 19

**Returns**:

| Type | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle *](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | Returns the pointer to the new arrow style. |

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle *arrowStyle, int32_t showBackground)
```

**Description**

Sets whether to show the background for the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |
| int32_t showBackground | whether to show the background for the arrow. The value <b>1</b> means to show the background, and <b>0</b> means the opposite. The default value is <b>0</b>. |

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Gets whether to show the background for the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | whether to show the background for the arrow.          The value <b>1</b> means to show the background, and <b>0</b> means the opposite. |

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)
```

**Description**

Sets the display position of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| int32_t showSidebarMiddle | the display position of the arrow. The value <b>1</b> means to display on boths sides of the swiper, and <b>0</b> means display on boths sides of the swiper indicator. The default value is <b>0</b>. |

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Gets the display position of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | the display position of the arrow. The value <b>1</b> means to display on boths sides of the swiper,          and <b>0</b> means display on boths sides of the swiper indicator. |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```

**Description**

Sets the background size of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| float backgroundSize | the background size of the arrow. The unit is vp. The default value is <b>24</b> when the arrow displays on both sides of the swiper indicator. The default value is <b>32</b> when the arrow displays on both sides of the swiper. |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle *arrowStyle)
```

**Description**

Gets the background size of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| float | Returns the background size of the arrow. The unit is vp. |

### OH_ArkUI_SwiperArrowStyle_Destroy()

```c
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle *arrowStyle)
```

**Description**

Destroys the arrow style.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle *arrowStyle, uint32_t backgroundColor)
```

**Description**

Sets the background color of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) *arrowStyle | The pointer to the arrow style. |
| uint32_t backgroundColor | the background color of the arrow, in 0xARGB format. The default value is <b>0x00000000</b> when the arrow displays on both sides of the swiper indicator. The default value is <b>0x19182431</b> when the arrow displays on both sides of the swiper. |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Gets the background color of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the background color of the arrow, in 0xARGB format. |

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```

**Description**

Sets the size of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| float arrowSize | the size of the arrow. The unit is vp. The default value is <b>18</b> when the arrow displays on both sides of the swiper indicator. The default value is <b>24</b> when the arrow displays on both sides of the swiper. The arrow size is fixed to 3/4 of the background size when the background is shown. |

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Gets the size of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| float | the size of the arrow. The unit is vp. |

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```

**Description**

Sets the color of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |
| uint32_t arrowColor | the color of the arrow, in 0xARGB format. The default value is <b>0x00182431</b>. |

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Gets the color of the arrow.

**Since**: 19

**Parameters**:

| Parameter | Description |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | The pointer to the arrow style. |

**Returns**:

| Type | Description |
| -- | -- |
| uint32_t | Returns the color of the arrow, in 0xARGB format. |


