# 动效属性

## 概述

定义ArkUI在Native侧可以设置的属性样式集合。

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**所在头文件：** [native_node.h](capi-native-node-h.md)

### NODE_OPACITY_TRANSITION

```c
NODE_OPACITY_TRANSITION
```

**描述：**

转场时的透明度效果属性，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：表示转场结束时（即终点）的透明度值，转场将从当前透明度过渡到该值。</li><br><li>.value[1].i32：表示动画时长，单位ms，取值需大于0。</li><br><li>.value[2].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[3]?.i32：表示动画延迟时长，单位ms。不传入时默认值为0（无延迟），当需要在动画开始前等待一段时间时传入此参数。</li><br><li>.value[4]?.i32：表示动画播放次数。不传入时默认值为1（单次播放），当需要动画重复播放时传入此参数。</li><br><li>.value[5]?.i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。默认值为ARKUI_ANIMATION_PLAY_MODE_NORMAL，当需要反向播放、循环播放等特殊播放模式时传入此参数。</li><br><li>.value[6]?.f32：表示动画播放速度。不传入时默认值为1.0（正常速度），当需要加速或减速播放动画时传入此参数，大于1.0为加速，小于1.0为减速。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：表示起始和终点的透明度值，取值范围[0, 1]。超出范围时自动修正为边界值。</li><br><li>.value[1].i32：表示动画时长，单位ms。</li><br><li>.value[2].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[3].i32：表示动画延迟时长，单位ms。</li><br><li>.value[4].i32：表示动画播放次数。</li><br><li>.value[5].i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。</li> <li>.value[6].f32：表示动画播放速度。</li> </ul>

**起始版本：** 12

### NODE_ROTATE_TRANSITION

```c
NODE_ROTATE_TRANSITION
```

**描述：**

转场时的旋转效果属性，仅在组件插入和删除时生效。支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：表示横向旋转分量。</li><br><li>.value[1].f32：表示纵向的旋转分量。</li><br><li>.value[2].f32：表示竖向的旋转分量。</li><br><li>.value[3].f32：表示角度，单位为度（°）。</li><br><li>.value[4].f32：表示视距，即视点到z=0平面的距离，取值范围[0, +∞)，传入负值时按0处理。单位vp，默认值0.0。</li><br><li>.value[5].i32：表示动画时长，单位ms。</li><br><li>.value[6].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[7]?.i32：表示动画延迟时长，单位ms。不传入时默认值为0（无延迟），当需要在动画开始前等待一段时间时传入此参数。</li><br><li>.value[8]?.i32：表示动画播放次数。</li><br><li>.value[9]?.i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。默认值为ARKUI_ANIMATION_PLAY_MODE_NORMAL。</li><br><li>.value[10]?.f32：表示动画播放速度。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：表示横向旋转分量。</li><br><li>.value[1].f32：表示纵向的旋转分量。</li><br><li>.value[2].f32：表示竖向的旋转分量。</li><br><li>.value[3].f32：表示角度，单位为度（°）。</li><br><li>.value[4].f32：表示视距，单位为vp。</li><br><li>.value[5].i32：表示动画时长，单位ms。</li><br><li>.value[6].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[7].i32：表示动画延迟时长，单位ms。</li><br><li>.value[8].i32：表示动画播放次数。</li><br><li>.value[9].i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。</li> <li>.value[10].f32：表示动画播放速度。</li> </ul>

**起始版本：** 12

### NODE_SCALE_TRANSITION

```c
NODE_SCALE_TRANSITION
```

**描述：**

转场时的缩放效果属性，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：横向放大倍数，默认值1.0。</li><br><li>.value[1].f32：纵向放大倍数，默认值1.0。</li><br><li>.value[2].f32：竖向放大倍数，默认值1.0。</li><br><li>.value[3].i32：表示动画时长，单位ms。</li><br><li>.value[4].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[5]?.i32：表示动画延迟时长，单位ms。不传入时默认值为0（无延迟），当需要在动画开始前等待一段时间时传入此参数。</li><br><li>.value[6]?.i32：表示动画播放次数。</li><br><li>.value[7]?.i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。默认值为ARKUI_ANIMATION_PLAY_MODE_NORMAL。</li><br><li>.value[8]?.f32：表示动画播放速度。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：横向放大倍数。</li><br><li>.value[1].f32：纵向放大倍数。</li><br><li>.value[2].f32：竖向放大倍数。</li><br><li>.value[3].i32：表示动画时长，单位ms。</li><br><li>.value[4].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[5].i32：表示动画延迟时长，单位ms。</li><br><li>.value[6].i32：表示动画播放次数。</li><br><li>.value[7].i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。</li> <li>.value[8].f32：表示动画播放速度。</li> </ul>

**起始版本：** 12

### NODE_TRANSLATE_TRANSITION

```c
NODE_TRANSLATE_TRANSITION
```

**描述：**

