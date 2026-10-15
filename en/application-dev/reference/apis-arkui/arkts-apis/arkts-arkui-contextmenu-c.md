# ContextMenu

```TypeScript
declare class ContextMenu
```

The [Menu](../../../ui/arkts-popup-and-menu-components-menu.md) component is a great option for creating menus, but it relies on a bound UI component to work. Since API version 18, however, the global API [openMenu](arkts-arkui-arkui-uicontext-promptaction-c.md#openmenu) offers a more flexible solution. This API can be used directly or encapsulated in scenarios where no bound UI components are available, making it ideal for use cases such as event callbacks or when integrating with external systems.

**Since:** 8

<!--Device-unnamed-declare class ContextMenu--><!--Device-unnamed-declare class ContextMenu-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## close

```TypeScript
static close()
```

Invoking method close.

**Since:** 11

**Deprecated since:** 18

**Substitutes:** [close](arkts-arkui-arkui-uicontext-contextmenucontroller-c.md#close)

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ContextMenu-static close()--><!--Device-ContextMenu-static close()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
