# ArkUI_NodeAttributeType（导航类组件相关属性）
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @Hu_ZeQi-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

```c
enum ArkUI_NodeAttributeType
```

## 概述

定义ArkUI（方舟UI框架）在Native侧可以设置的导航类组件相关属性样式集合，包含Swiper（滑动容器组件）、ArcSwiper和ArcAlphabetIndexer组件属性设置。其中，Swiper属性用于设置循环播放、自动播放、导航指示器、动画效果等轮播能力；ArcSwiper属性用于设置弧形滑动容器的当前索引、导航点指示器、滑动方向、边缘效果等能力；ArcAlphabetIndexer属性用于设置弧形字母索引器的索引数组、颜色、字体、弹窗和选中项等能力。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

## NODE_SWIPER_LOOP

```c
NODE_SWIPER_LOOP = MAX_NODE_SCOPE_NUM * ARKUI_NODE_SWIPER = 1001000
```

Swiper是否开启循环，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 控制是否开启循环，0表示不循环，1表示循环，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否开启循环，0表示不循环，1表示循环。 |

## NODE_SWIPER_AUTO_PLAY

```c
NODE_SWIPER_AUTO_PLAY = 1001001
```

Swiper子组件是否自动播放，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 控制子组件是否自动播放，0表示不自动播放，1表示自动播放，默认值为0。 |
| .value[1]?.i32 | 手指按下是否停止自动播放，0表示停止，1表示不停止，默认值为0。该参数从API version 16开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 子组件是否自动播放，0表示不自动播放，1表示自动播放。 |
| .value[1].i32 | 手指按下是否停止自动播放，0表示停止，1表示不停止。该参数从API version 16开始支持。 |

## NODE_SWIPER_SHOW_INDICATOR

```c
NODE_SWIPER_SHOW_INDICATOR = 1001002
```

Swiper是否显示导航点指示器，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否显示导航点指示器，0表示不显示导航点指示器，1表示显示导航点指示器。 |

## NODE_SWIPER_INTERVAL

```c
NODE_SWIPER_INTERVAL = 1001003
```

设置Swiper自动播放时播放的时间间隔，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 使用自动播放时播放的时间间隔，单位为毫秒，取值范围[0, +∞)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 使用自动播放时播放的时间间隔，单位为毫秒。 |

## NODE_SWIPER_VERTICAL

```c
NODE_SWIPER_VERTICAL = 1001004
```

设置Swiper是否为纵向滑动，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否为纵向滑动，0表示横向滑动，1表示纵向滑动，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否为纵向滑动，0表示横向滑动，1表示纵向滑动。 |

## NODE_SWIPER_DURATION

```c
NODE_SWIPER_DURATION = 1001005
```

设置Swiper子组件切换的动画时长，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 子组件切换的动画时长，单位为毫秒，取值范围[0, +∞)，默认值为400。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 子组件切换的动画时长，单位为毫秒。 |

## NODE_SWIPER_CURVE

```c
NODE_SWIPER_CURVE = 1001006
```

