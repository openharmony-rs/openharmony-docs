# Picker

## Overview

Defines the ArkUI style attributes that can be set on the native side.

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

Defines whether haptic feedback. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to feedback. The value <b>true</b> means to feedback, and <b>false</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>value[0].i32: whether to feedback.</li> </ul>

**Since**: 23

### NODE_PICKER_CAN_LOOP

```c
NODE_PICKER_CAN_LOOP = 1018002
```

**Description**

Defines whether to support scroll looping for the picker. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether to support scroll looping. The value <b>true</b> means to support scroll looping, and <b>false</b> means the opposite.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>value[0].i32: The value <b>1</b> means to support scroll looping, and <b>0</b> means the opposite.</li> </ul>

**Since**: 23

### NODE_PICKER_SELECTION_INDICATOR

```c
NODE_PICKER_SELECTION_INDICATOR = 1018003
```

**Description**

Sets the type and parameters of the selection indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Attribute setting method parameter [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) Format:**<br><ul> <li>.object: Parameter type [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).</li> </ul><br> **Attribute fetch method return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) format:**<br><ul> <li>.object: Parameter type [ArkUI_PickerIndicatorStyle](capi-arkui-nativemodule-arkui-pickerindicatorstyle.md).</li> </ul>

**Since**: 23


