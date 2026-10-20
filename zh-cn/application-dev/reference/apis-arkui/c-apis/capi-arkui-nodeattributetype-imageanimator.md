# 图片帧动画

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_IMAGE_ANIMATOR_IMAGES

```c
NODE_IMAGE_ANIMATOR_IMAGES = ARKUI_NODE_IMAGE_ANIMATOR * MAX_NODE_SCOPE_NUM
```

**描述：**

Defines the image frames for the image animator. Dynamic updates are not supported. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.size: number of images.</li> <li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.size: number of images.</li> <li>.object: array of images. The array element type is [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md).</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_STATE

```c
NODE_IMAGE_ANIMATOR_STATE = 19001
```

**描述：**

Defines the playback status of the animation for the image animator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback status of the animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus). The default value is <b>ARKUI_ANIMATION_STATUS_INITIAL</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback status of the animation. The parameter type is [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus).</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_DURATION

```c
NODE_IMAGE_ANIMATOR_DURATION = 19002
```

**描述：**

Defines the playback duration for the image animator. When the duration is 0, no image is played. The value change takes effect only at the beginning of the next cycle. When a separate duration is set in images, the setting of this attribute is invalid. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback duration, in ms. The default value is 1000.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback duration, in ms.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_REVERSE

```c
NODE_IMAGE_ANIMATOR_REVERSE = 19003
```

**描述：**

Defines the playback direction for the image animator. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: playback direction. <b>0</b> indicates that images are played from the first one to the last one, and <b>1</b> indicates that images are played from the last one to the first one.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: playback direction. <b>0</b> indicates that images are played from the first one to the last one, and <b>1</b> indicates that images are played from the last one to the first one.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_FIXED_SIZE

```c
NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004
```

**描述：**

Defines whether the image size is the same as the component size. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: whether the image size is the same as the component size. <b>1</b> indicates that the image size is the same as the component size. In this case, the width, height, top, and left attributes of the image are invalid. <b>0</b> indicates that the image size is customized. The width, height, top, and left attributes of each image must be set separately.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: whether the image size is the same as the component size. <b>1</b> indicates that the image size is the same as the component size. <b>0</b> indicates that the image size is customized.</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_FILL_MODE

```c
NODE_IMAGE_ANIMATOR_FILL_MODE = 19005
```

**描述：**

Defines the status before and after execution of the animation in the current playback direction. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: status before and after execution of the animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode). The default value is <b>ARKUI_ANIMATION_FILL_MODE_FORWARDS</b>.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: status before and after execution of the animation in the current playback direction. The parameter type is [ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode).</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_ITERATION

```c
NODE_IMAGE_ANIMATOR_ITERATION = 19006
```

**描述：**

Defines the number of times that the animation is played. This attribute can be set, reset, and obtained as required through APIs.<br> **Format of the [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) parameter for setting the attribute:**<br><ul> <li>.value[0].i32: number of times that the animation is played.</li> </ul><br> **Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md):**<br><ul> <li>.value[0].i32: number of times that the animation is played.</li> </ul>

**起始版本：** 12