设置Swiper的动画曲线，支持属性设置，属性重置和属性获取接口。未设置或未重置该属性时，动画曲线为[interpolatingSpring](../../reference/apis-arkui/js-apis-curve.md#curvesinterpolatingspring10)(-1, 1, 328, 34)；设置该属性异常时，取默认值ARKUI_CURVE_LINEAR。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置动画曲线参数，参数类型[ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve)。默认值为ARKUI_CURVE_LINEAR。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 动画曲线参数，参数类型[ArkUI_AnimationCurve](capi-native-type-visual-h.md#arkui_animationcurve)。 |

## NODE_SWIPER_ITEM_SPACE

```c
NODE_SWIPER_ITEM_SPACE = 1001007
```

设置Swiper子组件与子组件之间间隙，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 子组件与子组件之间间隙数值，单位为vp，取值范围[0, +∞)，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 子组件与子组件之间间隙数值，单位为vp。 |

## NODE_SWIPER_INDEX

```c
NODE_SWIPER_INDEX = 1001008
```

设置Swiper当前在容器中显示的子组件的索引值，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 子组件的索引值，取值范围[0, 子组件数量-1]，默认值为0。 |
| .value[1]?.i32 | 跳转动画模式，参数类型[ArkUI_SwiperAnimationMode](capi-swiper-h.md#arkui_swiperanimationmode)，默认值为无动画模式。仅当次调用有效。<br>该参数从API version 15开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 子组件的索引值。 |

## NODE_SWIPER_DISPLAY_COUNT

```c
NODE_SWIPER_DISPLAY_COUNT = 1001009
```

设置Swiper一页内元素显示个数，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 视窗内显示的子元素个数，取值范围[1, +∞)，默认值为1。 |
| .value[1]?.i32 | 是否按组翻页，0表示按子元素翻页，1表示视窗内显示的子元素按组翻页，默认值为0。 |
| .string? | 此参数只能设置为“auto”。当设置为“auto”时，value[] 参数将被忽略。不设置该参数时，value[] 参数将被正常使用。<br>该参数从API version 19开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 视窗内显示的子元素个数。 |
| .value[1].i32 | 是否按组翻页，0表示按子元素翻页，1表示视窗内显示的子元素按组翻页。该参数从API version 19开始支持。 |
| .string | 值为“auto”时表示自适应显示个数。该参数从API version 19开始支持。 |

## NODE_SWIPER_DISABLE_SWIPE

```c
NODE_SWIPER_DISABLE_SWIPE = 1001010
```

设置Swiper禁用组件滑动切换功能，支持属性设置，属性重置和属性获取接口。适用场景：如只允许通过导航箭头或导航点切换页面、防止用户手势滑动干扰等场景。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否禁用组件滑动切换功能，0表示不禁用滑动切换功能，1表示禁用滑动切换功能。 |

## NODE_SWIPER_SHOW_DISPLAY_ARROW

```c
NODE_SWIPER_SHOW_DISPLAY_ARROW = 1001011
```

设置Swiper是否显示导航箭头，支持属性设置，属性重置和属性获取接口。<br/>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow)，默认值为ARKUI_SWIPER_ARROW_HIDE。 |
| ?.object | 显示导航箭头时设置箭头样式，参数类型为[ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)。不设置该参数时使用系统默认箭头样式。<br>该参数从API version 19开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 设置是否显示导航点箭头，参数类型[ArkUI_SwiperArrow](capi-swiper-h.md#arkui_swiperarrow)。 |
| .object | 箭头样式，参数类型为[ArkUI_SwiperArrowStyle](capi-arkui-nativemodule-arkui-swiperarrowstyle.md)。该参数从API version 19开始支持。 |

## NODE_SWIPER_EDGE_EFFECT_MODE

```c
NODE_SWIPER_EDGE_EFFECT_MODE = 1001012
```

设置Swiper滑动到边缘时的效果，支持属性设置，属性重置和属性获取接口。当Swiper已滑动到第一个或最后一个子组件时，用户继续滑动会触发边缘效果。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)，默认值为ARKUI_EDGE_EFFECT_SPRING。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 边缘滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)。 |

## NODE_SWIPER_NODE_ADAPTER

```c
NODE_SWIPER_NODE_ADAPTER = 1001013
```

Swiper组件适配器，支持属性设置，属性重置和属性获取接口。适用场景：当Swiper需要动态加载或复用子组件时使用适配器，如数据量较大的列表轮播、无限循环轮播等场景。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 使用[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)对象作为适配器。建议配合NODE_SWIPER_CACHED_COUNT使用以提升性能。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 返回值格式为[ArkUI_NodeAdapter](capi-arkui-nativemodule-arkui-nodeadapter8h.md)。 |

## NODE_SWIPER_CACHED_COUNT

```c
NODE_SWIPER_CACHED_COUNT = 1001014
```

Swiper组件Adapter缓存数量，支持属性设置，属性重置和属性获取接口。适用场景：用于优化Swiper性能，当子组件渲染较复杂或需要预加载更多页面时，可适当增加缓存数量。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 配合swiper组件Adapter使用，设置adapter中的缓存数量，取值范围[0, +∞)。建议根据实际业务场景合理设置，避免过大导致内存占用过高。 |
| .value[1]?.i32 | 是否显示缓存节点，0表示不显示，1表示显示，默认值为0。该参数从API version 19开始支持。 |
| .value[2]?.i32 | 缓存数量是否按组计算。0表示当NODE_SWIPER_DISPLAY_COUNT设置按组翻页时缓存数量按组计算，1表示缓存数量为真实设置数量，默认值为0。该参数从API version 24开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 配合swiper组件Adapter使用，返回adapter中的缓存数量。 |
| .value[1].i32 | 是否显示缓存节点，0表示不显示，1表示显示。该参数从API version 19开始支持。 |
| .value[2].i32 | 缓存数量是否按组计算，0表示按组计算，1表示为真实设置数量。该参数从API version 24开始支持。 |

