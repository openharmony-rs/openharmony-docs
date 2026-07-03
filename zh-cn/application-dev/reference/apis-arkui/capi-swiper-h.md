# swiper.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @Hu_ZeQi-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

定义Swiper组件的枚举和接口。

**引用文件：** <arkui/node_attributes/swiper.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[NDKSwiperSample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NDKSwiperSample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md) | ArkUI_SwiperIndicator | 定义Swiper组件的导航指示器样式，用于在轮播等场景中展示当前位置和切换状态。 |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | ArkUI_SwiperDigitIndicator | 定义Swiper组件的数字导航指示器样式，用于以数字形式展示当前位置和总页数。 |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | ArkUI_SwiperArrowStyle | 定义Swiper组件的导航箭头样式，用于在轮播等场景中提供更直观的翻页指引。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_SwiperArrow](#arkui_swiperarrow) | ArkUI_SwiperArrow | Swiper导航点箭头枚举值。 |
| [ArkUI_SwiperNestedScrollMode](#arkui_swipernestedscrollmode) | ArkUI_SwiperNestedScrollMode | Swiper组件和父组件的嵌套滚动模式。 |
| [ArkUI_PageFlipMode](#arkui_pageflipmode) | ArkUI_PageFlipMode | Swiper组件鼠标滚轮翻页模式。 |
| [ArkUI_SwiperAnimationMode](#arkui_swiperanimationmode) | ArkUI_SwiperAnimationMode | Swiper组件跳转到目标index的动画模式。 |
| [ArkUI_SwiperIndicatorType](#arkui_swiperindicatortype) | ArkUI_SwiperIndicatorType | 定义Swiper组件的导航指示器类型。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)](#oh_arkui_swiperindicator_create) | 创建Swiper组件的导航指示器。 |
| [void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_dispose) | 销毁Swiper组件的导航指示器指针。 |
| [void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setstartposition) | 设置导航点距离Swiper组件左边的距离。 |
| [float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getstartposition) | 获取导航点距离Swiper组件左边的距离。 |
| [void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_settopposition) | 设置导航点距离Swiper组件顶部的距离。 |
| [float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_gettopposition) | 获取导航点距离Swiper组件顶部的距离。 |
| [void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setendposition) | 设置导航点距离Swiper组件右边的距离。 |
| [float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getendposition) | 获取导航点距离Swiper组件右边的距离。 |
| [void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setbottomposition) | 设置导航点距离Swiper组件底部的距离。 |
| [float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getbottomposition) | 获取导航点距离Swiper组件底部的距离。 |
| [void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperindicator_setignoresizeofbottom) | 设置OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。 |
| [int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getignoresizeofbottom) | 获取OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。 |
| [void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemwidth) | 设置Swiper组件圆点导航指示器的宽。 |
| [float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemwidth) | 获取Swiper组件圆点导航指示器的宽。 |
| [void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setitemheight) | 设置Swiper组件圆点导航指示器的高。 |
| [float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getitemheight) | 获取Swiper组件圆点导航指示器的高。 |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemwidth) | 设置被选中的Swiper组件圆点导航指示器的宽。 |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemwidth) | 获取被选中Swiper组件圆点导航指示器的宽。 |
| [void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)](#oh_arkui_swiperindicator_setselecteditemheight) | 设置被选中的Swiper组件圆点导航指示器的高。 |
| [float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselecteditemheight) | 获取被选中Swiper组件圆点导航指示器的高。 |
| [void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)](#oh_arkui_swiperindicator_setmask) | 设置是否显示Swiper组件圆点导航指示器的蒙版样式。 |
| [int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmask) | 获取是否显示Swiper组件圆点导航指示器的蒙版样式。 |
| [void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)](#oh_arkui_swiperindicator_setcolor) | 设置Swiper组件圆点导航指示器的颜色。 |
| [uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getcolor) | 获取Swiper组件圆点导航指示器的颜色。 |
| [void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperindicator_setselectedcolor) | 设置被选中Swiper组件圆点导航指示器的颜色。 |
| [uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getselectedcolor) | 获取被选中Swiper组件圆点导航指示器的颜色。 |
| [int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)](#oh_arkui_swiperindicator_setmaxdisplaycount) | 设置圆点导航点指示器样式下，导航点显示个数的最大值。 |
| [int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getmaxdisplaycount) | 获取圆点导航点指示器样式下，导航点显示个数的最大值。 |
| [ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()](#oh_arkui_swiperdigitindicator_create) | 创建Swiper组件的数字导航指示器。 |
| [void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_destroy) | 销毁Swiper组件的数字导航指示器指针。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setstartposition) | 设置数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，设置其距离Swiper组件右边的距离。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getstartposition) | 获取数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，获取其距离Swiper组件右边的距离。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_settopposition) | 设置数字导航指示器距离Swiper组件顶部的距离。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_gettopposition) | 获取数字导航指示器距离Swiper组件顶部的距离。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setendposition) | 设置数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，设置其距离Swiper组件左边的距离。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getendposition) | 获取数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，获取其距离Swiper组件左边的距离。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)](#oh_arkui_swiperdigitindicator_setbottomposition) | 设置数字导航指示器距离Swiper组件底部的距离。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getbottomposition) | 获取数字导航指示器距离Swiper组件底部的距离。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)](#oh_arkui_swiperdigitindicator_setfontcolor) | 设置Swiper组件数字导航指示器字体颜色。 |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontcolor) | 获取Swiper组件数字导航指示器字体颜色。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)](#oh_arkui_swiperdigitindicator_setselectedfontcolor) | 设置被选中Swiper组件数字导航指示器字体颜色。 |
| [uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontcolor) | 获取被选中Swiper组件数字导航指示器字体颜色。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setfontsize) | 设置Swiper组件数字导航指示器字体大小。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getfontsize) | 获取Swiper组件数字导航指示器字体大小。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)](#oh_arkui_swiperdigitindicator_setselectedfontsize) | 设置被选中Swiper组件数字导航指示器字体大小。 |
| [float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getselectedfontsize) | 获取被选中Swiper组件数字导航指示器字体大小。 |
| [ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()](#oh_arkui_swiperarrowstyle_create) | 创建Swiper组件的导航箭头。 |
| [void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_destroy) | 销毁Swiper组件的导航箭头指针。 |
| [void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)](#oh_arkui_swiperarrowstyle_setshowbackground) | 设置Swiper组件导航箭头底板是否显示。 |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowbackground) | 获取Swiper组件导航箭头底板是否显示。 |
| [void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)](#oh_arkui_swiperarrowstyle_setshowsidebarmiddle) | 设置Swiper组件导航箭头显示位置。 |
| [int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getshowsidebarmiddle) | 获取Swiper组件导航箭头显示位置。 |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)](#oh_arkui_swiperarrowstyle_setbackgroundsize) | 设置Swiper组件导航箭头底板大小。 |
| [float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundsize) | 获取Swiper组件导航箭头底板大小。 |
| [void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)](#oh_arkui_swiperarrowstyle_setbackgroundcolor) | 设置Swiper组件导航箭头底板颜色。 |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getbackgroundcolor) | 获取Swiper组件导航箭头底板颜色。 |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)](#oh_arkui_swiperarrowstyle_setarrowsize) | 设置Swiper组件导航箭头大小。 |
| [float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowsize) | 获取Swiper组件导航箭头大小。 |
| [void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)](#oh_arkui_swiperarrowstyle_setarrowcolor) | 设置Swiper组件导航箭头颜色。 |
| [uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)](#oh_arkui_swiperarrowstyle_getarrowcolor) | 获取Swiper组件导航箭头颜色。 |
| [void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)](#oh_arkui_swiperindicator_setspace) | 设置导航点间距。 |
| [float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)](#oh_arkui_swiperindicator_getspace) | 获取导航点间距。 |
| [void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)](#oh_arkui_swiperdigitindicator_setignoresizeofbottom) | 设置OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。 |
| [int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)](#oh_arkui_swiperdigitindicator_getignoresizeofbottom) | 获取OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。 |

## 枚举类型说明

### ArkUI_SwiperArrow

```c
enum ArkUI_SwiperArrow
```

**描述**

Swiper导航点箭头枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_ARROW_HIDE = 0 | 不显示swiper中导航点箭头。 |
| ARKUI_SWIPER_ARROW_SHOW | 显示swiper中导航点箭头。 |
| ARKUI_SWIPER_ARROW_SHOW_ON_HOVER | 在hover状态下显示swiper中导航点箭头。 |

### ArkUI_SwiperNestedScrollMode

```c
enum ArkUI_SwiperNestedScrollMode
```

**描述**

Swiper组件和父组件的嵌套滚动模式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY = 0 | Swiper只自身滚动，不与父组件联动。 |
| ARKUI_SWIPER_NESTED_SRCOLL_SELF_FIRST | Swiper自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则Swiper触发边缘效果。 |

### ArkUI_PageFlipMode

```c
enum ArkUI_PageFlipMode
```

**描述**

Swiper组件鼠标滚轮翻页模式。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_PAGE_FLIP_MODE_CONTINUOUS = 0 | 鼠标滚轮连续滚动时翻多页，根据鼠标事件上报次数确定。 |
| ARKUI_PAGE_FLIP_MODE_SINGLE | 一次翻页动画结束前不响应其他鼠标滚轮事件。 |

### ArkUI_SwiperAnimationMode

```c
enum ArkUI_SwiperAnimationMode
```

**描述**

Swiper组件跳转到目标index的动画模式。

**起始版本：** 15

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_NO_ANIMATION = 0 | 无动画跳转到目标index。 |
| ARKUI_SWIPER_DEFAULT_ANIMATION = 1 | 做动画跳转到目标index。 |
| ARKUI_SWIPER_FAST_ANIMATION = 2 | 先无动画跳转到目标附近再做动画跳转到目标index。 |

### ArkUI_SwiperIndicatorType

```c
enum ArkUI_SwiperIndicatorType
```

**描述**

定义Swiper组件的导航指示器类型。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SWIPER_INDICATOR_TYPE_DOT | 圆点指示器类型。 |
| ARKUI_SWIPER_INDICATOR_TYPE_DIGIT | 数字指示器类型。 |


## 函数说明

### OH_ArkUI_SwiperIndicator_Create()

```c
ArkUI_SwiperIndicator* OH_ArkUI_SwiperIndicator_Create(ArkUI_SwiperIndicatorType type)
```

**描述**

创建Swiper组件的导航指示器。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype) type | 导航指示器的类型。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperIndicator*](capi-arkui-nativemodule-arkui-swiperindicator.md) | 导航指示器对象指针。 |

