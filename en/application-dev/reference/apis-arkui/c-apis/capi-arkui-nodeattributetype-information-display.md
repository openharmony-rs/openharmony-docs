# Information Display

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_LOADING_PROGRESS_COLOR

```c
NODE_LOADING_PROGRESS_COLOR = MAX_NODE_SCOPE_NUM * ARKUI_NODE_LOADING_PROGRESS
```

**Description**

Defines the foreground color of the loading progress bar. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: foreground color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: foreground color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_LOADING_PROGRESS_ENABLE_LOADING

```c
NODE_LOADING_PROGRESS_ENABLE_LOADING
```

**Description**

Defines whether to show the loading animation for the <LoadingProgress> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to show the loading animation. The value <b>true</b> means to show the loading animation, and <b>false</b> means the opposite.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: The value <b>1</b> means to show the loading animation, and <b>0</b> means the opposite.</li> </ul>

**Since**: 12

### NODE_PROGRESS_VALUE

```c
NODE_PROGRESS_VALUE = MAX_NODE_SCOPE_NUM * ARKUI_NODE_PROGRESS
```

**Description**

Defines the current value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: current value of the progress indicator.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: current value of the progress indicator.</li> </ul>

**Since**: 12

### NODE_PROGRESS_TOTAL

```c
NODE_PROGRESS_TOTAL
```

**Description**

Defines the total value of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: total value of the progress indicator.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: total value of the progress indicator.</li> </ul>

**Since**: 12

### NODE_PROGRESS_COLOR

```c
NODE_PROGRESS_COLOR
```

**Description**

Defines the color for the progress value on the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: color value, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: color value, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_PROGRESS_TYPE

```c
NODE_PROGRESS_TYPE
```

**Description**

Defines the type of the progress indicator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: type of the progress indicator {@link ArkUI_ProgressType}. The default value is <b>ARKUI_PROGRESS_TYPE_LINEAR</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: type of the progress indicator {@link ArkUI_ProgressType}.</li> </ul>

**Since**: 12

### NODE_PROGRESS_LINEAR_STYLE

```c
NODE_PROGRESS_LINEAR_STYLE
```

**Description**

Sets the style of the linear progress indicator. This attribute can be set, reset, and obtained as required through APIs. If the progress indicator type is not linear, it will not take effect.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: Use the {@link ArkUI_ProgressLinearStyleOption} object to set the style.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: Use the {@link ArkUI_ProgressLinearStyleOption} object to get the style.</li> </ul>

**Since**: 15


