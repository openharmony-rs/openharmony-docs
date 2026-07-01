# swiper.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

## Overview

Defines the enumerations and APIs of the **Swiper** component.

**File to include:** <arkui/swiper.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Sample:** <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End-->

## Summary

### Structs

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) | ArkUI_SwiperIndicator | Defines the navigation indicator style of the **Swiper** component.|
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | ArkUI_SwiperDigitIndicator | Defines the style of the digit navigation indicator for the **Swiper** component.|
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | ArkUI_SwiperArrowStyle | Defines the navigation arrow style for the **Swiper** component.|

### Enums

| Name| typedef Keyword| Description|
| -- | -- | -- |
| [ArkUI_SwiperArrow](#arkui_swiperarrow) | ArkUI_SwiperArrow | Enumerates arrow styles of the navigation indicator of the **Swiper** component.|
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) | ArkUI_SwiperNestedScrollMode | Enumerates the nested scrolling modes of the **Swiper** component and its parent container.|
| [ArkUI_PageFlipMode](#arkui_pageflipmode) | ArkUI_PageFlipMode | Enumerates the page flipping modes using the mouse wheel for the **Swiper** component.|
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode) | ArkUI_SwiperAnimationMode | Enumerates the animation modes for the **Swiper** component when jumping to the page with the specified index.|
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) | ArkUI_SwiperIndicatorType | Enumerates the navigation indicator types of the **Swiper** component.|

