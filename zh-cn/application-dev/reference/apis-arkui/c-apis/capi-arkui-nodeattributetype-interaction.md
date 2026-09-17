# 交互属性

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_VISIBILITY

```c
NODE_VISIBILITY
```

**描述：**

组件是否可见属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：控制当前组件显示或隐藏，参数类型{@link ArkUI_Visibility}，默认值为ARKUI_VISIBILITY_VISIBLE。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：控制当前组件显示或隐藏，参数类型{@link ArkUI_Visibility}，默认值为ARKUI_VISIBILITY_VISIBLE。各枚举值含义及对应数字：ARKUI_VISIBILITY_VISIBLE(0)表示可见，ARKUI_VISIBILITY_HIDDEN(1)表示隐藏但占位，ARKUI_VISIBILITY_NONE(2)表示隐藏且不占位。</li> </ul>

**起始版本：** 12

### NODE_HIT_TEST_BEHAVIOR

```c
NODE_HIT_TEST_BEHAVIOR
```

**描述：**

触摸测试类型，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型{@link ArkUI_HitTestMode}，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。</li><br></ul><br>**返回：**<br><ul><br><li><b>.value[0].i32</b>：控制当前组件的触摸测试类型，参数类型{@link ArkUI_HitTestMode}，默认值为ARKUI_HIT_TEST_MODE_DEFAULT。</li> </ul>

**起始版本：** 12

### NODE_FOCUSABLE

```c
NODE_FOCUSABLE
```

**描述：**

获焦属性，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。默认为不可获焦。</li><br></ul><br>**返回：**<br><ul><br><li><b>.value[0].i32</b>：参数类型为1表示可获焦，为0表示不可获焦。</li> </ul>

**起始版本：** 12

### NODE_DEFAULT_FOCUS

```c
NODE_DEFAULT_FOCUS
```

**描述：**

默认焦点属性，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。</li><br></ul><br>**返回：**<br><ul><br><li><b>.value[0].i32</b>：参数值为1表示是默认焦点，为0表示不是默认焦点。</li> </ul>

**起始版本：** 12

### NODE_RESPONSE_REGION

```c
NODE_RESPONSE_REGION
```

**描述：**

