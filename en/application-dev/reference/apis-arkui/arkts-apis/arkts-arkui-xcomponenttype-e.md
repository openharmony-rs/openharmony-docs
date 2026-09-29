# XComponentType

```TypeScript
declare enum XComponentType
```

The type of XComponent

**Since:** 10

<!--Device-unnamed-declare enum XComponentType--><!--Device-unnamed-declare enum XComponentType-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SURFACE

```TypeScript
SURFACE
```

Used for EGL/OpenGLES and media data writing, displaying developer-customized rendering content on the screen independently. When the background color is set to black, the display subsystem (DSS) is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-XComponentType-SURFACE--><!--Device-XComponentType-SURFACE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## COMPONENT

```TypeScript
COMPONENT
```

Uses [XComponent](../arkts-components/arkts-arkui-xcomponent-comp.md) as a container component, supporting non-UI logic execution within it to dynamically load display content.

**NOTE:** 

This API is supported since API version 10 and deprecated since API version 12. You are advised to use other container components instead.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** [Column](arkts-arkui-flexdirection-e.md#column)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-XComponentType-COMPONENT--><!--Device-XComponentType-COMPONENT-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## TEXTURE

```TypeScript
TEXTURE
```

Used for EGL/OpenGLES and media data writing. The developer-customized rendering content is composited with the XComponent component's content and then displayed on the screen. 1. Frame synchronization is maintained, and the GPU texture and other ArkUI drawing instructions are sent to the render service (RenderService) in the same frame.
2. Animations and system components are unified. 3. GPU compositing is used, which may consume more power compared
to the display subsystem (DSS) path used by surface.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-XComponentType-TEXTURE--><!--Device-XComponentType-TEXTURE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## NODE

```TypeScript
NODE
```

Placeholder container for Native UI nodes. Page components developed by developers through native APIs can be displayed within this container area.

**NOTE:** 

This API is supported since API version 12 and deprecated since API version 20. You are advised to use the [ContentSlot](../../../ui/rendering-control/arkts-rendering-control-contentslot.md) component instead.

**Since:** 12

**Deprecated since:** 20

**Substitutes:** [ContentSlot](../arkts-components/arkts-arkui-contentslot-comp.md)

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-XComponentType-NODE--><!--Device-XComponentType-NODE-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