### Functions

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)](#oh_arkui_swiperindicator_create) | Creates a navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_dispose) | Disposes of the pointer to the navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setstartposition) | Sets the distance between a navigation indicator and the left edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getstartposition) | Obtains the distance between the navigation indicator and the left edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_settopposition) | Sets the distance between a navigation indicator and the top edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_gettopposition) | Obtains the distance between the navigation indicator and the top edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setendposition) | Sets the distance between a navigation indicator and the right edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getendposition) | Obtains the distance between the navigation indicator and the right edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setbottomposition) | Sets the distance between a navigation indicator and the bottom edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getbottomposition) | Obtains the distance between the navigation indicator and the bottom edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperindicator_setignoresizeofbottom) | Sets whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getignoresizeofbottom) | Obtains whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemwidth) | Sets the width of a dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemwidth) | Obtains the width of the dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemheight) | Sets the height of a dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemheight) | Obtains the height of the dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemwidth) | Sets the width of a selected dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemwidth) | Obtains the width of the selected dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemheight) | Sets the height of a selected dot-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemheight) | Obtains the height of the selected dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)](#oh_arkui_swiperindicator_setmask) | Sets whether to enable the mask for a dot-style navigation indicator for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmask) | Obtains whether the mask is enabled for the dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)](#oh_arkui_swiperindicator_setcolor) | Sets the color of a dot-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getcolor) | Obtains the color of the dot-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperindicator_setselectedcolor) | Sets the color of a selected dot-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselectedcolor) | Obtains the color of the selected dot-style navigation indicator of the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)](#oh_arkui_swiperindicator_setmaxdisplaycount) | Sets the maximum number of dots for a dot-style navigation indicator.|
| [int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmaxdisplaycount) | Obtains the maximum number of dots for the dot-style navigation indicator.|
| [ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()](#oh_arkui_swiperdigitindicator_create) | Creates a digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_destroy) | Destroy the pointer to the digit-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setstartposition) | Sets the start position of a digit-style navigation indicator for the **Swiper** component. This determines the distance from the left edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the right edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getstartposition) | Obtains the start position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_settopposition) | Sets the distance from a digit-style navigation indicator to the top edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_gettopposition) | Obtains the distance from the digit-style navigation indicator to the top edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setendposition) | Sets the end position of a digit-style navigation indicator for the **Swiper** component. This determines the distance from the right edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the left edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getendposition) | Obtains the end position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setbottomposition) | Sets the distance from a digit-style navigation indicator to the bottom edge of the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getbottomposition) | Obtains the distance from the digit-style navigation indicator to the bottom edge of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)](#oh_arkui_swiperdigitindicator_setfontcolor) | Sets the font color of a digit-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontcolor) | Obtains the font color of the digit-style navigation indicator for the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperdigitindicator_setselectedfontcolor) | Sets the font color of a selected digit-style navigation indicator for the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontcolor) | Obtains the font color of the selected digit-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setfontsize) | Sets the font size of a digit-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontsize) | Obtains the font size of the digit-style navigation indicator of the **Swiper** component.|
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setselectedfontsize) | Sets the font size of a selected digit-style navigation indicator for the **Swiper** component.|
| [float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontsize) | Obtains the font size of the selected digit-style navigation indicator of the **Swiper** component.|
| [ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()](#oh_arkui_swiperarrowstyle_create) | Creates a navigation arrow for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_destroy) | Destroys the navigation arrow pointer of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)](#oh_arkui_swiperarrowstyle_setshowbackground) | Sets whether to display the background of a navigation arrow for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowbackground) | Obtains whether the background of the navigation arrow is displayed for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle) | Sets the position of a navigation arrow for the **Swiper** component.|
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle) | Obtains the position of the navigation arrow for the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)](#oh_arkui_swiperarrowstyle_setbackgroundsize) | Sets the background size for a navigation arrow of the **Swiper** component.|
| [float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundsize) | Obtains the background size of the navigation arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)](#oh_arkui_swiperarrowstyle_setbackgroundcolor) | Sets the background color for a navigation arrow of the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundcolor) | Obtains the background color of the navigation arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)](#oh_arkui_swiperarrowstyle_setarrowsize) | Sets the size for a navigation arrow of the **Swiper** component.|
| [float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowsize) | Obtains the size of the navigation arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)](#oh_arkui_swiperarrowstyle_setarrowcolor) | Sets the color for a navigation arrow of the **Swiper** component.|
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowcolor) | Obtains the color of the navigation arrow of the **Swiper** component.|
| [void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)](#oh_arkui_swiperindicator_setspace) | Sets the spacing between navigation indicators.|
| [float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getspace) | Obtains the spacing between navigation indicators.|
| [void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperdigitindicator_setignoresizeofbottom) | Sets whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|
| [int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getignoresizeofbottom) | Obtains whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.|

## Enumeration Description

### ArkUI_SwiperArrow

```c
enum ArkUI_SwiperArrow
```

**Description**

Enumerates arrow styles of the navigation indicator of the **Swiper** component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_ARROW_HIDE = 0 | The arrow is not displayed for the navigation indicator.|
| ARKUI_SWIPER_ARROW_SHOW | The arrow is displayed for the navigation indicator.|
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER | The arrow is displayed only when the mouse pointer hovers over the navigation indicator.|

### ArkUI_SwiperNestedScrollMode

```c
enum ArkUI_SwiperNestedScrollMode
```

**Description**

Enumerates the nested scrolling modes of the **Swiper** component and its parent container.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0 | The scrolling is contained within the **Swiper** component, and no scroll chaining occurs, that is, the parent container does not scroll when the component scrolling reaches the boundary.|
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST | The **Swiper** component scrolls first, and when it hits the boundary, the parent container scrolls. When the parent container hits the boundary, its edge effect is displayed. If no edge effect is specified for the parent container, the edge effect of the **Swiper** component is displayed instead.|

### ArkUI_PageFlipMode

```c
enum ArkUI_PageFlipMode
```

**Description**

Enumerates the page flipping modes using the mouse wheel for the **Swiper** component.

**Since:** 15

| Value| Description|
| -- | -- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0 | When the mouse wheel is scrolled continuously, multiple pages are flipped, which is determined by the number of times that mouse events are reported.|
| ARKUI_PAGE_FLIP_MODE_SINGLE | The system does not respond to other mouse wheel events until the page flipping animation ends.|

### ArkUI_SwiperAnimationMode

```c
enum ArkUI_SwiperAnimationMode
```

**Description**

Enumerates the animation modes for the **Swiper** component when jumping to the page with the specified index.

**Since:** 15

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_NO_ANIMATION = 0 | Jumps to the target page without any animation.|
| ARKUI_SWIPER_DEFAULT_ANIMATION = 1 | Animates smoothly to the target page.|
| ARKUI_SWIPER_FAST_ANIMATION = 2 | First jumps to a position near the target page without animation, then animates to the target page.|

### ArkUI_SwiperIndicatorType

```c
enum ArkUI_SwiperIndicatorType
```

**Description**

Enumerates the navigation indicator types of the **Swiper** component.

**Since:** 12

| Value| Description|
| -- | -- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT | Dot type.|
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT | Digit type.|


## Function Description

### OH_ArkUI_SwiperIndicator_Create()

```c
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)
```

**Description**

Creates a navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype) type | Type of the navigation indicator.|

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_SwiperIndicator*](capi-arkui-nativemodule-arkui-swiperindicator.md) | Pointer to the navigation indicator object.|

