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

设置帧动画组件的图片帧信息集合。不支持动态更新。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.size: 图片数量。</li> <li>.object: 图片数组。数组元素类型为[ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.size: 图片数量。</li> <li>.object: 图片数组。数组元素类型为[ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_STATE

```c
NODE_IMAGE_ANIMATOR_STATE = 19001
```

**描述：**

设置帧动画组件的播放状态。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画播放状态。参数类型为 [ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus)。默认值为<b>ARKUI_ANIMATION_STATUS_INITIAL</b>。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画播放状态。参数类型为[ArkUI_AnimationStatus](capi-native-type-h.md#arkui_animationstatus)。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_DURATION

```c
NODE_IMAGE_ANIMATOR_DURATION = 19002
```

**描述：**

设置帧动画组件的播放时长。当设置duration为0时，表示不播放图片。属性变化只在下一帧动画开始时生效。 如果images中单独设置了duration属性，则此属性设置无效。支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 播放时长，单位ms。默认值为1000。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 播放时长，单位ms。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_REVERSE

```c
NODE_IMAGE_ANIMATOR_REVERSE = 19003
```

**描述：**

设置帧动画组件的播放方向。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 播放方向。<b>0</b>表示从首帧到尾帧播放，<b>1</b>表示从尾帧到首帧播放。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 播放方向。<b>0</b>表示从首帧到尾帧播放，<b>1</b>表示从尾帧到首帧播放。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_FIXED_SIZE

```c
NODE_IMAGE_ANIMATOR_FIXED_SIZE = 19004
```

**描述：**

设置图片大小是否与组件大小一致。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 图片大小是否与组件大小一致。<b>1</b>表示图片大小与组件大小一致， 此时图片的width、height、top、left属性设置无效。<b>0</b>表示自定义图片大小， 需分别设置每张图片的width、height、top、left属性。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 图片大小是否与组件大小一致。<b>1</b>表示图片大小与组件大小一致， <b>0</b>表示自定义图片大小。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_FILL_MODE

```c
NODE_IMAGE_ANIMATOR_FILL_MODE = 19005
```

**描述：**

设置动画执行前后在当前播放方向上的状态。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画执行前后在当前播放方向上的状态。 参数类型为[ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode)。默认值为 <b>ARKUI_ANIMATION_FILL_MODE_FORWARDS</b>。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画执行前后在当前播放方向上的状态。参数类型为[ArkUI_AnimationFillMode](capi-native-type-h.md#arkui_animationfillmode)。</li> </ul>

**起始版本：** 12

### NODE_IMAGE_ANIMATOR_ITERATION

```c
NODE_IMAGE_ANIMATOR_ITERATION = 19006
```

**描述：**

设置动画播放次数。 支持属性设置，属性重置和属性获取接口。<br> 属性设置方法参数[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画播放次数。</li> </ul><br> 属性获取方法返回值[ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md)格式： <ul> <li>.value[0].i32: 动画播放次数。</li> </ul>

**起始版本：** 12