触摸热区属性，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 <br>**说明：**<br><br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到前20个。 **参数：**<br><ul> <li>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。</li><br><li>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。</li><br><li>.data[2].f32</b>：触摸热区的宽度，单位为百分比。</li><br><li>.data[3].f32</b>：触摸热区的高度，单位为百分比。</li><br><li>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li><br></ul><br>**返回：**<br><ul><br><li>.data[0].f32</b>：触摸点相对于组件左上角的x轴坐标，单位为vp。</li><br><li>.data[1].f32</b>：触摸点相对于组件左上角的y轴坐标，单位为vp。</li><br><li>.data[2].f32</b>：触摸热区的宽度，单位为百分比。</li><br><li>.data[3].f32</b>：触摸热区的高度，单位为百分比。</li><br><li>.data[4...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li> </ul>

**起始版本：** 12

### NODE_OVERLAY

```c
NODE_OVERLAY
```

**描述：**

定义遮罩属性，支持属性设置，属性重置和属性获取。开发者可以通过如下.string或.object设置浮层内容，.string有更高的优先级。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.string</b>：遮罩文本。</li><br><li>.value[0]?.i32</b>：可选值，浮层相对于组件的位置，参数类型{@link ArkUI_Alignment}，默认值为ARKUI_ALIGNMENT_TOP_START。</li><br><li>.value[1]?.f32</b>：可选值，浮层基于自身左上角的偏移量X，单位为vp，默认值为0vp。</li><br><li>.value[2]?.f32</b>：可选值，浮层基于自身左上角的偏移量Y，单位为vp，默认值为0vp。</li><br><li>.value[3]?.i32</b>：可选值，浮层的布局方向，参数类型{@link ArkUI_Direction}，默认值为ARKUI_DIRECTION_LTR。<br>在大部分场景下，这个参数都应该被设置成Auto，这个模式允许系统自动处理布局方向，如果在某些场景下需要保持特定的方向，设置这个属性为LTR（Left-to-Right）或者RTL（Right-to-Left）。<br>从API version 21开始支持。</li><br><li>.object</b>：用于overlay的节点树，参数类型为{@link ArkUI_NodeHandle}，默认值为nullptr。从API version 21开始支持。</li><br></ul><br>**返回：**<br><ul><br><li>.string</b>：遮罩文本。</li><br><li>.value[0].i32</b>：浮层相对于组件的位置，参数类型{@link ArkUI_Alignment}，默认值为ARKUI_ALIGNMENT_TOP_START。</li><br><li>.value[1].f32</b>：浮层基于自身左上角的偏移量X，单位为vp。</li><br><li>.value[2].f32</b>：浮层基于自身左上角的偏移量Y，单位为vp。</li><br><li>.value[3].i32</b>：浮层的布局方向，参数类型{@link ArkUI_Direction}，默认值为ARKUI_DIRECTION_LTR。从API version 21开始支持。</li><br><li>.object</b>：用于overlay的节点树，参数类型为{@link ArkUI_NodeHandle}。从API version 21开始支持。</li> </ul>

**起始版本：** 12

### NODE_FOCUS_STATUS

```c
NODE_FOCUS_STATUS
```

**描述：**

组件获取焦点属性，支持属性设置，属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 <br>**说明：**<br><br>设置参数为0时，当前层级页面获焦组件失焦，焦点转移到根容器上。 **参数：**<br><ul> <li>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32</b>：参数值为1表示组件获焦，为0表示组件失焦。</li> </ul>

**起始版本：** 12

### NODE_FOCUS_ON_TOUCH

```c
NODE_FOCUS_ON_TOUCH
```

**描述：**

设置当前组件是否支持点击获焦能力，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32：参数值为1表示支持点击获焦，为0表示不支持点击获焦。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：参数值为1表示支持点击获焦，为0表示不支持点击获焦。</li> </ul>

**起始版本：** 12

### NODE_VISIBLE_AREA_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_CHANGE_RATIO = 93
```

**描述：**

Defines the visible area ratio (visible area/total area of the component) threshold for invoking the visible area change event of the component. **Format of the {@link ArkUI_AttributeItem} parameter for setting the<br>attribute:**<br><ul><br><li>.value[...].f32: threshold array. The value ranges from 0 to 1.</li><br><li>.object: The parameter type is {@link ArkUI_VisibleAreaEventOptions}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[...].f32: threshold array.</li><br><li>.object: The return type is {@link ArkUI_VisibleAreaEventOptions}.</li> </ul>

**起始版本：** 12

### NODE_FOCUS_BOX

```c
NODE_FOCUS_BOX = 96
```

**描述：**

设置当前组件系统焦点框样式。 <br>作为属性设置方法参数{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32</b>：焦点框相对组件边缘的距离。正数代表外侧，负数代表内侧。不支持百分比。</li><br><li>.value[1].f32</b>：焦点框宽度。不支持负数和百分比。</li><br><li>.value[2].u32</b>：焦点框颜色。</li> </ul>

**起始版本：** 12

### NODE_CLICK_DISTANCE

```c
NODE_CLICK_DISTANCE = 97
```

**描述：**

组件所绑定的点击手势移动距离限制，支持属性设置。 <br>作为属性设置方法参数{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32</b>：表示识别点击手势时允许手指在该范围内移动，单位为vp。</li> </ul>

**起始版本：** 12

### NODE_TAB_STOP

```c
NODE_TAB_STOP = 98
```

**描述：**

控制焦点是否能停在当前组件，支持属性设置，属性重置和属性获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32</b>：参数值为1表示焦点能停在当前组件，为0表示焦点不能停在当前组件。默认值为0。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32</b>：参数值为1表示焦点停在当前组件，为0表示焦点未停在当前组件。</li> </ul>

**起始版本：** 14

### NODE_NEXT_FOCUS

```c
NODE_NEXT_FOCUS = 101
```

**描述：**

设置下一个走焦节点。 <br>作为属性设置方法参数{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32</b>：走焦类型，定义在{@link ArkUI_FocusMove}。</li><br><li>.object</b>：下一个焦点。参数类型为{@link ArkUI_NodeHandle}。</li> </ul>

**起始版本：** 18

### NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO

```c
NODE_VISIBLE_AREA_APPROXIMATE_CHANGE_RATIO = 102
```

**描述：**

设置可见区域变化监听的参数。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br><br>**说明：**<br><br>非实时回调，实际回调与预期间隔可能存在差别。两次可见区域回调的时间间隔不小于预期更新间隔。当开发者设置的预期间隔过小时，由系统负载决定实际回调间隔时间。当前接口的可见区域回调阈值默认包含0。例如，开发者设置回调阈值为[<br>0.5]，实际生效的阈值为[0.0, 0.5]。<br>**参数：**<br><ul><br><li>.object</b>：参数类型为{@link ArkUI_VisibleAreaEventOptions}。</li><br></ul><br>**返回：**<br><ul><br><li>.object</b>：参数类型为{@link ArkUI_VisibleAreaEventOptions}。</li> </ul>

**起始版本：** 17

### NODE_ENABLE_CLICK_SOUND_EFFECT

```c
NODE_ENABLE_CLICK_SOUND_EFFECT = 110
```

**描述：**

设置组件是否启用默认点击音效。此功能仅在TV上生效，在其他设备上启用默认点击音效也不会播放音效。是否能够发音依赖设备声音相关的设置，如静音模式下不会播放音效。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32</b>：参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效，默认值为1。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32</b>：表示此节点是否启用了默认的点击音效。参数取值为1或0，1表示启用默认点击音效，0表示禁用默认点击音效。</li> </ul>

**起始版本：** 24

### NODE_HOVER_EFFECT

```c
NODE_HOVER_EFFECT = 112
```

**描述：**

定义组件被悬停时的效果。该属性可根据需要通过API进行设置、重置和获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为{@link ArkUI_HoverEffect}。默认值为ARKUI_HOVER_EFFECT_AUTO。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32</b>：组件在悬停状态下的悬停效果。参数类型为{@link ArkUI_HoverEffect}。</li> </ul>

**起始版本：** 23

### NODE_FOCUS_SCOPE_ID

```c
NODE_FOCUS_SCOPE_ID = 113
```

**描述：**

将容器设置为具有特定标识符的焦点组，支持属性设置、属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.string</b>：焦点作用域标识符。</li> <li>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。</li><br><li>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部，<br>0表示箭头键无法将焦点从焦点组内部移至外部。</li><br></ul><br>**返回：**<br><ul><br><li>.string</b>：焦点作用域标识符。</li><br><li>.value[0].i32</b>：该作用域是否为焦点组，默认值为0。取值范围为1或0。1表示设置为焦点组，0表示组件未被设置为焦点组。</li><br><li>.value[1].i32</b>：箭头键是否可以将焦点从焦点组内部移至外部，仅当isGroup为true时有效，默认值为1。取值范围为1或0。1表示箭头键可以将焦点从焦点组内部移至外部， 0表示箭头键无法将焦点从焦点组内部移至外部。</li> </ul>

**起始版本：** 23

### NODE_FOCUS_SCOPE_PRIORITY

```c
NODE_FOCUS_SCOPE_PRIORITY = 114
```

**描述：**

设置组件在特定焦点作用域内的焦点优先级，支持属性设置、属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.string</b>：焦点作用域标识符。</li><br><li>.value[0].i32</b>：焦点作用域内获焦优先级。参数类型为{@link ArkUI_FocusPriority}。默认值为ARKUI_FOCUS_PRIORITY_AUTO。</li><br></ul><br>**返回：**<br><ul><br><li>.string</b>：焦点作用域标识符。</li><br><li>.value[0].i32</b>：焦点作用域优先级。参数类型为{@link ArkUI_FocusPriority}。</li> </ul>

**起始版本：** 23

### NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD

```c
NODE_ON_CLICK_EVENT_DISTANCE_THRESHOLD = 115
```

**描述：**

设置点击事件的距离阈值，支持属性设置、属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].f32</b>：点击事件移动阈值。取值范围(0, +∞)。默认值为+∞，单位vp。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32</b>：点击事件移动阈值。</li> </ul>

**起始版本：** 23

### NODE_RESPONSE_REGION_LIST

```c
NODE_RESPONSE_REGION_LIST = 116
```

**描述：**

设置组件事件的响应区域，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br><br>**说明：**<br><br>设置时data数据大小无数量限制，均可以设置成功，但仅支持获取到20个。获取到的data数组顺序与设置顺序可能存在差异。<br>**参数：**<br><ul><br><li>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为{@link ArkUI_ResponseRegionSupportedTool}。默认值：</li><br><li>ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。</li><br><li>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。</li><br><li>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。</li><br><li>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。</li><br><li>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。</li><br><li>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li><br></ul><br>**返回：**<br><ul><br><li>.data[0].i32</b>：适用于此响应区域的事件工具类型。参数类型为{@link ArkUI_ResponseRegionSupportedTool}。默认值：</li> <li>ARKUI_RESPONSE_REGIN_SUPPORTED_TOOL_ALL。</li> <li>.data[1].f32</b>：触摸点相对于组件左上角的x轴坐标，默认值：0.0，单位为vp。</li><br><li>.data[2].f32</b>：触摸点相对于组件左上角的y轴坐标，默认值：0.0，单位为vp。</li><br><li>.data[3].f32</b>：触摸热区的宽度，默认值：100.0，单位为百分比。</li><br><li>.data[4].f32</b>：触摸热区的高度，默认值：100.0，单位为百分比。</li><br><li>.data[5...].f32</b>：可以设置多个手势响应区域，顺序和上述一致。</li> </ul>

**起始版本：** 23

### NODE_MONOPOLIZE_EVENTS

```c
NODE_MONOPOLIZE_EVENTS = 117
```

**描述：**

定义独占事件属性，该属性可根据需要通过API进行设置、重置和获取。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32</b>：取值范围为1或0。1表示设置组件独占，0表示组件未设置独占属性。</li> </ul>

**起始版本：** 23


