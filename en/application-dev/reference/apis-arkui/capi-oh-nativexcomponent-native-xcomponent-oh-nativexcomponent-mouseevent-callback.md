# OH_NativeXComponent_MouseEvent_Callback
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @pengzhiwen3-->
<!--Designer: @dutie123-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=26981b54dcb92d5646f17bc8dcf56ce1bdfdfcf7 translatedAt=2026-08-27T08:48:05.720Z pushedAt=2026-08-28T02:36:50.694Z -->

```c
typedef struct OH_NativeXComponent_MouseEvent_Callback {...} OH_NativeXComponent_MouseEvent_Callback
```

## Overview

Defines the capability of registering callbacks for mouse events and hover events. You can use this callback struct to listen for mouse and stylus interaction behaviors on **NativeXComponent**, which is applicable to scenarios where pointer input interactions need to be handled on the native side. Among them, **DispatchMouseEvent** focuses on operation behaviors within the component, such as mouse button press, release, and movement, while **DispatchHoverEvent** focuses on hover state changes when the mouse or stylus enters or leaves the component. The two listen to different dimensions and can be registered simultaneously as needed.

**Since**: 9

**Related module**: [OH_NativeXComponent Native XComponent](capi-oh-nativexcomponent-native-xcomponent.md)

**Header file**: [native_interface_xcomponent.h](capi-native-interface-xcomponent-h.md)

## Summary

### Member Functions

| Name| Description|
| -- | -- |
| [void (\*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)](#dispatchmouseevent) | Invoked when a mouse event is triggered.|
| [void (\*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)](#dispatchhoverevent) | Invoked when a hover event is triggered.|

## Member Function Description

### DispatchMouseEvent()

```c
void (*DispatchMouseEvent)(OH_NativeXComponent* component, void* window)
```

**Description**


Called when a mouse event (for example, pressing, releasing, or moving a mouse button) is triggered.

**Since**: 9

**Parameters**

| Name                               | Description|
|------------------------------------| -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
| void* window | **NativeWindow** handle associated when the mouse event is triggered. |

### DispatchHoverEvent()

```c
void (*DispatchHoverEvent)(OH_NativeXComponent* component, bool isHover)
```

**Description**


Called when a hover event is triggered. This API is triggered when the mouse or stylus enters or leaves the component.

**Since**: 9

**Parameters**

| Name                               | Description|
|------------------------------------| -- |
| [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md)* component | Pointer to an [OH_NativeXComponent](capi-oh-nativexcomponent-native-xcomponent-oh-nativexcomponent.md) instance.|
| bool isHover                       | Whether the mouse or stylus hovers over the component. The value is **true** when the mouse or stylus enters the component, and **false** when it leaves. |


