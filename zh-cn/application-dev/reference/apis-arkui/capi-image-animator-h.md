# image_animator.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liyujie43-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

## 概述

为NativeNode API提供ImageAnimator节点类型定义。

**引用文件：** <arkui/image_animator.h>

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**相关示例：** <!--RP1-->[native_type_sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/ArkUISample/NativeType/native_type_sample)<!--RP1End-->

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md) | ArkUI_ImageAnimatorFrameInfo | 定义图片动画帧信息。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_AnimationStatus](#arkui_animationstatus) | ArkUI_AnimationStatus | 定义帧动画的播放状态。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)](#oh_arkui_imageanimatorframeinfo_createfromstring) | 使用图片路径创建帧图片信息，图片格式为svg、png和jpg。支持应用沙箱内的相对路径和绝对路径。 |
| [ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)](#oh_arkui_imageanimatorframeinfo_createfromdrawabledescriptor) | 使用DrawableDescriptor对象创建帧图片信息，图片格式为Resource和PixelMap。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_dispose) | 销毁帧图片对象指针。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)](#oh_arkui_imageanimatorframeinfo_setwidth) | 设置图片宽度。 |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getwidth) | 获取图片宽度。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)](#oh_arkui_imageanimatorframeinfo_setheight) | 设置图片高度。 |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getheight) | 获取图片高度。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)](#oh_arkui_imageanimatorframeinfo_settop) | 设置图片相对于组件左上角的纵向坐标。 |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_gettop) | 获取图片相对于组件左上角的纵向坐标。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)](#oh_arkui_imageanimatorframeinfo_setleft) | 设置图片相对于组件左上角的横向坐标。 |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getleft) | 获取图片相对于组件左上角的横向坐标。 |
| [void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)](#oh_arkui_imageanimatorframeinfo_setduration) | 设置图片的播放时长。 |
| [int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)](#oh_arkui_imageanimatorframeinfo_getduration) | 获取图片的播放时长。 |

## 枚举类型说明

### ArkUI_AnimationStatus

```c
enum ArkUI_AnimationStatus
```

**描述**

定义帧动画的播放状态。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ARKUI_ANIMATION_STATUS_INITIAL = 0 | 动画初始状态。 |
| ARKUI_ANIMATION_STATUS_RUNNING = 1 | 动画处于播放状态。 |
| ARKUI_ANIMATION_STATUS_PAUSED = 2 | 动画处于暂停状态。 |
| ARKUI_ANIMATION_STATUS_STOPPED = 3 | 动画处于停止状态。 |

## 函数说明

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromString(char* src)
```

**描述**

使用图片路径创建帧图片信息，图片格式为svg、png和jpg。支持应用沙箱内的相对路径和绝对路径。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* src | 图片路径，支持应用沙箱内的相对路径或绝对路径。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | 帧图片对象指针。 |

### OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor()

```c
ArkUI_ImageAnimatorFrameInfo* OH_ArkUI_ImageAnimatorFrameInfo_CreateFromDrawableDescriptor(ArkUI_DrawableDescriptor* drawable)
```

**描述**

使用[ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)对象创建帧图片信息，图片格式为Resource和PixelMap。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_DrawableDescriptor](capi-arkui-nativemodule-arkui-drawabledescriptor.md)* drawable | 使用Resource或PixelMap创建的ArkUI_DrawableDescriptor对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* | 帧图片对象指针。 |

### OH_ArkUI_ImageAnimatorFrameInfo_Dispose()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_Dispose(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

销毁帧图片对象指针。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

### OH_ArkUI_ImageAnimatorFrameInfo_SetWidth()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t width)
```

**描述**

设置图片宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |
| int32_t width | 图片宽度，单位为px。 |

### OH_ArkUI_ImageAnimatorFrameInfo_GetWidth()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetWidth(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

获取图片宽度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 图片宽度，单位为px，imageInfo为空指针时返回0。 |

### OH_ArkUI_ImageAnimatorFrameInfo_SetHeight()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t height)
```

**描述**

设置图片高度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |
| int32_t height | 图片高度，单位为px。 |

### OH_ArkUI_ImageAnimatorFrameInfo_GetHeight()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetHeight(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

获取图片高度。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 图片高度，单位为px，imageInfo为空指针时返回0。 |

### OH_ArkUI_ImageAnimatorFrameInfo_SetTop()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t top)
```

**描述**

设置图片相对于组件左上角的纵向坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |
| int32_t top | 图片相对于组件左上角的纵向坐标，单位为px。 |

### OH_ArkUI_ImageAnimatorFrameInfo_GetTop()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetTop(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

获取图片相对于组件左上角的纵向坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 图片相对于组件左上角的纵向坐标，单位为px，imageInfo为空指针时返回0。 |

### OH_ArkUI_ImageAnimatorFrameInfo_SetLeft()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t left)
```

**描述**

设置图片相对于组件左上角的横向坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |
| int32_t left | 图片相对于组件左上角的横向坐标，单位为px。 |

### OH_ArkUI_ImageAnimatorFrameInfo_GetLeft()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetLeft(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

获取图片相对于组件左上角的横向坐标。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 图片相对于组件左上角的横向坐标，单位为px，imageInfo为空指针时返回0。 |

### OH_ArkUI_ImageAnimatorFrameInfo_SetDuration()

```c
void OH_ArkUI_ImageAnimatorFrameInfo_SetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo, int32_t duration)
```

**描述**

设置图片的播放时长。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |
| int32_t duration | 图片的播放时长，单位为ms。 |

### OH_ArkUI_ImageAnimatorFrameInfo_GetDuration()

```c
int32_t OH_ArkUI_ImageAnimatorFrameInfo_GetDuration(ArkUI_ImageAnimatorFrameInfo* imageInfo)
```

**描述**

获取图片的播放时长。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [ArkUI_ImageAnimatorFrameInfo](capi-arkui-nativemodule-arkui-imageanimatorframeinfo.md)* imageInfo | 帧图片对象指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | 图片的播放时长，单位为毫秒，imageInfo为空指针时返回0。 |
