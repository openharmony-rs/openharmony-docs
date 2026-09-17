# Image

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_SRC

```c
NODE_IMAGE_SRC = MAX_NODE_SCOPE_NUM * ARKUI_NODE_IMAGE
```

**Description**

Defines the image source of the <Image> component. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**Since**: 12

### NODE_IMAGE_OBJECT_FIT

```c
NODE_IMAGE_OBJECT_FIT
```

**Description**

Defines how the image is resized to fit its container. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of<br>{@link ArkUI_ObjectFit}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: how the image is resized to fit its container. The value is an enum of<br>{@link ArkUI_ObjectFit}.</li> </ul>

**Since**: 12

### NODE_IMAGE_INTERPOLATION

```c
NODE_IMAGE_INTERPOLATION
```

**Description**

Defines the interpolation effect of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: interpolation effect of the image. The value is an enum of<br>{@link ArkUI_ImageInterpolation}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: interpolation effect of the image. The value is an enum of<br>{@link ArkUI_ImageInterpolation}.</li> </ul>

**Since**: 12

### NODE_IMAGE_OBJECT_REPEAT

```c
NODE_IMAGE_OBJECT_REPEAT
```

**Description**

Defines how the image is repeated. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: how the image is repeated. The value is an enum of {@link ArkUI_ImageRepeat}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: how the image is repeated. The value is an enum of {@link ArkUI_ImageRepeat}.</li> </ul>

**Since**: 12

### NODE_IMAGE_COLOR_FILTER

```c
NODE_IMAGE_COLOR_FILTER
```

**Description**

Defines the color filter of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32 to .value[19].f32: filter matrix array.</li><br><li>.size: 5 x 4 filter array size.</li><br><li>.object: the pointer to OH_Drawing_ColorFilter. Either .value or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32 to .value[19].f32: filter matrix array.</li> <li>.size: 5 x 4 filter array size.</li> <li>.object: the pointer to OH_Drawing_ColorFilter.</li> </ul>

**Since**: 12

### NODE_IMAGE_AUTO_RESIZE

```c
NODE_IMAGE_AUTO_RESIZE
```

**Description**

Defines the auto resize attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to resize the image source.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to resize the image source.</li> </ul>

**Since**: 12

### NODE_IMAGE_ALT

```c
NODE_IMAGE_ALT
```

**Description**

Defines the placeholder image source. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**Since**: 12

### NODE_IMAGE_DRAGGABLE

```c
NODE_IMAGE_DRAGGABLE
```

**Description**

Defines whether the image is draggable. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the image is draggable. The value <b>true</b> means that the image is draggable.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the image is draggable.</li> </ul>

**Since**: 12

### NODE_IMAGE_RENDER_MODE

```c
NODE_IMAGE_RENDER_MODE
```

**Description**

Defines the image rendering mode. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_ImageRenderMode}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: The parameter type is {@link ArkUI_ImageRenderMode}.</li> </ul>

**Since**: 12

### NODE_IMAGE_FIT_ORIGINAL_SIZE

```c
NODE_IMAGE_FIT_ORIGINAL_SIZE
```

**Description**

Defines whether the image display size follows the image source size. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to follow the image source size. The value <b>true</b> means to follow.</li> </ul>

**Since**: 12

### NODE_IMAGE_FILL_COLOR

```c
NODE_IMAGE_FILL_COLOR
```

**Description**

Defines the fill color of the image. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: fill color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: fill color, in 0xARGB format.</li> </ul>

**Since**: 12

### NODE_IMAGE_RESIZABLE

```c
NODE_IMAGE_RESIZABLE
```

**Description**

Defines how the image is resized when stretched using an array or a lattice object. The parameter types for setting and getting should be the same.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: width of the left edge, in vp.</li><br><li>.value[1].f32: width of the top edge, in vp.</li><br><li>.value[2].f32: width of the right edge, in vp.</li><br><li>.value[3].f32: width of the bottom edge, in vp.</li><br><li>.object: The parameter type is {@link OH_Drawing_Lattice}, supported since API version 24.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: width of the left edge, in vp.</li><br><li>.value[1].f32: width of the top edge, in vp.</li><br><li>.value[2].f32: width of the right edge, in vp.</li><br><li>.value[3].f32: width of the bottom edge, in vp.</li><br><li>.object: The parameter type is {@link OH_Drawing_Lattice}, supported since API version 24.</li> </ul>

**Since**: 12

### NODE_IMAGE_SYNC_LOAD

```c
NODE_IMAGE_SYNC_LOAD = 4012
```

**Description**

Defines the synchronous image loading attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to load the image synchronously.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to load the image synchronously.</li> </ul>

