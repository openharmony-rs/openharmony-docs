# common_type.h

## 概述

定义ArkUI Native API的公共类型。

**库：** libace_ndk.z.so

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**起始版本：** 12

**相关模块：** [ArkUI_NativeModule](capi-arkui-nativemodule.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [ArkUI_ContextCallback](capi-arkui-nativemodule-arkui-contextcallback.md) | ArkUI_ContextCallback | 事件回调类型，用于定义回调函数及其用户自定义数据。使用该类型的接口触发回调时，会调用callback，并将userData作为参数传入。 |
| [ArkUI_NumberValue](capi-arkui-nativemodule-arkui-numbervalue.md) | ArkUI_NumberValue | ArkUI 在 Native 侧使用的数字类型，用于通过统一类型承载浮点、有符号整型和无符号整型数值。 |
| [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) | ArkUI_AttributeItem | 定义节点属性接口的通用入参结构。 |
| [ArkUI_Rect](capi-arkui-nativemodule-arkui-rect.md) | ArkUI_Rect | 定义矩形区域。 |
| [ArkUI_IntSize](capi-arkui-nativemodule-arkui-intsize.md) | ArkUI_IntSize | 定义组件宽高。 |
| [ArkUI_IntOffset](capi-arkui-nativemodule-arkui-intoffset.md) | ArkUI_IntOffset | 定义组件位置。 |
| [ArkUI_Node*](capi-arkui-nativemodule-arkui-node8h.md) | ArkUI_NodeHandle | 定义 ArkUI Native 组件实例对象指针，用于在 ArkUI Native 接口中标识和传递组件实例，例如创建、挂载、移除或销毁组件节点。 |
| [ArkUI_NodeContent*](capi-arkui-nativemodule-arkui-nodecontent8h.md) | ArkUI_NodeContentHandle | 定义ArkUI_NodeContent在Native侧的实例对象指针，用于在Native接口中引用和传递NodeContent实例。 |
| [ArkUI_LayoutConstraint](capi-arkui-nativemodule-arkui-layoutconstraint.md) | ArkUI_LayoutConstraint | 定义组件布局过程中的尺寸约束。 |
| [ArkUI_DrawContext](capi-arkui-nativemodule-arkui-drawcontext.md) | ArkUI_DrawContext | 定义组件绘制上下文的结构体类型，用于在自定义组件绘制过程中提供绘制上下文信息，可获取用于绘制的 Canvas 指针和可绘制区域大小。 |
| [ArkUI_Context*](capi-arkui-nativemodule-arkui-context8h.md) | ArkUI_ContextHandle | 定义ArkUI Native上下文对象指针。 |
| [ArkUI_NodeEvent](capi-arkui-nativemodule-arkui-nodeevent.md) | ArkUI_NodeEvent | 定义组件事件通用结构类型。 |

