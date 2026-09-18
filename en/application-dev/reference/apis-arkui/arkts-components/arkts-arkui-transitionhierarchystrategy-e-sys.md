# TransitionHierarchyStrategy (System API)

Enumerates the strategies for the hierarchical position movement of **in** / **out** components in the component tree during the shared element transition process.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0
```

The **in** / **out** components maintain their original hierarchy levels and are affected by the scale and position of their parent components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12 - 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## ADAPTIVE

```TypeScript
ADAPTIVE = 1
```

The component with the lower hierarchy level between the **in** and **out** components is promoted to the hierarchy level of the higher one in the component tree.

This mode also causes the promoted components to be decoupled from their parent components, not affected by the scale and position of their parent components.

For example, if the **in** component is at a higher hierarchy level than the **out** component, in this mode the **out** component will be decoupled from its own parent component during the animation process and promoted to the hierarchical position of the **in** component, while the **in** component's hierarchical position remains unchanged.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12 - 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
