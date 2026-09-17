# Background Display

## Overview

Defines the ArkUI style attributes that can be set on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_BACKGROUND_COLOR

```c
NODE_BACKGROUND_COLOR
```

**Description**

Defines the background color attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].u32: background color, in 0xARGB format. For example, 0xFFFF0000 indicates red.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_IMAGE

```c
NODE_BACKGROUND_IMAGE
```

**Description**

Defines the background image attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.string: image address. In API version 22 and earlier versions, the value can be a network image resource<br>address, local image resource address, Base64 image, or {@link PixelMap}, but cannot be an animated image such<br>as an [SVG](capi-native-node-h.md#arkui_nodeattributetype), GIF, or WebP image. In API version 23 and later versions, animated images of the WebP and GIF<br>types are supported. Only the first frame of the animated image is displayed. Other types of animated images are<br>not supported.</li><br><li>.value[0]?.i32: whether to repeat the image. Optional. The parameter type is {@link ArkUI_ImageRepeat}. The<br>default value is **ARKUI_IMAGE_REPEAT_NONE**.</li><br><li>.object: **PixelMap** object. The parameter type is {@link ArkUI_DrawableDescriptor}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.string: image address. In API version 22 and earlier versions, the value can be network image resource<br>addresses, local image resource addresses, Base64 strings, or PixelMap resources, but cannot be addresses of SVG<br>images, or animated images such as GIF and WebP. In API version 23 and later versions, animated images of the<br>WebP and GIF types are supported. Only the first frame of the animated image is displayed. Other types of<br>animated images are not supported.</li><br><li>.value[0].i32: whether to repeat the image. The parameter type is {@link ArkUI_ImageRepeat}.</li><br><li>.object: **PixelMap** object. The parameter type is {@link ArkUI_DrawableDescriptor}. <br>Either **.object** or **.string** must be set.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_IMAGE_SIZE

```c
NODE_BACKGROUND_IMAGE_SIZE
```

**Description**

Defines the background image size attribute, which can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: width of the image. The value range is [0, +∞), and the unit is vp.</li><br><li>.value[1].f32: height of the image. The value range is [0, +∞), and the unit is vp.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: width of the image, in vp.</li><br><li>.value[1].f32: height of the image, in vp.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE

```c
NODE_BACKGROUND_IMAGE_SIZE_WITH_STYLE
```

**Description**

Defines the background image size with style. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: size of the background image. The value is an enumerated value of {@link ArkUI_ImageSize}.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: size of the background image. The value is an enumerated value of {@link ArkUI_ImageSize}.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_BLUR_STYLE

```c
NODE_BACKGROUND_BLUR_STYLE
```

**Description**

Defines the background blur attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].i32: blue type. The value is an enum of {@link ArkUI_BlurStyle}.</li><br><li>.value[1]?.i32: color mode. The value is an enum of {@link ArkUI_ColorMode}.</li><br><li>.value[2]?.i32: adaptive color mode. The value is an enum of {@link ArkUI_AdaptiveColor}.</li><br><li>.value[3]?.f32: blur degree. The value range is [0.0, 1.0].</li><br><li>.value[4]?.f32: start boundary of grayscale blur.</li><br><li>.value[5]?.f32: end boundary of grayscale blur.</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].i32: blue type. The value is an enum of {@link ArkUI_BlurStyle}.</li><br><li>.value[1].i32: color mode. The value is an enum of {@link ArkUI_ColorMode}.</li><br><li>.value[2].i32: adaptive color mode. The value is an enum of {@link ArkUI_AdaptiveColor}.</li> <li>.value[3].f32: blur degree. The value range is [0.0, 1.0].</li><br><li>.value[4].f32: start boundary of grayscale blur.</li><br><li>.value[5].f32: end boundary of grayscale blur.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_IMAGE_POSITION

```c
NODE_BACKGROUND_IMAGE_POSITION
```

**Description**

Defines the position of the background image in the component, that is, the coordinates relative to the upper left corner of the component. This attribute can be set, reset, and obtained as required through APIs. **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: position along the x-axis, in px.</li><br><li>.value[1].f32: position along the y-axis, in px.</li><br><li>.value[2].?i32: alignment mode. The parameter type is {@link ArkUI_Alignment}. The default value is **<br>ARKUI_ALIGNMENT_TOP_START**.</li><br><li>.value[3].?i32: layout direction. The parameter type is {@link ArkUI_Direction}. The default value is **<br>ARKUI_DIRECTION_AUTO**.<br><br>In most scenarios, this parameter should be set to **AUTO**, which allows the system to automatically handle<br>the layout direction. If specific directions need to be maintained in certain scenarios, set this parameter to **<br>LTR** (left-to-right) or **RTL** (right-to-left).</li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul><br><li>.value[0].f32: position along the x-axis, in px.</li><br><li>.value[1].f32: position along the y-axis, in px.</li><br><li>.value[2].i32: alignment mode. The parameter type is {@link ArkUI_Alignment}. The default value is **<br>ARKUI_ALIGNMENT_TOP_START**.</li><br><li>.value[3].i32: layout direction. The parameter type is {@link ArkUI_Direction}. The default value is **<br>ARKUI_DIRECTION_AUTO**.</li> </ul>

**Since**: 12

### NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE

```c
NODE_BACKGROUND_IMAGE_RESIZABLE_WITH_SLICE = 100
```

**Description**

Defines the background image resizable attribute, which can be set, reset, and obtained as required through APIs.<br> **Format of the {@link ArkUI_AttributeItem} parameter for setting the attribute:**<br><ul><br><li>.value[0].f32: width of the left edge. The unit is vp. </li><br><li>.value[1].f32: width of the top edge. The unit is vp. </li><br><li>.value[2].f32: width of the right edge. The unit is vp. </li><br><li>.value[3].f32: width of the bottom edge. The unit is vp.<br></li><br></ul><br>**Format of the return value {@link ArkUI_AttributeItem}:**<br><ul> <li>.value[0].f32: width of the left edge. The unit is vp. </li><br><li>.value[1].f32: width of the top edge. The unit is vp. </li><br><li>.value[2].f32: width of the right edge. The unit is vp. </li><br><li>.value[3].f32: width of the bottom edge. The unit is vp. </li> </ul>

**Since**: 19


