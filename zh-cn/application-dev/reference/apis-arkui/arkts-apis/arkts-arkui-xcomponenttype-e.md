# XComponentType

```TypeScript
declare enum XComponentType
```

XComponent的类型

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SURFACE

```TypeScript
SURFACE
```

用于EGL/OpenGLES和媒体数据写入，单独展示开发者定制的绘制内容到屏幕上。背景色设置为黑色时走显示子系统（DSS）。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COMPONENT

```TypeScript
COMPONENT
```

Component type.

**起始版本：** 10

**废弃版本：** 12

**替代接口：** [Column](arkts-arkui-flexdirection-e.md#column)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEXTURE

```TypeScript
TEXTURE
```

用于EGL/OpenGLES和媒体数据写入，开发者定制的绘制内容将与XComponent组件的内容合成后展示到屏幕上。1、保持帧同步，保持在同一帧将图形处理器（GPU）纹理和ArkUI其他的绘制指令统一发给渲染服务(RenderService)。2、动效和系统组件统一。3、走图形处理器（GPU）合成，相比surface可能走显示子系统（DSS）功耗更高。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NODE

```TypeScript
NODE
```

用于Native UI节点的占位容器，开发者通过Native接口开发的页面组件可展示在此容器区域内。

**说明：** 

从API version 12开始支持，从API version 20开始废弃，推荐使用[ContentSlot](../../../ui/rendering-control/arkts-rendering-control-contentslot.md)组件替代。

**起始版本：** 12

**废弃版本：** 20

**替代接口：** [ContentSlot](../arkts-components/arkts-arkui-contentslot-comp.md#contentslot)

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
