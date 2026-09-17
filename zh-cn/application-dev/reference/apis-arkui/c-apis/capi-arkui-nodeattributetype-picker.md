# 容器滑动选择器

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_PICKER_OPTION_SELECTED_INDEX

```c
NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER
```

**描述：**

定义选择器数据选择范围内默认选中项的索引。 支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].u32：索引值。默认值：0。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].u32：选择器数据选择范围内当前选中项的索引。</li> </ul>

**起始版本：** 23

### NODE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001
```

**描述：**

定义是否启用触控反馈。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否启用触控反馈。1表示启用反馈，0表示不启用。默认值：1。开启后，是否存在触控反馈取决于系统硬件支持情况。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：是否启用触控反馈。1表示启用反馈，0表示不启用。是否存在触控反馈取决于系统硬件支持情况。</li> </ul>

**起始版本：** 23

### NODE_PICKER_CAN_LOOP

```c
NODE_PICKER_CAN_LOOP = 1018002
```

**描述：**

定义选择器是否支持滚动循环。支持属性设置，属性重置和属性获取接口。 使用场景：循环滚动适用于选项有限且希望提供快速选择体验的场景（如性别选择）；非循环滚动适用于选项有明确边界、需要限制用户选择范围的场景。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：是否支持滚动循环。1表示支持滚动循环，0表示不支持。默认值：1。如果子组件的个数小于8个，无论设置为1还是0，都不会循环滚动。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：是否支持滚动循环。返回0表示不支持滚动循环，返回1表示支持滚动循环。</li> </ul>

**起始版本：** 23

### NODE_PICKER_SELECTION_INDICATOR

```c
NODE_PICKER_SELECTION_INDICATOR = 1018003
```

**描述：**

设置选择指示器的类型和参数。支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.object：参数类型为{@link ArkUI_PickerIndicatorStyle}。默认值：<br>{<br>type: PickerIndicatorType.BACKGROUND,<br>borderRadius: {<br>value:12,<br>unit:LengthUnit.vp<br>},<br>backgroundColor: 'sys.color.comp_background_tertiary'<br>}<br>未设置时使用默认值。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.object：当前设置的选择指示器样式对象，类型为{@link ArkUI_PickerIndicatorStyle}。</li> </ul>

**起始版本：** 23

### NODE_PICKER_DISPLAYED_ITEM_COUNT

```c
NODE_PICKER_DISPLAYED_ITEM_COUNT = 1018004
```

**描述：**

设置Picker容器可见选项的数量，语义与ArkTS侧UIPickerComponent的displayedItemCount一致。 未设置时，可见选项为7行。Picker为立体滚轮样式时，除选中项外的选项会按角度旋转，实际可视高度会小于选项行高；若增大可见行数或行高，请相应增大容器高度，详见UIPickerComponent。 支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].i32：可见选项数量。取值范围为<b>[2, 9]</b>内的整数。传入小数时按向下取整处理；<br>传入偶数时，会规范为不小于该值的奇数（例如2变为3、8变为9）。不在取值范围内时使用默认值<b>7</b>。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].i32：当前Picker容器可见选项的数量，取值范围为[2, 9]内的整数。</li> </ul>

**起始版本：** 26.0.0

### NODE_PICKER_ITEM_HEIGHT

```c
NODE_PICKER_ITEM_HEIGHT = 1018005
```

**描述：**

设置Picker容器每个选项的高度，语义与ArkTS侧UIPickerComponent的itemHeight一致。 未设置时，每个选项高度为40vp。CAPI以vp为单位传入高度值。 支持属性设置，属性重置和属性获取接口。<br> **属性设置方法参数{@link ArkUI_AttributeItem}格式：**<br><ul><br><li>.value[0].f32：选项高度，单位为vp。有效范围为<b>[40, 64]</b>。小于40vp或大于64vp时使用默认值<b>40</b>vp。不支持百分比。</li><br></ul><br>**属性获取方法返回值{@link ArkUI_AttributeItem}格式：**<br><ul> <li>.value[0].f32：当前选项高度，单位为vp。</li> </ul>

**起始版本：** 26.0.0