### OH_ArkUI_SwiperIndicator_Dispose()

```c
void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)
```

**Description**

Disposes of the pointer to the navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

### OH_ArkUI_SwiperIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between a navigation indicator and the left edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Distance between the navigation indicator and the left edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation indicator and the left edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the left edge of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between a navigation indicator and the top edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Distance between the navigation indicator and the top edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation indicator and the top edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the top edge of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between a navigation indicator and the right edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Distance between the navigation indicator and the right edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation indicator and the right edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the right edge of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the distance between a navigation indicator and the bottom edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Distance between the navigation indicator and the bottom edge of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the distance between the navigation indicator and the bottom edge of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance between the navigation indicator and the bottom edge of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)
```

**Description**

Sets whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| int32_t ignoreSize | Whether to ignore the indicator size when positioning the indicator. The value **1** means to ignore the indicator size when positioning the indicator, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains whether the **OH_ArkUI_SwiperIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the indicator size is ignored when positioning the indicator.|

### OH_ArkUI_SwiperIndicator_SetItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the width of a dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Width of the dot-style navigation indicator. Default value: **12**, in vp.|

### OH_ArkUI_SwiperIndicator_GetItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the width of the dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Width of the dot-style navigation indicator. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the height of a dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Height of the dot-style navigation indicator. Default value: **6**, in vp.|

### OH_ArkUI_SwiperIndicator_GetItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the height of the dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Height of the dot-style navigation indicator. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the width of a selected dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Width of the dot-style navigation indicator. Default value: **12**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the width of the selected dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Width of the dot-style navigation indicator. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**Description**

Sets the height of a selected dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float value | Height of the dot-style navigation indicator. Default value: **6**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the height of the selected dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Height of the dot-style navigation indicator. The unit is vp.|

### OH_ArkUI_SwiperIndicator_SetMask()

```c
void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)
```

**Description**

Sets whether to enable the mask for a dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| int32_t mask | Whether to enable the mask. The value **1** means to enable, and **0** means the opposite.|

### OH_ArkUI_SwiperIndicator_GetMask()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains whether the mask is enabled for the dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Returns **1** if the mask is enabled; returns **0** otherwise.|

### OH_ArkUI_SwiperIndicator_SetColor()

```c
void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)
```

**Description**

Sets the color of a dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| uint32_t color | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperIndicator_GetColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the color of the dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)
```

**Description**

Sets the color of a selected dot-style navigation indicator for the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| uint32_t selectedColor | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the color of the selected dot-style navigation indicator of the **Swiper** component.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)
```

**Description**

Sets the maximum number of dots for a dot-style navigation indicator.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| int32_t maxDisplayCount | Maximum number of dots. Value range: [6, 9].|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Error code.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if the operation is successful.<br>         Returns [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) if **maxDisplayCount** is set to an invalid value.|

### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the maximum number of dots for the dot-style navigation indicator.

**Since:** 12

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Maximum number of dots. Value range: [6, 9].|

### OH_ArkUI_SwiperDigitIndicator_Create()

```c
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```

**Description**

Creates a digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator *](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | Pointer to the digit-style navigation indicator object.|

### OH_ArkUI_SwiperDigitIndicator_Destroy()

```c
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Destroy the pointer to the digit-style navigation indicator of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the start position of a digit-style navigation indicator for the **Swiper** component. This determines the distance from the left edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the right edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float value | Distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the start position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the left edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the right edge. The unit is vp.|

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance from a digit-style navigation indicator to the top edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float value | Distance from the digit-style navigation indicator to the top of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the distance from the digit-style navigation indicator to the top edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the digit-style navigation indicator to the top of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the end position of a digit-style navigation indicator for the **Swiper** component. This determines the distance from the right edge of the **Swiper** component. For right-to-left scripts, this determines the distance from the left edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float value | Distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the end position of the digit-style navigation indicator for the **Swiper** component. This indicates the distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the right edge of the **Swiper** component. For right-to-left scripts, this indicates the distance from the left edge. The unit is vp.|

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**Description**

Sets the distance from a digit-style navigation indicator to the bottom edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float value | Distance from the digit-style navigation indicator to the bottom of the **Swiper** component. Default value: **0**, in vp.|

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the distance from the digit-style navigation indicator to the bottom edge of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Distance from the digit-style navigation indicator to the bottom of the **Swiper** component. The unit is vp.|

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```

**Description**

Sets the font color of a digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| uint32_t color | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red. Default value: **0xFF182431**.|

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the font color of the digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```