**Since**: 20

### NODE_IMAGE_SOURCE_SIZE

```c
NODE_IMAGE_SOURCE_SIZE = 4013
```

**Description**

Defines the image decoding size attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: width of the decoded image, in px.</li><br><li>.value[1].i32: height of the decoded image, in px.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: width of the decoded image, in px.</li><br><li>.value[1].i32: height of the decoded image, in px.</li> </ul>

**Since**: 21

### NODE_IMAGE_IMAGE_MATRIX

```c
NODE_IMAGE_IMAGE_MATRIX = 4014
```

**Description**

Support the implementation of affine image transformations using floating-point numbers. This attribute can be set, reset, and obtained as required through APIs. The parameter types for setting and getting should be the same.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0...15].f32: 16 floating-point numbers.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0...15].f32: 16 floating-point numbers.</li> </ul>

**Since**: 21

### NODE_IMAGE_MATCH_TEXT_DIRECTION

```c
NODE_IMAGE_MATCH_TEXT_DIRECTION = 4015
```

**Description**

Defines the image follow text direction attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether the image follows the text direction.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether the image follows the text direction.</li> </ul>

**Since**: 21

### NODE_IMAGE_COPY_OPTION

```c
NODE_IMAGE_COPY_OPTION = 4016
```

**Description**

Defines the image copy attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: copy option {@link ArkUI_CopyOptions}. The default value is<br><b>ARKUI_COPY_OPTIONS_NONE</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: copy option {@link ArkUI_CopyOptions}.</li> </ul>

**Since**: 21

### NODE_IMAGE_ENABLE_ANALYZER

```c
NODE_IMAGE_ENABLE_ANALYZER = 4017
```

**Description**

Defines the image AI analysis enable attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: whether to enable AI analysis for the image.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: whether to enable AI analysis for the image.</li> </ul>

**Since**: 21

### NODE_IMAGE_DYNAMIC_RANGE_MODE

```c
NODE_IMAGE_DYNAMIC_RANGE_MODE = 4018
```

**Description**

Defines the image dynamic display range attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: dynamic range mode {@link ArkUI_DynamicRangeMode}. The default value is<br><b>ARKUI_DYNAMIC_RANGE_MODE_STANDARD</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: dynamic range mode {@link ArkUI_DynamicRangeMode}.</li> </ul>

**Since**: 21

### NODE_IMAGE_HDR_BRIGHTNESS

```c
NODE_IMAGE_HDR_BRIGHTNESS = 4019
```

**Description**

Defines the image dynamic display brightness attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: HDR brightness. The value range is [0, 1].</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: HDR brightness. The value range is [0, 1].</li> </ul>

**Since**: 21

### NODE_IMAGE_ORIENTATION

```c
NODE_IMAGE_ORIENTATION = 4020
```

**Description**

Defines the image display direction attribute. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: orientation {@link ArkUI_Orientation}. The default value is <b>ARKUI_ORIENTATION_UP</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: orientation {@link ArkUI_Orientation}.</li> </ul>

**Since**: 21

### NODE_IMAGE_SUPPORT_SVG2

```c
NODE_IMAGE_SUPPORT_SVG2 = 4021
```

**Description**

Defines the range of SVG parsing capabilities supported through an enable switch. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: enable switch.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: enable switch.</li> </ul>

**Since**: 21

### NODE_IMAGE_CONTENT_TRANSITION

```c
NODE_IMAGE_CONTENT_TRANSITION = 4022
```

**Description**

Defines the animation effect for the image content transformation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.object: The parameter type is {@link ArkUI_ContentTransitionEffect}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.object: The parameter type is {@link ArkUI_ContentTransitionEffect}.</li> </ul>

**Since**: 21

### NODE_IMAGE_ALT_PLACEHOLDER

```c
NODE_IMAGE_ALT_PLACEHOLDER = 4023
```

**Description**

Defines the placeholder image during loading process. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**Since**: 22

### NODE_IMAGE_ALT_ERROR

```c
NODE_IMAGE_ALT_ERROR = 4024
```

**Description**

Defines the placeholder image when loading fails. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}. Either .string or .object must be set.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: placeholder image source.</li><br><li>.object: The parameter type is {@link ArkUI_DrawableDescriptor}.</li> </ul>

**Since**: 22

### NODE_IMAGE_ANTIALIASED

```c
NODE_IMAGE_ANTIALIASED = 4025
```

**Description**

Defines image edge anti-aliasing through an enable switch. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: enable switch. The default value is <b>false</b>.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].i32: enable switch.</li> </ul>

**Since**: 23


