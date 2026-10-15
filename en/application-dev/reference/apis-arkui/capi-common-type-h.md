# common_type.h
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=61f18ec8e1ceacc8a14d94c25acf53247c827d4b translatedAt=2026-10-10T10:50:30.954Z pushedAt=2026-10-12T01:21:42.863Z -->

## Overview

Defines the common types of ArkUI native APIs.

**File to include:** <arkui/common_type.h>

**Library:** libace_ndk.z.so

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Since:** 12

**Related module:** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | Defines an event callback type, which is used to define the callback function and its user-defined data. When an API of this type is called to trigger a callback, the callback is invoked and **userData** is passed as a parameter. |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | Defines a numeric type used by ArkUI on the native side, including floating-point, signed integer, and unsigned integer types. |
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | Defines the [setAttribute](capi-arkui-nativemodule-arkui-nativenodeapi-1.md#setattribute) function. This is a general input parameter struct. Individual attribute-setting APIs can use appropriate member variables within it to store parameter data of specific types. |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | Defines a mask area. |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | Describes the width and height of a component. |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | Defines an offset, which describes the position of the current component relative to its parent component. |
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | Defines the pointer to an ArkUI native component object, which is used to identify and pass component instances in ArkUI native APIs, for example, creating, mounting, removing, or destroying component nodes. |
| [ArkUI_NodeContent*](capi-arkui-nativemodule-arkui-nodecontent8h.md) | ArkUI_NodeContentHandle | Defines the pointer to the node content on the native side, which is used to reference and pass the **NodeContent** instance in native APIs. |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | Defines the layout constraint, which is used to limit the size range during component layout. You can set the minimum and maximum size constraints. The constraint values are non-negative floating-point numbers. During component layout, the system limits the final size range of the component based on the constraint values to ensure that the layout result meets the constraints. This struct is applicable to scenarios where the size range of child components needs to be controlled during custom layout container design. For example, in a waterfall layout, the height of image cards can be limited; in a grid layout, the size of cells can be limited. It is also applicable to scenarios where the upper and lower limits of the component size need to be restricted. For example, the maximum width of an image display component can be limited to prevent stretching, and the minimum size can be limited in a responsive layout to ensure readability. This prevents the component size from exceeding the expected range, enabling more precise layout control, improving the predictability and stability of the layout, and enhancing the controllability of the interface. |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | Defines component drawing context, which is used to provide drawing context information during the drawing of a custom component. You can obtain the canvas pointer used for drawing and the size of the drawing area. |
| [ArkUI_Context](capi-arkui-nativemodule-arkui-context.md) | ArkUI_Context | Defines the context object of the native UI. |
| [ArkUI_Context*](capi-arkui-nativemodule-arkui-context8h.md) | ArkUI_ContextHandle | Defines the pointer to the context object of ArkUI on the native side, which is used to represent the UI context of the page where the component is located. You can obtain the pointer through [OH_ArkUI_GetContextByNode](capi-native-node-h.md#oh_arkui_getcontextbynode) or [OH_ArkUI_GetContextFromNapiValue](capi-native-node-napi-h.md#oh_arkui_getcontextfromnapivalue) and use it as the context input parameter for APIs such as UI task scheduling, animation, and focus control. |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | Defines a component event. This is a general struct type. This struct is used to pass event information in the component event handling process. |
