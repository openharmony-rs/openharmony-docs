# WindowManager_WindowProperties

```c
typedef struct WindowManager_WindowProperties {...} WindowManager_WindowProperties
```

## 概述

The struct describes the window properties.

<!--Device-typedef struct WindowManager_WindowProperties {...} WindowManager_WindowProperties--><!--Device-typedef struct WindowManager_WindowProperties {...} WindowManager_WindowProperties-End-->

**系统能力：** SystemCapability.Window.SessionManager

**起始版本：** 15

**相关模块：** [WindowManager](capi-arkui-windowmanager.md)

**所在头文件：** [oh_window_comm.h](capi-oh-window-comm-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [WindowManager_Rect](capi-windowmanager-windowmanager-rect.md) windowRect | Position and size of the window.<br><!--Device-WindowManager_Rect windowRect--><!--Device-WindowManager_Rect windowRect-End--> |
| [WindowManager_Rect](capi-windowmanager-windowmanager-rect.md) drawableRect | Size of the drawable area within the window.<br><!--Device-WindowManager_Rect drawableRect--><!--Device-WindowManager_Rect drawableRect-End--> |
| [WindowManager_WindowType](capi-oh-window-comm-h.md#windowmanager_windowtype) type | Window type.<br><!--Device-WindowManager_WindowType type--><!--Device-WindowManager_WindowType type-End--> |
| bool isFullScreen | Whether the window is in full-screen mode. The default value is **false**. **true** if in full-screen mode, ** false** otherwise.<br><!--Device-bool isFullScreen--><!--Device-bool isFullScreen-End--> |
| bool isLayoutFullScreen | Whether the window layout is immersive. The default value is **false**. **true** if immersive, **false** otherwise.<br><!--Device-bool isLayoutFullScreen--><!--Device-bool isLayoutFullScreen-End--> |
| bool focusable | Whether the window is focusable. The default value is **true**. **true** if focusable, **false** otherwise.<br><!--Device-bool focusable--><!--Device-bool focusable-End--> |
| bool touchable | Whether the window is touchable. The default value is **true**. **true** if touchable, **false** otherwise.<br><!--Device-bool touchable--><!--Device-bool touchable-End--> |
| float brightness | Screen brightness of the window. The value is a floating-point number in the range [0.0, 1.0] or is set to **-1. 0**, where **1.0** indicates the brightest, and **-1.0** is the default brightness.<br><!--Device-float brightness--><!--Device-float brightness-End--> |
| bool isKeepScreenOn | Whether the screen is steady on. The default value is **false**. **true** if steady on, **false** otherwise.<br><!--Device-bool isKeepScreenOn--><!--Device-bool isKeepScreenOn-End--> |
| bool isPrivacyMode | Whether privacy mode is enabled for the window. The default value is **false**. **true** if enabled, **false** otherwise.<br><!--Device-bool isPrivacyMode--><!--Device-bool isPrivacyMode-End--> |
| bool isTransparent | Whether the window is transparent. The default value is **false**. **true** if transparent, **false** otherwise.<br><!--Device-bool isTransparent--><!--Device-bool isTransparent-End--> |
| uint32_t id | Window ID. The default value is **0**, and the value is an integer.<br><!--Device-uint32_t id--><!--Device-uint32_t id-End--> |
| uint32_t displayId | ID of the screen where the window is located. By default, the ID of the primary screen is returned. The value is an integer.<br><!--Device-uint32_t displayId--><!--Device-uint32_t displayId-End--> |


