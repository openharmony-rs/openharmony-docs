# node_scroll.h

## 概述

Provides shared scroll-related enum definitions for <b>NativeNode</b> APIs.

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_EdgeEffect](#arkui_edgeeffect) | ArkUI_EdgeEffect | 定义边缘滑动效果枚举值。Grid、Scroll、WaterFlow组件默认值为ARKUI_EDGE_EFFECT_NONE，List组件默认值为ARKUI_EDGE_EFFECT_SPRING。 |
| [ArkUI_BarState](#arkui_barstate) | ArkUI_BarState | 定义文本控制滚动条状态枚举值。 |
| [ArkUI_EffectEdge](#arkui_effectedge) | ArkUI_EffectEdge | 定义边缘效果生效边缘的方向枚举值。 |
| [ArkUI_ScrollDirection](#arkui_scrolldirection) | ArkUI_ScrollDirection | 定义Scroll组件排列方向枚举值。 |
| [ArkUI_ScrollSnapAlign](#arkui_scrollsnapalign) | ArkUI_ScrollSnapAlign | 定义列表项滚动结束对齐效果枚举值。 |
| [ArkUI_ScrollSnapAnimationSpeed](#arkui_scrollsnapanimationspeed) | ArkUI_ScrollSnapAnimationSpeed | 定义列表限位滚动动画速度。 |
| [ArkUI_ScrollBarDisplayMode](#arkui_scrollbardisplaymode) | ArkUI_ScrollBarDisplayMode | 定义滚动条状态枚举值。 |
| [ArkUI_ContentClipMode](#arkui_contentclipmode) | ArkUI_ContentClipMode | 定义滚动容器的内容层裁剪区域枚举值。 |
| [ArkUI_ScrollNestedMode](#arkui_scrollnestedmode) | ArkUI_ScrollNestedMode | 定义嵌套滚动选项。 |
| [ArkUI_ScrollEdge](#arkui_scrolledge) | ArkUI_ScrollEdge | 定义滚动到的边缘位置。 |
| [ArkUI_ScrollAlignment](#arkui_scrollalignment) | ArkUI_ScrollAlignment | 滚动到具体item时的对齐方式。 |
| [ArkUI_ScrollState](#arkui_scrollstate) | ArkUI_ScrollState | 定义当前滚动状态。 |
| [ArkUI_ScrollSource](#arkui_scrollsource) | ArkUI_ScrollSource | 定义滚动来源枚举值。 |

## 枚举类型说明

### ArkUI_EdgeEffect

```c
enum ArkUI_EdgeEffect
```

**描述**

定义边缘滑动效果枚举值。Grid、Scroll、WaterFlow组件默认值为ARKUI_EDGE_EFFECT_NONE，List组件默认值为ARKUI_EDGE_EFFECT_SPRING。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EDGE_EFFECT_SPRING = 0 | 弹性物理动效，滑动到边缘后可以根据初始速度或通过触摸事件继续滑动一段距离，松手后回弹。 |
| ARKUI_EDGE_EFFECT_FADE | 阴影效果，滑动到边缘后会有圆弧状的阴影。 |
| ARKUI_EDGE_EFFECT_NONE | 滑动到边缘后无效果。 |

### ArkUI_BarState

```c
enum ArkUI_BarState
```

**描述**

定义文本控制滚动条状态枚举值。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_BAR_STATE_OFF = 0 | 不显示。 |
| ARKUI_BAR_STATE_AUTO = 1 | 按需显示。 |
| ARKUI_BAR_STATE_ON = 2 | 常驻显示。 |

### ArkUI_EffectEdge

```c
enum ArkUI_EffectEdge
```

**描述**

定义边缘效果生效边缘的方向枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_EFFECT_EDGE_START = 1 | 起始边生效。 |
| ARKUI_EFFECT_EDGE_END = 2 | 末尾边生效。 |

### ArkUI_ScrollDirection

```c
enum ArkUI_ScrollDirection
```

**描述**

定义Scroll组件排列方向枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_DIRECTION_VERTICAL = 0 | 仅支持竖直方向滚动。 |
| ARKUI_SCROLL_DIRECTION_HORIZONTAL | 仅支持水平方向滚动。 |
| ARKUI_SCROLL_DIRECTION_NONE = 3 | 禁止滚动。 |
| ARKUI_SCROLL_DIRECTION_FREE = 4 |  |

### ArkUI_ScrollSnapAlign

```c
enum ArkUI_ScrollSnapAlign
```

**描述**

定义列表项滚动结束对齐效果枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ALIGN_NONE = 0 | 默认无列表滚动对齐效果。 |
| ARKUI_SCROLL_SNAP_ALIGN_START | 视图中的第一项将在列表的开头对齐。 |
| ARKUI_SCROLL_SNAP_ALIGN_CENTER | 视图中的中间项将在列表中心对齐。 |
| ARKUI_SCROLL_SNAP_ALIGN_END | 视图中的最后一项将在列表末尾对齐。 |

### ArkUI_ScrollSnapAnimationSpeed

```c
enum ArkUI_ScrollSnapAnimationSpeed
```

**描述**

定义列表限位滚动动画速度。

**起始版本：** 22

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SNAP_ANIMATION_NORMAL = 0 | 限位滚动动画速度快。 |
| ARKUI_SCROLL_SNAP_ANIMATION_SLOW = 1 | 限位滚动动画速度慢。 |

### ArkUI_ScrollBarDisplayMode

```c
enum ArkUI_ScrollBarDisplayMode
```

**描述**

定义滚动条状态枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_OFF = 0 | 不显示。 |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_AUTO | 按需显示(触摸时显示，2s后消失)。 |
| ARKUI_SCROLL_BAR_DISPLAY_MODE_ON | 常驻显示。 |

### ArkUI_ContentClipMode

```c
enum ArkUI_ContentClipMode
```

**描述**

定义滚动容器的内容层裁剪区域枚举值。

**起始版本：** 18

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_CONTENT_CLIP_MODE_CONTENT_ONLY = 0 | 按内容区裁剪。 |
| ARKUI_CONTENT_CLIP_MODE_BOUNDARY | 按组件区域裁剪。 |
| ARKUI_CONTENT_CLIP_MODE_SAFE_AREA | Clip to the {@link safe area} configured for the component. |

### ArkUI_ScrollNestedMode

```c
enum ArkUI_ScrollNestedMode
```

**描述**

定义嵌套滚动选项。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_NESTED_MODE_SELF_ONLY = 0 | 只自身滚动，不与父组件联动。 |
| ARKUI_SCROLL_NESTED_MODE_SELF_FIRST | 自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则子组件触发边缘效果。 |
| ARKUI_SCROLL_NESTED_MODE_PARENT_FIRST | 父组件先滚动，父组件滚动到边缘以后自身滚动。自身滚动到边缘后，如果有边缘效果，会触发自身的边缘效果，否则触发父组件的边缘效果。 |
| ARKUI_SCROLL_NESTED_MODE_PARALLEL | 自身和父组件同时滚动，自身和父组件都到达边缘以后，如果自身有边缘效果，则自身触发边缘效果，否则父组件触发边缘效果。 |

### ArkUI_ScrollEdge

```c
enum ArkUI_ScrollEdge
```

**描述**

定义滚动到的边缘位置。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_EDGE_TOP = 0 | 竖直方向上边缘。 |
| ARKUI_SCROLL_EDGE_BOTTOM | 竖直方向下边缘。 |
| ARKUI_SCROLL_EDGE_START | 水平方向起始位置。 |
| ARKUI_SCROLL_EDGE_END | 水平方向末尾位置。 |

### ArkUI_ScrollAlignment

```c
enum ArkUI_ScrollAlignment
```

**描述**

滚动到具体item时的对齐方式。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_ALIGNMENT_START = 0 | 首部对齐。指定item首部与容器首部对齐。 |
| ARKUI_SCROLL_ALIGNMENT_CENTER | 居中对齐。指定item主轴方向居中对齐于容器。 |
| ARKUI_SCROLL_ALIGNMENT_END | 尾部对齐。指定item尾部与容器尾部对齐。 |
| ARKUI_SCROLL_ALIGNMENT_AUTO | 自动对齐。若指定item完全处于显示区，不做调整。否则依照滑动距离最短的原则，将指定item首部对齐或尾部对齐于容器,使指定item完全处于显示区。 |

### ArkUI_ScrollState

```c
enum ArkUI_ScrollState
```

**描述**

定义当前滚动状态。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_STATE_IDLE = 0 | 空闲状态。使用控制器提供的方法控制滚动时触发，拖动滚动条滚动时触发。 |
| ARKUI_SCROLL_STATE_SCROLL | 滚动状态。使用手指拖动容器滚动时触发。 |
| ARKUI_SCROLL_STATE_FLING | 惯性滚动状态。快速划动松手后进行惯性滚动和划动到边缘回弹时触发。 |

### ArkUI_ScrollSource

```c
enum ArkUI_ScrollSource
```

**描述**

定义滚动来源枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_SCROLL_SOURCE_DRAG = 0 | 手指拖动。 |
| ARKUI_SCROLL_SOURCE_FLING | 手指拖动后的惯性滚动。 |
| ARKUI_SCROLL_SOURCE_EDGE_EFFECT | {@link EdgeEffect.Spring} for boundary crossing. |
| ARKUI_SCROLL_SOURCE_OTHER_USER_INPUT | 除了拖动以外的其他用户输入，如鼠标滚轮、键盘事件等。 |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR | 拖动滚动条。 |
| ARKUI_SCROLL_SOURCE_SCROLL_BAR_FLING | 拖动滚动条后的惯性滚动。 |
| ARKUI_SCROLL_SOURCE_SCROLLER | 滚动控制器引起的无动画的滚动。 |
| ARKUI_SCROLL_SOURCE_ANIMATION | 滚动控制器引起的带动画的滚动。 |