## NODE_SWIPER_PREV_MARGIN

```c
NODE_SWIPER_PREV_MARGIN = 1001015
```

设置 Swiper 组件的前边距，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 前边距数值，单位为vp，取值范围[0, +∞)，默认值为0。 |
| .value[1]?.i32 | 是否忽略空白，1表示忽略空白，0表示不忽略空白，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 前边距数值，单位为vp。 |
| .value[1].i32 | 是否忽略空白，1表示忽略空白，0表示不忽略空白，默认值为0。 |

## NODE_SWIPER_NEXT_MARGIN

```c
NODE_SWIPER_NEXT_MARGIN = 1001016
```

设置 Swiper 组件的后边距，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 后边距数值，单位为vp，取值范围[0, +∞)，默认值为0。 |
| .value[1]?.i32 | 是否忽略空白，1表示忽略空白，0表示不忽略空白，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 后边距数值，单位为vp。 |
| .value[1].i32 | 是否忽略空白，1表示忽略空白，0表示不忽略空白，默认值为0。 |

## NODE_SWIPER_INDICATOR

```c
NODE_SWIPER_INDICATOR = 1001017
```

设置Swiper组件的导航指示器类型，支持属性设置，属性重置和属性获取接口。适用场景：ARKUI_SWIPER_INDICATOR_TYPE_DOT适用于轮播图、广告位等场景；ARKUI_SWIPER_INDICATOR_TYPE_DIGIT适用于需要显示当前页码的场景，如阅读器、图库等。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype)，默认值为ARKUI_SWIPER_INDICATOR_TYPE_DOT。 |
| .object | 导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型为[ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)。<br>导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型为[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)。<br>ArkUI_SwiperDigitIndicator类型从API version 19开始支持。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 导航指示器的类型，参数类型[ArkUI_SwiperIndicatorType](capi-swiper-h.md#arkui_swiperindicatortype)。 |
| .object | 导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DOT时参数类型为[ArkUI_SwiperIndicator](capi-arkui-nativemodule-arkui-swiperindicator.md)。<br>导航指示器的类型为ARKUI_SWIPER_INDICATOR_TYPE_DIGIT时参数类型为[ArkUI_SwiperDigitIndicator](capi-arkui-nativemodule-arkui-swiperdigitindicator.md)。<br>ArkUI_SwiperDigitIndicator类型从API version 19开始支持。 |

## NODE_SWIPER_NESTED_SCROLL

```c
NODE_SWIPER_NESTED_SCROLL = 1001018
```

设置Swiper组件和父组件的嵌套滚动模式，支持属性设置，属性重置和属性获取接口。适用场景：当Swiper嵌套在ScrollView、List等可滚动容器中时，用于协调滚动行为，避免滚动冲突。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode)<br>默认值为：ARKUI_SWIPER_NESTED_SRCOLL_SELF_ONLY。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | Swiper组件和父组件的嵌套滚动模式，参数类型[ArkUI_SwiperNestedScrollMode](capi-swiper-h.md#arkui_swipernestedscrollmode)。 |

## NODE_SWIPER_SWIPE_TO_INDEX

```c
NODE_SWIPER_SWIPE_TO_INDEX = 1001019
```

设置Swiper组件翻至指定页面。作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下，不支持属性重置和属性获取接口。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 指定页面在Swiper中的索引值，取值范围[0, 页面数量-1]。 |
| .value[1]?.i32 | 设置翻至指定页面时是否有动效。1表示有动效，0表示没有动效，默认值为0。 |

## NODE_SWIPER_INDICATOR_INTERACTIVE

```c
NODE_SWIPER_INDICATOR_INTERACTIVE = 1001020
```

设置组件导航点是否可交互。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置组件导航点交互功能，0表示导航点不可交互，1表示导航点可交互，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 组件导航点是否可交互，0表示不可交互，1表示可交互。 |

## NODE_SWIPER_PAGE_FLIP_MODE

```c
NODE_SWIPER_PAGE_FLIP_MODE = 1001021
```

设置组件鼠标滚轮翻页模式。<br>
作为属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下，作为属性获取方法返回值[ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode)格式如下。

**起始版本：** 15


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 设置组件鼠标滚轮翻页模式，参数类型[ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 组件鼠标滚轮翻页模式，参数类型[ArkUI_PageFlipMode](capi-swiper-h.md#arkui_pageflipmode)。 |

## NODE_SWIPER_AUTO_FILL

```c
NODE_SWIPER_AUTO_FILL = 1001022
```

设置Swiper一页内元素显示个数根据元素最小宽度自适应，支持属性设置，属性重置和属性获取接口。适用场景：用于响应式布局，当需要根据容器宽度自动调整每页显示的元素数量时使用，如横竖屏适配、多端适配等场景。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 19


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 元素显示最小宽度，单位为vp，取值范围(0, +∞)。 |
| .value[1]?.i32 | 是否按组翻页，0表示按子元素翻页，1表示视窗内显示的子元素按组翻页，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 元素显示最小宽度，单位为vp。 |
| .value[1].i32 | 是否按组翻页，0表示按子元素翻页，1表示视窗内显示的子元素按组翻页。 |

## NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION

```c
NODE_SWIPER_MAINTAIN_VISIBLE_CONTENT_POSITION = 1001023
```

设置Swiper在显示区域外插入或删除子组件时，是否保持当前可见内容的位置不变。适用场景：当在Swiper中动态增删子组件时，需要保持当前显示内容不跳动，如聊天记录列表、商品列表等场景。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 控制Swiper显示区域外插入或删除数据时是否保持可见内容位置不变，0表示不保持可见内容位置，1表示保持可见内容位置，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | Swiper显示区域外插入或删除数据是否保持可见内容位置不变。0表示不保持可见内容位置，1表示保持可见内容位置。 |

## NODE_SWIPER_ITEMFILLPOLICY

```c
NODE_SWIPER_ITEMFILLPOLICY = 1001024
```

设置Swiper组件的响应式布局策略，根据不同断点规格自动调整一页内显示的子组件列数。支持属性设置，属性重置和属性获取接口。适用场景：用于在不同屏幕尺寸下自适应调整每页显示的列数，如横竖屏适配、多端适配等场景。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 22


**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。 |
| .value[1]?.i32 | 是否按组翻页，0表示按子元素翻页，1表示视窗内显示的子元素按组翻页，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 在不同断点规格下的列数，数据类型[ArkUI_ItemFillPolicy](capi-native-type-h.md#arkui_itemfillpolicy)。 |
| .value[1].i32 | 是否按组翻页。 |

## NODE_ARC_ALPHABET_INDEXER_ARRAY

```c
NODE_ARC_ALPHABET_INDEXER_ARRAY = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_ALPHABET_INDEXER = 23000
```

设置索引字符串数组，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .object | 索引字符串数组，类型为字符串数组。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .object | 索引字符串数组，类型为字符串数组。 |

## NODE_ARC_ALPHABET_INDEXER_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_COLOR = 23001
```

设置索引项在非选中状态下的文本颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。默认值为0xFFFFFFFF，表示白色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。 |

## NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_COLOR = 23002
```

设置索引项在选中状态下的文本颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。默认值为0xFFFFFFFF，表示白色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。 |

## NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_COLOR = 23003
```

设置提示弹窗的文本颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。默认值为0xFFFFFFFF，表示白色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 文本颜色，0xargb格式。 |

## NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED_BACKGROUND_COLOR = 23004
```

设置索引项在选中状态下的背景颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 背景颜色，0xargb格式。默认值为0xFF1F71FF，表示蓝色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 背景颜色，0xargb格式。 |

## NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_BACKGROUND_COLOR = 23005
```

设置提示弹窗的背景颜色，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].u32 | 背景颜色，0xargb格式。默认值为0xD8404040，表示深灰色。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].u32 | 背景颜色，0xargb格式。 |

## NODE_ARC_ALPHABET_INDEXER_USE_POPUP

```c
NODE_ARC_ALPHABET_INDEXER_USE_POPUP = 23006
```

设置是否使用提示弹窗，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否使用提示弹窗，0表示不使用弹窗，1表示使用弹窗，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否使用提示弹窗。 |

## NODE_ARC_ALPHABET_SELECTED_FONT

```c
NODE_ARC_ALPHABET_SELECTED_FONT = 23007
```

设置选中索引项的字体样式，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割，为可选参数。默认值为“HarmonyOS Sans”。 |
| .value[0].f32 | 字体大小，单位为fp，为可选参数，默认值为13。 |
| .value[1].i32 | 字体粗细，为可选参数，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_W500。 |
| .value[2].i32 | 字体样式，为可选参数，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割。 |
| .value[0].f32 | 字体大小，单位为fp。 |
| .value[1].i32 | 字体粗细，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。 |
| .value[2].i32 | 字体样式，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。 |

## NODE_ARC_ALPHABET_INDEXER_POPUP_FONT

```c
NODE_ARC_ALPHABET_INDEXER_POPUP_FONT = 23008
```

设置提示弹窗的字体样式，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割，为可选参数。默认值为“HarmonyOS Sans”。 |
| .value[0].f32 | 字体大小，单位为fp，为可选参数，默认值为19。 |
| .value[1].i32 | 字体粗细，为可选参数，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_W500。 |
| .value[2].i32 | 字体样式，为可选参数，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割。 |
| .value[0].f32 | 字体大小，单位为fp。 |
| .value[1].i32 | 字体粗细，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。 |
| .value[2].i32 | 字体样式，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。 |

## NODE_ARC_ALPHABET_FONT

```c
NODE_ARC_ALPHABET_FONT = 23009
```

设置索引项的默认字体样式，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割，为可选参数。默认值为“HarmonyOS Sans”。 |
| .value[0].f32 | 字体大小，单位为fp，为可选参数，默认值为13。 |
| .value[1].i32 | 字体粗细，为可选参数，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)，默认值为ARKUI_FONT_WEIGHT_W500。 |
| .value[2].i32 | 字体样式，为可选参数，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)，默认值为ARKUI_FONT_STYLE_NORMAL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .string | 字体族，多个字体使用','进行分割。 |
| .value[0].f32 | 字体大小，单位为fp。 |
| .value[1].i32 | 字体粗细，参数类型[ArkUI_FontWeight](capi-text-h.md#arkui_fontweight)。 |
| .value[2].i32 | 字体样式，参数类型[ArkUI_FontStyle](capi-text-h.md#arkui_fontstyle)。 |

## NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE

```c
NODE_ARC_ALPHABET_INDEXER_ITEM_SIZE = 23010
```

设置字母索引条字母区域大小，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].f32 | 字母区域为圆形，设置该圆形的直径，单位为vp，默认值为24。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].f32 | 字母区域为圆形，设置该圆形的直径，单位为vp。 |

## NODE_ARC_ALPHABET_INDEXER_SELECTED

```c
NODE_ARC_ALPHABET_INDEXER_SELECTED = 23011
```

设置选中项的索引，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 选中项的索引，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 选中项的索引。 |

## NODE_ARC_ALPHABET_AUTO_COLLAPSE

```c
NODE_ARC_ALPHABET_AUTO_COLLAPSE = 23012
```

设置当索引条空间不足以显示全部字符时是否折叠字符，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 当索引条空间不足以显示全部字符时是否折叠字符，1表示自动折叠字符，0表示不折叠，默认值为1。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 当索引条空间不足以显示全部字符时是否折叠字符。 |

## NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE

```c
NODE_ARC_ALPHABET_POPUP_BACKGROUND_BLUR_STYLE = 23013
```

设置提示弹窗的背景模糊样式，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 提示弹窗的背景模糊样式，参数类型[ArkUI_BlurStyle](capi-native-type-visual-h.md#arkui_blurstyle)，默认值为ARKUI_BLUR_STYLE_NONE。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 提示弹窗的背景模糊样式。 |

## NODE_ARC_SWIPER_INDEX

```c
NODE_ARC_SWIPER_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_ARC_SWIPER = 1022000
```

设置当前在ArcSwiper容器中显示的子组件的索引，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 子组件的索引值，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 子组件的索引值。 |

## NODE_ARC_SWIPER_INDICATOR

```c
NODE_ARC_SWIPER_INDICATOR = 1022001
```

设置ArcSwiper的导航点指示器，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否显示导航点指示器，1表示显示导航点指示器，0表示不显示，默认值为1。 |
| .value[1].i32 | ArcSwiper导航点指示器的方向，参数类型[OH_ArkUI_ArcDirection](capi-native-type-h.md#oh_arkui_arcdirection)，默认值为OH_ARKUI_ARCDIRECTION_SIX_CLOCK_DIRECTION，为可选参数。 |
| .value[2].i32 | 未选中点的颜色，0xargb格式，默认值为0xA9FFFFFF，表示白色，为可选参数。 |
| .value[3].i32 | 选中点的颜色，0xargb格式，默认值为0xFF5EA1FF，表示蓝色，为可选参数。 |
| .value[4].i32 | 长按后ArcSwiper导航点指示器的背景颜色，0xargb格式，默认值为0xFF5EA1FF，表示蓝色，为可选参数。 |
| .object | 遮罩的渐变颜色，为可选参数。颜色停止点数组，每个颜色停止点由一种颜色及其停止位置组成。参数类型为[ArkUI_ColorStop](capi-arkui-nativemodule-arkui-colorstop.md)。无效颜色会被自动跳过。colors：颜色停止点的颜色。stops：颜色停止点的停止位置。size：颜色数量。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否显示导航点指示器。 |
| .value[1].i32 | ArcSwiper导航点指示器的方向。 |
| .value[2].u32 | 未选中点的颜色。 |
| .value[3].u32 | 选中点的颜色。 |
| .value[4].u32 | 长按后ArcSwiper导航点指示器的背景颜色。 |
| .object | 遮罩的渐变颜色。 |

## NODE_ARC_SWIPER_DURATION

```c
NODE_ARC_SWIPER_DURATION = 1022002
```

设置子组件切换的动画时长，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 子组件切换的动画时长，单位为毫秒，默认值为400。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 子组件切换的动画时长，单位为毫秒。 |

## NODE_ARC_SWIPER_VERTICAL

```c
NODE_ARC_SWIPER_VERTICAL = 1022003
```

设置是否为纵向滑动，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否为纵向滑动，1表示纵向滑动，0表示横向滑动，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否为纵向滑动。 |

## NODE_ARC_SWIPER_DISABLE_SWIPE

```c
NODE_ARC_SWIPER_DISABLE_SWIPE = 1022004
```

设置是否禁用滑动功能，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否禁用滑动功能，1表示禁用滑动功能，0表示不禁用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否禁用滑动功能。 |

## NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY

```c
NODE_ARC_SWIPER_DIGITAL_CROWN_SENSITIVITY = 1022005
```

设置转动表冠的灵敏度，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 转动表冠的灵敏度，参数类型[ArkUI_CrownSensitivity](capi-native-type-h.md#arkui_crownsensitivity)，默认值为ARKUI_CROWN_SENSITIVITY_MEDIUM。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 转动表冠的灵敏度。 |

## NODE_ARC_SWIPER_EFFECT_MODE

```c
NODE_ARC_SWIPER_EFFECT_MODE = 1022006
```

设置滑动到可滚动内容的边界时ArcSwiper边缘的滑动效果，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 滑动到可滚动内容的边界时ArcSwiper边缘的滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)，默认值为ARKUI_EDGE_EFFECT_SPRING。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 滑动到可滚动内容的边界时ArcSwiper边缘的滑动效果，参数类型[ArkUI_EdgeEffect](capi-scroll-h.md#arkui_edgeeffect)。 |

## NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION

```c
NODE_ARC_SWIPER_DISABLE_TRANSITION_ANIMATION = 1022007
```

设置是否禁用转场动画，支持属性设置，属性重置和属性获取接口。<br>
作为属性设置方法参数、属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式如下。<br>

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| .value[0].i32 | 是否禁用转场动画，1表示禁用转场动画，0表示不禁用，默认值为0。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| .value[0].i32 | 是否禁用转场动画。 |