转场时的平移效果属性，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].f32：表示横向平移距离值，单位为vp。默认值为0.0vp。</li><br><li>.value[1].f32：表示纵向平移距离值，单位为vp。默认值为0.0vp。</li><br><li>.value[2].f32：表示竖向平移距离值，单位为vp。默认值为0.0vp。</li><br><li>.value[3].i32：表示动画时长，单位ms。</li><br><li>.value[4].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[5]?.i32：表示动画延迟时长，单位ms。不传入时默认值为0（无延迟），当需要在动画开始前等待一段时间时传入此参数。</li><br><li>.value[6]?.i32：表示动画播放次数。</li><br><li>.value[7]?.i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。默认值为ARKUI_ANIMATION_PLAY_MODE_NORMAL。</li><br><li>.value[8]?.f32：表示动画播放速度。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].f32：表示横向平移距离值，单位为vp。</li><br><li>.value[1].f32：表示纵向平移距离值，单位为vp。</li><br><li>.value[2].f32：表示竖向平移距离值，单位为vp。</li><br><li>.value[3].i32：表示动画时长，单位ms。</li><br><li>.value[4].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[5].i32：表示动画延迟时长，单位ms。</li><br><li>.value[6].i32：表示动画播放次数。</li><br><li>.value[7].i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。</li> <li>.value[8].f32：表示动画播放速度。</li> </ul>

**起始版本：** 12

### NODE_MOVE_TRANSITION

```c
NODE_MOVE_TRANSITION
```

**描述：**

转场时从屏幕边缘滑入和滑出的效果属性，支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.value[0].i32：转场时组件滑入滑出的方向，参数类型{@link ArkUI_TransitionEdge}，不同枚举值决定组件从屏幕的哪个边缘滑入和滑出。</li><br><li>.value[1].i32：表示动画时长，单位ms。</li><br><li>.value[2].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[3]?.i32：表示动画延迟时长，单位ms。不传入时默认值为0（无延迟），当需要在动画开始前等待一段时间时传入此参数。</li><br><li>.value[4]?.i32：表示动画播放次数。</li><br><li>.value[5]?.i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。默认值为ARKUI_ANIMATION_PLAY_MODE_NORMAL。</li><br><li>.value[6]?.f32：表示动画播放速度。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：参数类型{@link ArkUI_TransitionEdge}。</li><br><li>.value[1].i32：表示动画时长，单位ms。</li><br><li>.value[2].i32：表示动画曲线类型，取{@link ArkUI_AnimationCurve}枚举值。</li><br><li>.value[3].i32：表示动画延迟时长，单位ms。</li><br><li>.value[4].i32：表示动画播放次数。</li><br><li>.value[5].i32：表示动画播放模式，取{@link ArkUI_AnimationPlayMode}枚举值。</li> <li>.value[6].f32：表示动画播放速度。</li> </ul>

**起始版本：** 12

### NODE_GEOMETRY_TRANSITION

```c
NODE_GEOMETRY_TRANSITION
```

**描述：**

组件内隐式共享元素转场（转场在组件插入和删除时自动触发），支持属性设置，属性重置，属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。 **参数：**<br><ul> <li>.value[0]?.i32：参数类型为1或者0。共享元素绑定的2个组件，针对出场元素未进行删除时是否要继续参与共享元素动画，默认为false，不参与保持原始位置不动。</li><br><li>.string：用于设置绑定关系，id置""清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定，且两个组件必须分别为in和out两种不同类型的角色，不能多个组件绑定同一个id。</li><br></ul><br>**返回：**<br><ul><br><li>.value[0].i32：取值为1或0。</li> <li>.string：用于设置绑定关系，id置""清除绑定关系避免参与共享行为，id可更换重新建立绑定关系。同一个id只能有两个组件绑定，且两个组件必须分别扮演进入(in)和退出(out)两种不同角色，不能多个组件绑定同一个id。</li> </ul>

**起始版本：** 12

### NODE_TRANSITION

```c
NODE_TRANSITION = 94
```

**描述：**

定义组件插入和删除时显示过渡动效，支持属性设置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.object：组件插入和删除时的过渡动效配置，参数类型为{@link ArkUI_TransitionEffect}。</li><br></ul><br>**返回：**<br><ul><br><li>.object：表示组件插入和删除时的过渡动效配置，参数类型为{@link ArkUI_TransitionEffect}。</li> </ul>

**起始版本：** 12

### NODE_MOTION_PATH

```c
NODE_MOTION_PATH = 111
```

**描述：**

设置组件的运动路径属性，支持属性设置，属性重置和属性获取接口。 <br>作为属性设置方法参数、属性获取方法返回值{@link ArkUI_AttributeItem}格式如下。<br>**参数：**<br><ul><br><li>.object：指向路径动画的运动路径配置项的指针；参数类型为{@link ArkUI_MotionPathOptions}。</li><br></ul><br>**返回：**<br><ul><br><li>.object：指向路径动画的运动路径配置项的指针；参数类型为{@link ArkUI_MotionPathOptions}。</li> </ul>

**起始版本：** 23


