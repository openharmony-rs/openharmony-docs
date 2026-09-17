# XComponentType

The type of XComponent

@enum { number }

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SURFACE

```TypeScript
SURFACE
```

Surface type. The default type is used.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COMPONENT

```TypeScript
COMPONENT
```

Component type.

**Since:** 11

**Deprecated since:** 12

**Substitutes:** [Column](arkts-arkui-flexdirection-e.md#column)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEXTURE

```TypeScript
TEXTURE
```

Texture type. Supports EGL/OpenGLES and media data rendering. Custom drawing content is composited with XComponent’s native content before display. Key features:
1. Maintains frame synchronization between GPU textures and ArkUI drawing commands.
2. Supports unified animation with built-in components.
3. Utilizes GPU composition, which may have higher power consumption than the SURFACE type
using the display subsystem (DSS).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NODE

```TypeScript
NODE
```

Node type.

**Since:** 12

**Deprecated since:** 20

**Substitutes:** ContentSlot

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