### OH_ArkUI_SwiperIndicator_Dispose()

```c
void OH_ArkUI_SwiperIndicator_Dispose(ArkUI_SwiperIndicator* indicator)
```

**描述**

销毁Swiper组件的导航指示器指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

### OH_ArkUI_SwiperIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperIndicator_SetStartPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置导航点距离Swiper组件左边的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 导航点距离Swiper组件左边的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperIndicator_GetStartPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取导航点距离Swiper组件左边的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航点距离Swiper组件左边的距离。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperIndicator_SetTopPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置导航点距离Swiper组件顶部的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 导航点距离Swiper组件顶部的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperIndicator_GetTopPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取导航点距离Swiper组件顶部的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航点距离Swiper组件顶部的距离。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperIndicator_SetEndPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置导航点距离Swiper组件右边的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 导航点距离Swiper组件右边的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperIndicator_GetEndPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取导航点距离Swiper组件右边的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航点距离Swiper组件右边的距离。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperIndicator_SetBottomPosition(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置导航点距离Swiper组件底部的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 导航点距离Swiper组件底部的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperIndicator_GetBottomPosition(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取导航点距离Swiper组件底部的距离。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航点距离Swiper组件底部的距离。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator, int32_t ignoreSize)
```

**描述**

设置OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| int32_t ignoreSize | 是否忽略导航点大小。1表示忽略导航点大小，0表示不忽略，默认值0。 |

### OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取OH_ArkUI_SwiperIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 是否忽略导航点大小。 |

### OH_ArkUI_SwiperIndicator_SetItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置Swiper组件圆点导航指示器的宽。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 圆点导航指示器的宽。默认值：12，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetItemWidth(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取Swiper组件圆点导航指示器的宽。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 圆点导航指示器的宽。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置Swiper组件圆点导航指示器的高。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 圆点导航指示器的高。默认值：6，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetItemHeight(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取Swiper组件圆点导航指示器的高。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 圆点导航指示器的高。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetSelectedItemWidth()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemWidth(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置被选中的Swiper组件圆点导航指示器的宽。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 圆点导航指示器的宽。默认值：12，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetSelectedItemWidth()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemWidth(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取被选中Swiper组件圆点导航指示器的宽。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 圆点导航指示器的宽。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetSelectedItemHeight()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedItemHeight(ArkUI_SwiperIndicator* indicator, float value)
```

