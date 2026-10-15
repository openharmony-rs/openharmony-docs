# ImageAnimator

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_ANIMATOR_IMAGES

```c
NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM
```

**Description**

Defines the image frames for the image animator. Dynamic updates are not supported. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.size: number of images.</li> <li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.size: number of images.</li> <li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_STATE

```c
NODE_IMAGE_ANIMATOR_STATE = 19001
```

**Description**

Playback status of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback status of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-image-animator-h.md#arkui_animationstatus). The default state is initial.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback status of the frame-by-frame animation. The parameter type is [ArkUI_AnimationStatus](capi-image-animator-h.md#arkui_animationstatus).</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_DURATION

```c
NODE_IMAGE_ANIMATOR_DURATION = 19002
```

**Description**

Playback duration of the frame-by-frame animation. This attribute does not take effect when a separate duration is set for any of the image frames. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback duration, in milliseconds. The default value is <b>1000</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback duration, in milliseconds. The default value is <b>1000</b>.</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_REVERSE

```c
NODE_IMAGE_ANIMATOR_REVERSE = 19003
```

**Description**

Playback direction of the frame-by-frame animation. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback direction. The value <b>0</b> indicates that images are played from the first one to the last one, and <b>1</b> indicates that images are played from the last one to the first one. The default value is <b>0</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback direction. The value <b>0</b> indicates that images are played from the first one to the last one, and <b>1</b> indicates that images are played from the last one to the first one.</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_FIXED_SIZE

```c
NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004
```

**Description**

Whether the image size is fixed at the component size. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the image size is fixed at the component size. The value <b>1</b> indicates that the image size is fixed at the component size. The value <b>0</b> indicates that the <b>width</b>, <b>height</b>, <b>top</b>, and <b>left</b> attributes of each image must be set separately. The default value is <b>1</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the image size is fixed at the component size. The value <b>1</b> indicates that the image size is fixed at the component size. The value <b>0</b> indicates that the <b>width</b>, <b>height</b>, <b>top</b>, and <b>left</b> attributes of each image must be set separately.</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_FILL_MODE

```c
NODE_IMAGE_ANIMATOR_FILL_MODE = 19005
```

**Description**

Status before and after execution of the frame-by-frame animation in the current playback direction. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-visual-h.md#arkui_animationfillmode). The default value is <b>ARKUI_ANIMATION_FILL_MODE_FORWARDS</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: status before and after execution of the frame-by-frame animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-visual-h.md#arkui_animationfillmode).</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_ITERATION

```c
NODE_IMAGE_ANIMATOR_ITERATION = 19006
```

**Description**

Number of times that the frame-by-frame animation is played. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of times that the animation is played.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of times that the animation is played.</li> </ul>

**Since**: 12

### NODE_IMAGE_ANIMATOR_INTERPOLATION

```c
NODE_IMAGE_ANIMATOR_INTERPOLATION = 19007
```

**Description**

Defines the interpolation effect of the frame images, which mitigates aliasing during image scaling. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: interpolation effect of the frame images. The parameter type is [ArkUI_ImageInterpolation](capi-image-h.md#arkui_imageinterpolation). The default value is <b>ARKUI_IMAGE_INTERPOLATION_LOW</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: interpolation effect of the frame images. The parameter type is [ArkUI_ImageInterpolation](capi-image-h.md#arkui_imageinterpolation).</li> </ul>

**Since**: 26.0.1