**Description**

Sets the font color of a selected digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| uint32_t selectedColor | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red. Default value: **0xFF182431**.|

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the font color of the selected digit-style navigation indicator of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**

Sets the font size of a digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float size | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the font size of the digit-style navigation indicator of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**Description**

Sets the font size of a selected digit-style navigation indicator for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|
| float size | Font size, in fp.|

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains the font size of the selected digit-style navigation indicator of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the digit-style navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Font size, in fp.|

### OH_ArkUI_SwiperArrowStyle_Create()

```c
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```

**Description**

Creates a navigation arrow for the **Swiper** component.

**Since:** 19

**Returns**

| Type| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle *](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | Pointer to the navigation arrow object.|

### OH_ArkUI_SwiperArrowStyle_Destroy()

```c
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Destroys the navigation arrow pointer of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)
```

**Description**

Sets whether to display the background of a navigation arrow for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| int32_t showBackground | Whether to show the background of the navigation arrow. The value **1** means to show the background, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains whether the background of the navigation arrow is displayed for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the background of the navigation arrow is displayed. The value **1** means that the background is displayed, and **0** means the opposite.|

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)
```

**Description**

Sets the position of a navigation arrow for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| int32_t showSidebarMiddle | Position where the navigation arrow is displayed. The value **0** indicates that the navigation arrow is displayed on both sides of the navigation indicator, and **1** indicates that the navigation arrow is displayed on both sides of the **Swiper** component. The default value is **0**.|

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains the position of the navigation arrow for the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Position where the navigation arrow is displayed. The value **0** indicates that the navigation arrow is displayed on both sides of the navigation indicator, and **1** indicates that the navigation arrow is displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```

**Description**

Sets the background size for a navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| float backgroundSize | Background size of the navigation arrow, in vp. Default value: 24 vp when displayed on both sides of the navigation indicator and 32 vp when displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains the background size of the navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Background size of the navigation arrow, in vp.|

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)
```

**Description**

Sets the background color for a navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| uint32_t backgroundColor | Background color of the navigation arrow, in 0xARGB format. For example, **0xFFFF0000** indicates red. Default value: **0x00000000** when displayed on both sides of the navigation indicator and **0x19182431** when displayed on both sides of the **Swiper** component.|

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains the background color of the navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Background color of the navigation arrow, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```

**Description**

Sets the size for a navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| float arrowSize | Size of the navigation arrow, in vp. Default value: 18 vp when displayed on both sides of the navigation indicator and 24 vp when displayed on both sides of the **Swiper** component. When the navigation arrow background is displayed, the value of **arrowSize** is fixed at 3/4 of the value of **backgroundSize**.|

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains the size of the navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Size of the navigation arrow, in vp.|

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```

**Description**

Sets the color for a navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|
| uint32_t arrowColor | Color of the navigation arrow, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**Description**

Obtains the color of the navigation arrow of the **Swiper** component.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | Pointer to the navigation arrow object.|

**Returns**

| Type| Description|
| -- | -- |
| uint32_t | Color of the navigation arrow, in 0xARGB format. For example, **0xFFFF0000** indicates red.|

### OH_ArkUI_SwiperIndicator_SetSpace()

```c
void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)
```

**Description**

Sets the spacing between navigation indicators.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|
| float space | Spacing between navigation indicators. Default value: **8**, in vp.|

### OH_ArkUI_SwiperIndicator_GetSpace()

```c
float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)
```

**Description**

Obtains the spacing between navigation indicators.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| float | Spacing between navigation indicators. The unit is vp.|

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```

**Description**

Sets whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the navigation indicator object.|
| int32_t ignoreSize | Whether to ignore the indicator size when positioning the indicator. The value **1** means to ignore the indicator size when positioning the indicator, and **0** means the opposite. The default value is **0**.|

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```

**Description**

Obtains whether the **OH_ArkUI_SwiperDigitIndicator_SetBottomPosition** API ignores the indicator size when positioning the indicator.

**Since:** 19

**Parameters**

| Name| Description|
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | Pointer to the navigation indicator object.|

**Returns**

| Type| Description|
| -- | -- |
| int32_t | Whether the indicator size is ignored when positioning the indicator.|
