# oh_display_manager.h
<!--Kit: ArkUI-->
<!--Subsystem: Window-->
<!--Owner: @oh_wangxk; @logn-->
<!--Designer: @hejunfei1991-->
<!--Tester: @qinliwen0417-->
<!--Adviser: @ge-yafang-->

## 概述

提供屏幕管理的一些基础能力，包括获取默认显示设备的信息，以及监听显示设备的旋转、折叠、展开等状态变化的能力。

**引用文件：** <window_manager/oh_display_manager.h>

**库：** libnative_display_manager.so.

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

**相关模块：** [OH_DisplayManager](capi-oh-displaymanager.md)

## 汇总

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayId(uint64_t *displayId)](#oh_nativedisplaymanager_getdefaultdisplayid) | - | 获取默认屏幕的id号。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayWidth(int32_t *displayWidth)](#oh_nativedisplaymanager_getdefaultdisplaywidth) | - | 获取默认屏幕的宽度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayHeight(int32_t *displayHeight)](#oh_nativedisplaymanager_getdefaultdisplayheight) | - | 获取默认屏幕的高度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayRotation(NativeDisplayManager_Rotation *displayRotation)](#oh_nativedisplaymanager_getdefaultdisplayrotation) | - | 获取默认屏幕的顺时针旋转角度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayOrientation(NativeDisplayManager_Orientation *displayOrientation)](#oh_nativedisplaymanager_getdefaultdisplayorientation) | - | 获取默认屏幕的旋转方向。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayVirtualPixelRatio(float *virtualPixels)](#oh_nativedisplaymanager_getdefaultdisplayvirtualpixelratio) | - | 获取默认屏幕的虚拟像素密度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayRefreshRate(uint32_t *refreshRate)](#oh_nativedisplaymanager_getdefaultdisplayrefreshrate) | - | 获取默认屏幕的刷新率。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityDpi(int32_t *densityDpi)](#oh_nativedisplaymanager_getdefaultdisplaydensitydpi) | - | 获取屏幕的物理像素密度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityPixels(float *densityPixels)](#oh_nativedisplaymanager_getdefaultdisplaydensitypixels) | - | 获取屏幕逻辑像素的密度。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayScaledDensity(float *scaledDensity)](#oh_nativedisplaymanager_getdefaultdisplayscaleddensity) | - | 获取屏幕显示字体的缩放因子。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityXdpi(float *xDpi)](#oh_nativedisplaymanager_getdefaultdisplaydensityxdpi) | - | 获取屏幕X方向中每英寸屏幕的物理像素值。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityYdpi(float *yDpi)](#oh_nativedisplaymanager_getdefaultdisplaydensityydpi) | - | 获取Y方向中每英寸屏幕的物理像素值。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo **cutoutInfo)](#oh_nativedisplaymanager_createdefaultdisplaycutoutinfo) | - | 获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_DestroyDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo *cutoutInfo)](#oh_nativedisplaymanager_destroydefaultdisplaycutoutinfo) | - | 销毁挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。 |
| [bool OH_NativeDisplayManager_IsFoldable()](#oh_nativedisplaymanager_isfoldable) | - | 查询设备是否可折叠。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetFoldDisplayMode(NativeDisplayManager_FoldDisplayMode *displayMode)](#oh_nativedisplaymanager_getfolddisplaymode) | - | 获取可折叠设备的显示模式。 |
| [typedef void (\*OH_NativeDisplayManager_DisplayChangeCallback)(uint64_t displayId)](#oh_nativedisplaymanager_displaychangecallback) | OH_NativeDisplayManager_DisplayChangeCallback | 注册屏幕状态变化的回调函数。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayChangeListener(OH_NativeDisplayManager_DisplayChangeCallback displayChangeCallback, uint32_t *listenerIndex)](#oh_nativedisplaymanager_registerdisplaychangelistener) | - | 注册屏幕状态变化监听（如旋转变化、刷新率、DPI、分辨率等变化）。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayChangeListener(uint32_t listenerIndex)](#oh_nativedisplaymanager_unregisterdisplaychangelistener) | - | 取消屏幕状态变化的监听。 |
| [typedef void (\*OH_NativeDisplayManager_FoldDisplayModeChangeCallback)(NativeDisplayManager_FoldDisplayMode displayMode)](#oh_nativedisplaymanager_folddisplaymodechangecallback) | OH_NativeDisplayManager_FoldDisplayModeChangeCallback | 注册屏幕展开、折叠状态变化的回调函数。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener(OH_NativeDisplayManager_FoldDisplayModeChangeCallback displayModeChangeCallback, uint32_t *listenerIndex)](#oh_nativedisplaymanager_registerfolddisplaymodechangelistener) | - | 注册屏幕展开、折叠状态变化的监听。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener(uint32_t listenerIndex)](#oh_nativedisplaymanager_unregisterfolddisplaymodechangelistener) | - | 取消屏幕展开、折叠状态变化的监听。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateAllDisplays(NativeDisplayManager_DisplaysInfo **allDisplays)](#oh_nativedisplaymanager_createalldisplays) | - | 获取当前所有屏幕信息对象。 |
| [void OH_NativeDisplayManager_DestroyAllDisplays(NativeDisplayManager_DisplaysInfo *allDisplays)](#oh_nativedisplaymanager_destroyalldisplays) | - | 销毁所有屏幕的信息对象。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateDisplayById(uint32_t displayId,NativeDisplayManager_DisplayInfo **displayInfo)](#oh_nativedisplaymanager_createdisplaybyid) | - | 获取指定屏幕的信息对象。 |
| [void OH_NativeDisplayManager_DestroyDisplay(NativeDisplayManager_DisplayInfo *displayInfo)](#oh_nativedisplaymanager_destroydisplay) | - | 销毁指定屏幕的信息对象。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreatePrimaryDisplay(NativeDisplayManager_DisplayInfo **displayInfo)](#oh_nativedisplaymanager_createprimarydisplay) | - | 获取主屏信息对象。除2in1之外的设备获取的是设备自带屏幕的屏幕信息；2in1设备外接屏幕时获取的是当前主屏幕的屏幕信息；2in1设备没有外接屏幕时获取的是自带屏幕的屏幕信息。 |
| [typedef void (\*OH_NativeDisplayManager_AvailableAreaChangeCallback)(uint64_t displayId)](#oh_nativedisplaymanager_availableareachangecallback) | OH_NativeDisplayManager_AvailableAreaChangeCallback | 注册屏幕可用区域变化的回调函数。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterAvailableAreaChangeListener(OH_NativeDisplayManager_AvailableAreaChangeCallback availableAreaChangeCallback, uint32_t *listenerIndex)](#oh_nativedisplaymanager_registeravailableareachangelistener) | - | 注册屏幕可用区域变化监听。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterAvailableAreaChangeListener(uint32_t listenerIndex)](#oh_nativedisplaymanager_unregisteravailableareachangelistener) | - | 取消屏幕可用区域变化的监听。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateAvailableArea(uint64_t displayId, NativeDisplayManager_Rect **availableArea)](#oh_nativedisplaymanager_createavailablearea) | - | 获取屏幕的可用区域。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_DestroyAvailableArea(NativeDisplayManager_Rect *availableArea)](#oh_nativedisplaymanager_destroyavailablearea) | - | 销毁屏幕的可用区域。 |
| [typedef void (\*OH_NativeDisplayManager_DisplayAddCallback)(uint64_t displayId)](#oh_nativedisplaymanager_displayaddcallback) | OH_NativeDisplayManager_DisplayAddCallback | 注册屏幕连接的回调函数。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayAddListener(OH_NativeDisplayManager_DisplayAddCallback displayAddCallback, uint32_t *listenerIndex)](#oh_nativedisplaymanager_registerdisplayaddlistener) | - | 注册屏幕连接变化监听（如插入显示器）。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayAddListener(uint32_t listenerIndex)](#oh_nativedisplaymanager_unregisterdisplayaddlistener) | - | 取消屏幕连接的监听。 |
| [typedef void (\*OH_NativeDisplayManager_DisplayRemoveCallback)(uint64_t displayId)](#oh_nativedisplaymanager_displayremovecallback) | OH_NativeDisplayManager_DisplayRemoveCallback | 注册屏幕移除的回调函数。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayRemoveListener(OH_NativeDisplayManager_DisplayRemoveCallback displayRemoveCallback, uint32_t *listenerIndex)](#oh_nativedisplaymanager_registerdisplayremovelistener) | - | 注册屏幕移除变化监听（如移除显示器）。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayRemoveListener(uint32_t listenerIndex)](#oh_nativedisplaymanager_unregisterdisplayremovelistener) | - | 取消屏幕移除的监听。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDisplaySourceMode(uint64_t displayId, NativeDisplayManager_SourceMode *sourceMode)](#oh_nativedisplaymanager_getdisplaysourcemode) | - | 获取屏幕的显示模式。 |
| [NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDisplayPosition(uint64_t displayId, int32_t *x, int32_t *y)](#oh_nativedisplaymanager_getdisplayposition) | - | 获取屏幕的位置信息。 |

## 函数说明

### OH_NativeDisplayManager_GetDefaultDisplayId()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayId(uint64_t *displayId)
```

**描述**

获取默认屏幕的id号。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t *displayId | 默认屏幕的id号，非负整数，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayWidth()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayWidth(int32_t *displayWidth)
```

**描述**

获取默认屏幕的宽度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t *displayWidth | 默认屏幕的宽度，单位为px，该参数应为整数，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayHeight()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayHeight(int32_t *displayHeight)
```

**描述**

获取默认屏幕的高度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t *displayHeight | 默认屏幕的高度，单位为px，该参数应为整数，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayRotation()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayRotation(NativeDisplayManager_Rotation *displayRotation)
```

**描述**

获取默认屏幕的顺时针旋转角度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_Rotation](capi-oh-display-info-h.md#nativedisplaymanager_rotation) *displayRotation | 默认屏幕的顺时针旋转角度，具体可见[NativeDisplayManager_Rotation](capi-oh-display-info-h.md#nativedisplaymanager_rotation)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayOrientation()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayOrientation(NativeDisplayManager_Orientation *displayOrientation)
```

**描述**

获取默认屏幕的旋转方向。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_Orientation](capi-oh-display-info-h.md#nativedisplaymanager_orientation) *displayOrientation | 屏幕当前显示的方向，具体可见[NativeDisplayManager_Orientation](capi-oh-display-info-h.md#nativedisplaymanager_orientation)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayVirtualPixelRatio()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayVirtualPixelRatio(float *virtualPixels)
```

**描述**

获取默认屏幕的虚拟像素密度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float *virtualPixels | 屏幕的虚拟像素密度，该参数为浮点数，通常与densityPixels相同，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayRefreshRate()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayRefreshRate(uint32_t *refreshRate)
```

**描述**

获取默认屏幕的刷新率。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t *refreshRate | 屏幕的刷新率，该参数应为整数，单位为Hz，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayDensityDpi()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityDpi(int32_t *densityDpi)
```

**描述**

获取屏幕的物理像素密度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| int32_t *densityDpi | 屏幕的物理像素密度，表示每英寸上的像素点数。该参数为整数，单位为px，实际能取到的值取决于不同设备设置里提供的可选值。此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayDensityPixels()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityPixels(float *densityPixels)
```

**描述**

获取屏幕逻辑像素的密度。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float *densityPixels | 设备逻辑像素的密度，代表物理像素与逻辑像素的缩放系数，该参数为浮点数，受densityDPI范围限制，取值范围在[0.5，4.0]。一般取值1.0、3.0等，实际取值取决于不同设备提供的densityDpi。此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayScaledDensity()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayScaledDensity(float *scaledDensity)
```

**描述**

获取屏幕显示字体的缩放因子。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float *scaledDensity | 显示字体的缩放因子，该参数为浮点数，通常与densityPixels相同，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayDensityXdpi()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityXdpi(float *xDpi)
```

**描述**

获取屏幕X方向中每英寸屏幕的物理像素值。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float *xDpi | X方向中每英寸屏幕的物理像素值，该参数为浮点数，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDefaultDisplayDensityYdpi()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDefaultDisplayDensityYdpi(float *yDpi)
```

**描述**

获取Y方向中每英寸屏幕的物理像素值。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| float *yDpi | 获取Y方向中每英寸屏幕的物理像素值，该参数为浮点数，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo **cutoutInfo)
```

**描述**

获取挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_CutoutInfo](capi-nativedisplaymanager-cutoutinfo.md) **cutoutInfo | 挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息，具体可见[NativeDisplayManager_CutoutInfo](capi-nativedisplaymanager-cutoutinfo.md)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DestroyDefaultDisplayCutoutInfo()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_DestroyDefaultDisplayCutoutInfo(NativeDisplayManager_CutoutInfo *cutoutInfo)
```

**描述**

销毁挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_CutoutInfo](capi-nativedisplaymanager-cutoutinfo.md) *cutoutInfo | 销毁通过[OH_NativeDisplayManager_CreateDefaultDisplayCutoutInfo](capi-oh-display-manager-h.md#oh_nativedisplaymanager_createdefaultdisplaycutoutinfo)接口获取的挖孔屏、刘海屏、瀑布屏等不可用屏幕区域信息对象，具体可见[NativeDisplayManager_CutoutInfo](capi-nativedisplaymanager-cutoutinfo.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_IsFoldable()

```
bool OH_NativeDisplayManager_IsFoldable()
```

**描述**

查询设备是否可折叠。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12

**返回：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回查询设备是否可折叠的结果。true表示设备可折叠，false表示设备不可折叠。 |

### OH_NativeDisplayManager_GetFoldDisplayMode()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetFoldDisplayMode(NativeDisplayManager_FoldDisplayMode *displayMode)
```

**描述**

获取可折叠设备的显示模式。

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_FoldDisplayMode](capi-oh-display-info-h.md#nativedisplaymanager_folddisplaymode) *displayMode | 折叠设备当前的显示模式，具体可见[NativeDisplayManager_FoldDisplayMode](capi-oh-display-info-h.md#nativedisplaymanager_folddisplaymode)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DisplayChangeCallback()

```
typedef void (*OH_NativeDisplayManager_DisplayChangeCallback)(uint64_t displayId)
```

**描述**

注册屏幕状态变化的回调函数。

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 屏幕状态发生变化的编号。 |

### OH_NativeDisplayManager_RegisterDisplayChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayChangeListener(OH_NativeDisplayManager_DisplayChangeCallback displayChangeCallback, uint32_t *listenerIndex)
```

**描述**

注册屏幕状态变化监听（如旋转变化、刷新率、DPI、分辨率等变化）。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeDisplayManager_DisplayChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displaychangecallback) displayChangeCallback | 屏幕状态变化后触发的回调函数，回调函数定义见[OH_NativeDisplayManager_DisplayChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displaychangecallback)。 |
| uint32_t *listenerIndex | 注册成功后返回的监听编号，调用取消注册函数[OH_NativeDisplayManager_UnregisterDisplayChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_unregisterdisplaychangelistener)时作为入参使用，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_UnregisterDisplayChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayChangeListener(uint32_t listenerIndex)
```

**描述**

取消屏幕状态变化的监听。

**系统能力：** SystemCapability.WindowManager.WindowManager.Core

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t listenerIndex | 调用注册函数[OH_NativeDisplayManager_RegisterDisplayChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_registerdisplaychangelistener)时获取到的监听编号。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_FoldDisplayModeChangeCallback()

```
typedef void (*OH_NativeDisplayManager_FoldDisplayModeChangeCallback)(NativeDisplayManager_FoldDisplayMode displayMode)
```

**描述**

注册屏幕展开、折叠状态变化的回调函数。

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_FoldDisplayMode](capi-oh-display-info-h.md#nativedisplaymanager_folddisplaymode) displayMode | 折叠/展开动作执行后屏幕的状态，具体可见[NativeDisplayManager_FoldDisplayMode](capi-oh-display-info-h.md#nativedisplaymanager_folddisplaymode)。 |

### OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener(OH_NativeDisplayManager_FoldDisplayModeChangeCallback displayModeChangeCallback, uint32_t *listenerIndex)
```

**描述**

注册屏幕展开、折叠状态变化的监听。

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeDisplayManager_FoldDisplayModeChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_folddisplaymodechangecallback) displayModeChangeCallback | 屏幕展开和折叠变化后触发的回调函数，回调函数定义见[OH_NativeDisplayManager_FoldDisplayModeChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_folddisplaymodechangecallback)。 |
| uint32_t *listenerIndex | 注册成功后返回的监听编号，调用取消注册函数[OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_unregisterfolddisplaymodechangelistener)时作为入参使用，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterFoldDisplayModeChangeListener(uint32_t listenerIndex)
```

**描述**

取消屏幕展开、折叠状态变化的监听。

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t listenerIndex | 调用注册函数[OH_NativeDisplayManager_RegisterFoldDisplayModeChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_registerfolddisplaymodechangelistener)时获取到的监听编号。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_CreateAllDisplays()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateAllDisplays(NativeDisplayManager_DisplaysInfo **allDisplays)
```

**描述**

获取当前所有屏幕信息对象。

**系统能力：** SystemCapability.Window.SessionManager.Core

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_DisplaysInfo](capi-nativedisplaymanager-displaysinfo.md) **allDisplays | 当前所有的屏幕信息，具体可见[NativeDisplayManager_DisplaysInfo](capi-nativedisplaymanager-displaysinfo.md)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DestroyAllDisplays()

```
void OH_NativeDisplayManager_DestroyAllDisplays(NativeDisplayManager_DisplaysInfo *allDisplays)
```

**描述**

销毁所有屏幕的信息对象。

**系统能力：** SystemCapability.Window.SessionManager.Core

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_DisplaysInfo](capi-nativedisplaymanager-displaysinfo.md) *allDisplays | 销毁通过[OH_NativeDisplayManager_CreateAllDisplays](capi-oh-display-manager-h.md#oh_nativedisplaymanager_createalldisplays)接口获取的所有的屏幕信息，具体可见[NativeDisplayManager_DisplaysInfo](capi-nativedisplaymanager-displaysinfo.md)。 |

### OH_NativeDisplayManager_CreateDisplayById()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateDisplayById(uint32_t displayId,NativeDisplayManager_DisplayInfo **displayInfo)
```

**描述**

获取指定屏幕的信息对象。

**系统能力：** SystemCapability.Window.SessionManager.Core

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t displayId | 指定屏幕的id编号，该值为非负整数。 |
| [NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md) **displayInfo | 指定的屏幕信息对象，具体可见[NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DestroyDisplay()

```
void OH_NativeDisplayManager_DestroyDisplay(NativeDisplayManager_DisplayInfo *displayInfo)
```

**描述**

销毁指定屏幕的信息对象。

**系统能力：** SystemCapability.Window.SessionManager.Core

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md) *displayInfo | 销毁通过[OH_NativeDisplayManager_CreateDisplayById](capi-oh-display-manager-h.md#oh_nativedisplaymanager_createdisplaybyid)或者[OH_NativeDisplayManager_CreatePrimaryDisplay](capi-oh-display-manager-h.md#oh_nativedisplaymanager_createprimarydisplay)接口获取到的屏幕信息，具体可见[NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md)。 |

### OH_NativeDisplayManager_CreatePrimaryDisplay()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreatePrimaryDisplay(NativeDisplayManager_DisplayInfo **displayInfo)
```

**描述**

获取主屏信息对象。除2in1之外的设备获取的是设备自带屏幕的屏幕信息；2in1设备外接屏幕时获取的是当前主屏幕的屏幕信息；2in1设备没有外接屏幕时获取的是自带屏幕的屏幕信息。

**系统能力：** SystemCapability.Window.SessionManager.Core

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md) **displayInfo | 主屏的屏幕信息对象，具体可见[NativeDisplayManager_DisplayInfo](capi-nativedisplaymanager-displayinfo.md)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_AvailableAreaChangeCallback()

```
typedef void (*OH_NativeDisplayManager_AvailableAreaChangeCallback)(uint64_t displayId)
```

**描述**

注册屏幕可用区域变化的回调函数。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 屏幕的id号，非负整数。 |

### OH_NativeDisplayManager_RegisterAvailableAreaChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterAvailableAreaChangeListener(OH_NativeDisplayManager_AvailableAreaChangeCallback availableAreaChangeCallback, uint32_t *listenerIndex)
```

**描述**

注册屏幕可用区域变化监听。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeDisplayManager_AvailableAreaChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_availableareachangecallback) availableAreaChangeCallback | 屏幕可用区域变化后触发的回调函数，<br>回调函数定义见[OH_NativeDisplayManager_AvailableAreaChangeCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_availableareachangecallback)。 |
| uint32_t *listenerIndex | 注册成功后返回的监听编号，<br>调用取消注册函数[OH_NativeDisplayManager_UnregisterAvailableAreaChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_unregisteravailableareachangelistener)时作为入参使用，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_UnregisterAvailableAreaChangeListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterAvailableAreaChangeListener(uint32_t listenerIndex)
```

**描述**

取消屏幕可用区域变化的监听。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t listenerIndex | 调用注册函数<br>[OH_NativeDisplayManager_RegisterAvailableAreaChangeListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_registeravailableareachangelistener)时获取到的监听编号。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_CreateAvailableArea()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_CreateAvailableArea(uint64_t displayId, NativeDisplayManager_Rect **availableArea)
```

**描述**

获取屏幕的可用区域。该接口仅可在2in1设备使用。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 查询屏幕的id号，非负整数。 |
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md) **availableArea | 屏幕可用区域，具体可见[NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DestroyAvailableArea()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_DestroyAvailableArea(NativeDisplayManager_Rect *availableArea)
```

**描述**

销毁屏幕的可用区域。该接口仅可在2in1设备使用。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md) *availableArea | 销毁通过[OH_NativeDisplayManager_CreateAvailableArea](capi-oh-display-manager-h.md#oh_nativedisplaymanager_createavailablearea)获取的屏幕可用区域，<br>可用区域定义具体可见[NativeDisplayManager_Rect](capi-nativedisplaymanager-rect.md)。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DisplayAddCallback()

```
typedef void (*OH_NativeDisplayManager_DisplayAddCallback)(uint64_t displayId)
```

**描述**

注册屏幕连接的回调函数。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 新增屏幕的id号，非负整数。 |

### OH_NativeDisplayManager_RegisterDisplayAddListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayAddListener(OH_NativeDisplayManager_DisplayAddCallback displayAddCallback, uint32_t *listenerIndex)
```

**描述**

注册屏幕连接变化监听（如插入显示器）。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeDisplayManager_DisplayAddCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displayaddcallback) displayAddCallback | 屏幕连接后触发的回调函数，回调函数定义见[OH_NativeDisplayManager_DisplayAddCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displayaddcallback)。 |
| uint32_t *listenerIndex | 注册成功后返回的监听编号，<br>调用取消注册函数[OH_NativeDisplayManager_UnregisterDisplayAddListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_unregisterdisplayaddlistener)时作为入参使用，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_UnregisterDisplayAddListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayAddListener(uint32_t listenerIndex)
```

**描述**

取消屏幕连接的监听。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t listenerIndex | 调用注册函数[OH_NativeDisplayManager_RegisterDisplayAddListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_registerdisplayaddlistener)时获取到的监听编号。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_DisplayRemoveCallback()

```
typedef void (*OH_NativeDisplayManager_DisplayRemoveCallback)(uint64_t displayId)
```

**描述**

注册屏幕移除的回调函数。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 被移除屏幕的id号，非负整数。 |

### OH_NativeDisplayManager_RegisterDisplayRemoveListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_RegisterDisplayRemoveListener(OH_NativeDisplayManager_DisplayRemoveCallback displayRemoveCallback, uint32_t *listenerIndex)
```

**描述**

注册屏幕移除变化监听（如移除显示器）。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_NativeDisplayManager_DisplayRemoveCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displayremovecallback) displayRemoveCallback | 屏幕移除后触发的回调函数，回调函数定义见[OH_NativeDisplayManager_DisplayRemoveCallback](capi-oh-display-manager-h.md#oh_nativedisplaymanager_displayremovecallback)。 |
| uint32_t *listenerIndex | 注册成功后返回的监听编号，<br>调用取消注册函数[OH_NativeDisplayManager_UnregisterDisplayRemoveListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_unregisterdisplayremovelistener)时作为入参使用，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_UnregisterDisplayRemoveListener()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_UnregisterDisplayRemoveListener(uint32_t listenerIndex)
```

**描述**

取消屏幕移除的监听。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint32_t listenerIndex | 调用注册函数[OH_NativeDisplayManager_RegisterDisplayRemoveListener](capi-oh-display-manager-h.md#oh_nativedisplaymanager_registerdisplayremovelistener)时获取到的监听编号。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDisplaySourceMode()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDisplaySourceMode(uint64_t displayId, NativeDisplayManager_SourceMode *sourceMode)
```

**描述**

获取屏幕的显示模式。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 查询屏幕的id号，非负整数。 |
| [NativeDisplayManager_SourceMode](capi-oh-display-info-h.md#nativedisplaymanager_sourcemode) *sourceMode | 屏幕当前的显示模式，具体可见[NativeDisplayManager_SourceMode](capi-oh-display-info-h.md#nativedisplaymanager_sourcemode)，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。 |

### OH_NativeDisplayManager_GetDisplayPosition()

```
NativeDisplayManager_ErrorCode OH_NativeDisplayManager_GetDisplayPosition(uint64_t displayId, int32_t *x, int32_t *y)
```

**描述**

获取屏幕的位置信息。

**起始版本：** 20


**参数：**

| 参数项 | 描述 |
| -- | -- |
| uint64_t displayId | 查询屏幕的id号，非负整数。 |
| int32_t *x | 相对于主屏左上角的x方向坐标，此处作为出参返回。 |
| int32_t *y | 相对于主屏左上角的y方向坐标，此处作为出参返回。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode) | 返回屏幕管理接口的通用状态码，具体可见[NativeDisplayManager_ErrorCode](capi-oh-display-info-h.md#nativedisplaymanager_errorcode)。<br>当前仅支持主屏幕和扩展屏幕查询屏幕位置信息，其他屏幕查询会返回DISPLAY_MANAGER_ERROR_ILLEGAL_PARAM。 |


