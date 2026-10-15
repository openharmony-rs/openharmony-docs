# common_type.h

## Overview

Defines the common types for ArkUI native APIs.

**Library**: libace_ndk.z.so

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | Provides an event callback type, which is used to define the callback function and its user-defined data. When an API of this type is called to trigger a callback, the callback is invoked and **userData** is passed as a parameter. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | Defines a numeric type used by ArkUI on the native side, including floating-point, signed integer, and unsigned integer types. |
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | Defines the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. This is a general input parameter struct. Individual attribute-setting API can use appropriate member variables within it to store parameter data of specific types. |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | Defines a rectangular area. |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | Describes the width and height of a component. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | Describes the position of a component. |
| [ArkUI_NodeHandle](capi-arkui-nativemodule-arkui-nodehandle.md) | ArkUI_NodeHandle | Defines the pointer to an ArkUI native component object, which is used to identify and pass component instances in ArkUI native APIs, for example, creating, mounting, removing, or destroying component nodes. |
| [ArkUI_NodeContentHandle](capi-arkui-nativemodule-arkui-nodecontenthandle.md) | ArkUI_NodeContentHandle | Defines the pointer to an **ArkUI_NodeContent** object on the native side, which is used to reference and pass a **NodeContent** instance in native APIs. |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | Sets the size constraints of a component during component layout. |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | Defines component drawing context, which is used to provide drawing context information during the drawing of a custom component. You can obtain the canvas pointer used for drawing and the size of the drawing area. |
| [ArkUI_Context](capi-arkui-nativemodule-arkui-context.md) | ArkUI_Context | Defines a context object of the ArkUI native UI, which is used to represent the UI context of the page where the component is located. The pointer type is [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md). You can obtain the context using OH_ArkUI_GetContextByNode and use it as the input parameter for APIs such as dragging, animation, and UI task scheduling. |
| [ArkUI_ContextHandle](capi-arkui-nativemodule-arkui-contexthandle.md) | ArkUI_ContextHandle | Defines the pointer to the context object of ArkUI on the native side, which is used to represent the UI context of the page where the component is located. You can obtain the pointer through OH_ArkUI_GetContextByNode or OH_ArkUI_GetContextFromNapiValue and use the pointer as the context input parameter for APIs such as UI task scheduling, animation, and focus control. |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | Defines a component event. This is a general struct type. This struct is used to pass event information in the component event handling process. |