**描述**

设置被选中的Swiper组件圆点导航指示器的高。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float value | 圆点导航指示器的高。默认值：6，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetSelectedItemHeight()

```c
float OH_ArkUI_SwiperIndicator_GetSelectedItemHeight(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取被选中Swiper组件圆点导航指示器的高。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 圆点导航指示器的高。单位：vp。 |

### OH_ArkUI_SwiperIndicator_SetMask()

```c
void OH_ArkUI_SwiperIndicator_SetMask(ArkUI_SwiperIndicator* indicator, int32_t mask)
```

**描述**

设置是否显示Swiper组件圆点导航指示器的蒙版样式。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| int32_t mask | 是否显示蒙版样式，1表示显示，0表示不显示。 |

### OH_ArkUI_SwiperIndicator_GetMask()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMask(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取是否显示Swiper组件圆点导航指示器的蒙版样式。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | mask 1表示显示圆点导航指示器的蒙版样式，0表示不显示。 |

### OH_ArkUI_SwiperIndicator_SetColor()

```c
void OH_ArkUI_SwiperIndicator_SetColor(ArkUI_SwiperIndicator* indicator, uint32_t color)
```

**描述**

设置Swiper组件圆点导航指示器的颜色。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| uint32_t color | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperIndicator_GetColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetColor(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取Swiper组件圆点导航指示器的颜色。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperIndicator_SetSelectedColor()

```c
void OH_ArkUI_SwiperIndicator_SetSelectedColor(ArkUI_SwiperIndicator* indicator, uint32_t selectedColor)
```

**描述**

设置被选中Swiper组件圆点导航指示器的颜色。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| uint32_t selectedColor | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperIndicator_GetSelectedColor()

```c
uint32_t OH_ArkUI_SwiperIndicator_GetSelectedColor(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取被选中Swiper组件圆点导航指示器的颜色。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperIndicator_SetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_SetMaxDisplayCount(ArkUI_SwiperIndicator* indicator, int32_t maxDisplayCount)
```

**描述**

设置圆点导航点指示器样式下，导航点显示个数的最大值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| int32_t maxDisplayCount | 导航点显示个数最大值，有效取值范围[6, 9]。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 错误码。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 成功。<br>         [ARKUI_ERROR_CODE_NO_ERROR](capi-native-type-h.md#arkui_errorcode) 如果maxDisplayCount设置范围错误, 返回错误码。 |

### OH_ArkUI_SwiperIndicator_GetMaxDisplayCount()

```c
int32_t OH_ArkUI_SwiperIndicator_GetMaxDisplayCount(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取圆点导航点指示器样式下，导航点显示个数的最大值。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 导航点显示个数最大值，有效取值范围[6, 9]。 |

### OH_ArkUI_SwiperDigitIndicator_Create()

```c
ArkUI_SwiperDigitIndicator *OH_ArkUI_SwiperDigitIndicator_Create()
```

**描述**

创建Swiper组件的数字导航指示器。

**起始版本：** 19

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator *](capi-arkui-nativemodule-arkui-swiperdigitindicator.md) | 数字导航指示器对象指针。 |

### OH_ArkUI_SwiperDigitIndicator_Destroy()

```c
void OH_ArkUI_SwiperDigitIndicator_Destroy(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

销毁Swiper组件的数字导航指示器指针。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

### OH_ArkUI_SwiperDigitIndicator_SetStartPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetStartPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

设置数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，设置其距离Swiper组件右边的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float value | 数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，其距离Swiper组件右边的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_GetStartPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetStartPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，获取其距离Swiper组件右边的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数字导航指示器距离Swiper组件左边的距离，在从右至左显示的语言模式下，其距离Swiper组件右边的距离。单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_SetTopPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetTopPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

设置数字导航指示器距离Swiper组件顶部的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float value | 数字导航指示器距离Swiper组件顶部的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_GetTopPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetTopPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取数字导航指示器距离Swiper组件顶部的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数字导航指示器距离Swiper组件顶部的距离。单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_SetEndPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetEndPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

设置数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，设置其距离Swiper组件左边的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float value | 数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，其距离Swiper组件左边的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_GetEndPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetEndPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，获取其距离Swiper组件左边的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数字导航指示器距离Swiper组件右边的距离，在从右至左显示的语言模式下，其距离Swiper组件左边的距离。单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_SetBottomPosition()

```c
void OH_ArkUI_SwiperDigitIndicator_SetBottomPosition(ArkUI_SwiperDigitIndicator* indicator, float value)
```

**描述**

设置数字导航指示器距离Swiper组件底部的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float value | 数字导航指示器距离Swiper组件底部的距离。默认值：0，单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_GetBottomPosition()

```c
float OH_ArkUI_SwiperDigitIndicator_GetBottomPosition(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取数字导航指示器距离Swiper组件底部的距离。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 数字导航指示器距离Swiper组件底部的距离。单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_SetFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t color)
```

**描述**

设置Swiper组件数字导航指示器字体颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| uint32_t color | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。默认值：0xFF182431。 |

### OH_ArkUI_SwiperDigitIndicator_GetFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取Swiper组件数字导航指示器字体颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator, uint32_t selectedColor)
```

**描述**

设置被选中Swiper组件数字导航指示器字体颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| uint32_t selectedColor | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。默认值：0xFF182431。 |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor()

```c
uint32_t OH_ArkUI_SwiperDigitIndicator_GetSelectedFontColor(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取被选中Swiper组件数字导航指示器字体颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 颜色类型，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperDigitIndicator_SetFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**描述**

设置Swiper组件数字导航指示器字体大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float size | 字体大小数值，单位为fp。 |

### OH_ArkUI_SwiperDigitIndicator_GetFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取Swiper组件数字导航指示器字体大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 字体大小数值，单位为fp。 |

### OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize()

```c
void OH_ArkUI_SwiperDigitIndicator_SetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator, float size)
```

**描述**

设置被选中Swiper组件数字导航指示器字体大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |
| float size | 字体大小数值，单位为fp。 |

### OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize()

```c
float OH_ArkUI_SwiperDigitIndicator_GetSelectedFontSize(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取被选中Swiper组件数字导航指示器字体大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 数字导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 字体大小数值，单位为fp。 |

### OH_ArkUI_SwiperArrowStyle_Create()

```c
ArkUI_SwiperArrowStyle *OH_ArkUI_SwiperArrowStyle_Create()
```

**描述**

创建Swiper组件的导航箭头。

**起始版本：** 19

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_SwiperArrowStyle *](capi-arkui-nativemodule-arkui-swiperarrowstyle.md) | 导航箭头对象指针。 |

