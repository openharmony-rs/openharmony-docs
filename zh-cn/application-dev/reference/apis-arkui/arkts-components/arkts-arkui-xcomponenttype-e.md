# XComponentType

The type of XComponent

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SURFACE

```TypeScript
SURFACE
```

Surface type. The default type is used.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## COMPONENT

```TypeScript
COMPONENT
```

Component type.

**起始版本：** 11

**废弃版本：** 12

**替代接口：** Column

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## TEXTURE

```TypeScript
TEXTURE
```

Texture type.
Supports EGL/OpenGLES and media data rendering.
Custom drawing content is composited with XComponent’s native content before display.
Key features:
1. Maintains frame synchronization between GPU textures and ArkUI drawing commands.
2. Supports unified animation with built-in components.
3. Utilizes GPU composition, which may have higher power consumption than the SURFACE type
using the display subsystem (DSS).

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本23开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## NODE

```TypeScript
NODE
```

Node type.

**起始版本：** 12

**废弃版本：** 20

**替代接口：** ContentSlot

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

