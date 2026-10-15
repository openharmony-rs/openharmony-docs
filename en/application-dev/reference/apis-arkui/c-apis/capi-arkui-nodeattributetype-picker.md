# Picker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_PICKER_OPTION_SELECTED_INDEX

```c
NODE_PICKER_OPTION_SELECTED_INDEX = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PICKER
```

**Description**

Defines the index of the default selected item in the data selection range of the picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].u32: index.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].u32: index.</li> </ul>

**Since**: 23

### NODE_PICKER_ENABLE_HAPTIC_FEEDBACK

```c
NODE_PICKER_ENABLE_HAPTIC_FEEDBACK = 1018001
```

**Description**

Defines whether to enable haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to enable haptic feedback. <b>1</b> indicates to enable, and <b>0</b> indicates opposite. Default value: <b>1</b>. When enabled, whether haptic feedback exists depends on the hardware support of the system.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether haptic feedback is enabled. <b>1</b> indicates enabled, and <b>0</b> indicates the opposite. Whether haptic feedback exists depends on the hardware support of the system.</li> </ul>

**Since**: 23

### NODE_PICKER_CAN_LOOP

```c
NODE_PICKER_CAN_LOOP = 1018002
```

**Description**

Whether the picker supports looping. This attribute can be set, reset, and obtained as required through APIs.<br> Use scenario: Looping is suitable for scenarios with limited options where a quick selection experience is desired (such as gender selection). Non-looping is suitable for scenarios where options have clear boundaries and the user selection range needs to be restricted.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the picker supports looping. <b>1</b> to support; <b>0</b> otherwise. The default value is <b>1</b>.<br> If the number of child components is less than 8, looping will not occur regardless of whether the value is <b>1</b> or <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the picker supports looping. <b>1</b> indicates that scrolling is supported; <b>0</b> indicates that scrolling is not supported.</li> </ul>

**Since**: 23

### NODE_PICKER_SELECTION_INDICATOR

```c
NODE_PICKER_SELECTION_INDICATOR = 1018003
```

**Description**

Picker indicator style. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.object: picker indicator style. The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md). Default value:<br> {<br> type: PickerIndicatorType.BACKGROUND,<br> borderRadius: {<br> value:12,<br> unit:LengthUnit.vp<br> },<br> backgroundColor: 'sys.color.comp_background_tertiary'<br> }<br> When not set, the default value is used.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.object: picker indicator style. The parameter type is [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).</li> </ul>

**Since**: 23