### OH_ArkUI_SwiperArrowStyle_Destroy()

```c
void OH_ArkUI_SwiperArrowStyle_Destroy(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

销毁Swiper组件的导航箭头指针。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

### OH_ArkUI_SwiperArrowStyle_SetShowBackground()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showBackground)
```

**描述**

设置Swiper组件导航箭头底板是否显示。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| int32_t showBackground | 导航箭头底板是否显示，0：不显示，1：显示，默认值：0。 |

### OH_ArkUI_SwiperArrowStyle_GetShowBackground()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowBackground(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头底板是否显示。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 导航箭头底板是否显示，0：不显示，1：显示。 |

### OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle()

```c
void OH_ArkUI_SwiperArrowStyle_SetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle, int32_t showSidebarMiddle)
```

**描述**

设置Swiper组件导航箭头显示位置。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| int32_t showSidebarMiddle | 导航箭头显示位置，0：显示在导航指示器两侧，1：显示在Swiper组件两侧，默认值：0。 |

### OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle()

```c
int32_t OH_ArkUI_SwiperArrowStyle_GetShowSidebarMiddle(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头显示位置。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 导航箭头显示位置，0：显示在导航指示器两侧，1：显示在Swiper组件两侧。 |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle, float backgroundSize)
```

**描述**

设置Swiper组件导航箭头底板大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| float backgroundSize | 导航箭头底板大小，单位：vp。默认值：显示在导航指示器两侧24vp，显示在Swiper两侧32vp。 |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetBackgroundSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头底板大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航箭头底板大小，单位：vp。 |

### OH_ArkUI_SwiperArrowStyle_SetBackgroundColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t backgroundColor)
```

**描述**

设置Swiper组件导航箭头底板颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| uint32_t backgroundColor | 导航箭头底板颜色，0xargb格式，形如 0xFFFF0000表示红色。默认值：显示在导航指示器两侧为0x00000000，显示在Swiper两侧为0x19182431。 |

### OH_ArkUI_SwiperArrowStyle_GetBackgroundColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetBackgroundColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头底板颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 导航箭头底板颜色，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperArrowStyle_SetArrowSize()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle, float arrowSize)
```

**描述**

设置Swiper组件导航箭头大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| float arrowSize | 导航箭头大小，单位：vp。默认值：显示在导航指示器两侧18vp，显示在Swiper两侧24vp。显示导航箭头底板时，arrowSize固定为backgroundSize的3/4。 |

### OH_ArkUI_SwiperArrowStyle_GetArrowSize()

```c
float OH_ArkUI_SwiperArrowStyle_GetArrowSize(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航箭头大小，单位：vp。 |

### OH_ArkUI_SwiperArrowStyle_SetArrowColor()

```c
void OH_ArkUI_SwiperArrowStyle_SetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle, uint32_t arrowColor)
```

**描述**

设置Swiper组件导航箭头颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |
| uint32_t arrowColor | 导航箭头颜色，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperArrowStyle_GetArrowColor()

```c
uint32_t OH_ArkUI_SwiperArrowStyle_GetArrowColor(ArkUI_SwiperArrowStyle* arrowStyle)
```

**描述**

获取Swiper组件导航箭头颜色。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)* arrowStyle | 导航箭头对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| uint32_t | 导航箭头颜色，0xargb格式，形如 0xFFFF0000表示红色。 |

### OH_ArkUI_SwiperIndicator_SetSpace()

```c
void OH_ArkUI_SwiperIndicator_SetSpace(ArkUI_SwiperIndicator* indicator, float space)
```

**描述**

设置导航点间距。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |
| float space | 导航点间距。默认值：8，单位：vp。 |

### OH_ArkUI_SwiperIndicator_GetSpace()

```c
float OH_ArkUI_SwiperIndicator_GetSpace(ArkUI_SwiperIndicator* indicator)
```

**描述**

获取导航点间距。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| float | 导航点间距。单位：vp。 |

### OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom()

```c
void OH_ArkUI_SwiperDigitIndicator_SetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator, int32_t ignoreSize)
```

**描述**

设置OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 导航指示器对象指针。 |
| int32_t ignoreSize | 是否忽略导航点大小。1表示忽略导航点大小，0表示不忽略，默认值0。 |

### OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom()

```c
int32_t OH_ArkUI_SwiperDigitIndicator_GetIgnoreSizeOfBottom(ArkUI_SwiperDigitIndicator* indicator)
```

**描述**

获取OH_ArkUI_SwiperDigitIndicator_SetBottomPosition是否忽略导航点大小。

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)* indicator | 导航指示器对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 是否忽略导航点大小。 |


