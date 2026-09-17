# RelativeContainer

The **RelativeContainer** component is a container component used for relative layout of elements in complex scenarios. Child components can define their alignment rules within the container using alignRules. > **NOTE** > > * When width and height are not set, > **RelativeContainer** defaults to 100% in both dimensions. > > * Since API version 11, setting width or height to > **"auto"** enables child-adaptive sizing. However, if the child components use the container as an anchor in the > horizontal direction, the **auto** value of **width** has no effect (equivalent to **width** not being set). The > same rule applies to the vertical direction. > > * Since API version 20, the size adaptation behavior of child components in the **RelativeContainer** component > follows the following rules, depending on the **LayoutPolicy** setting for > width and height: > **LayoutPolicy.wrapContent**: The child component adapts to its content size and is constrained by the size of the > ancestor node. **LayoutPolicy.fixAtIdealSize**: The child component adapts to its ideal content size and is not > constrained by the size of the ancestor node. If **width** is set to **wrapContent** or **fixAtIdealSize**, and the > child component (in the horizontal direction) directly or indirectly uses the **RelativeContainer** as its anchor, > the container's horizontal size will not adapt to the child component. The same rule applies to the vertical > direction. > > * For a child component of the container, > margin has a different meaning from the universal attribute **margin**. It indicates > the distance to the anchor in the respective direction. If there is no anchor in the respective direction, > **margin** in that direction does not take effect. > > **Child Components** > > Multiple child components are supported.

## RelativeContainer

```TypeScript
RelativeContainer()
```

Defines the constructor of RelativeContainer.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BarrierStyle](arkts-arkui-barrierstyle-i.md) | Defines the ID, direction, and referenced components of a barrier. |
| [GuideLinePosition](arkts-arkui-guidelineposition-i.md) | Defines the position of a guideline. |
| [GuideLineStyle](arkts-arkui-guidelinestyle-i.md) | Defines the ID, direction, and position of a guideline. |
| [LocalizedBarrierStyle](arkts-arkui-localizedbarrierstyle-i.md) | Defines the ID, direction, and referenced components of a barrier. |

### Enums

| Name | Description |
| --- | --- |
| [BarrierDirection](arkts-arkui-barrierdirection-e.md) | Defines the direction of a barrier. |
| [LocalizedBarrierDirection](arkts-arkui-localizedbarrierdirection-e.md) | Enumerates the directions of barriers with mirror mode support. |

## Examples

```TypeScript
### Example 1: Implementing a Layout Using Containers and Components as Anchors

This example demonstrates how to use the alignRules API to implement a layout with containers and their internal components as anchors.


```

```TypeScript
### Example 2: Setting Margins for Child Components

This example shows how to set margins for child components in the container.


```

```TypeScript
### Example 3: Configuring the Container to Adapt Its Size to Content

This example shows how to configure the container to adapt its size to content by setting width or height to "auto".


```

```TypeScript
### Example 4: Applying Vertical Offsets

This example uses [bias](ts-types.md#bias11) to offset the position of a child component between two anchors in the vertical direction.


```

```TypeScript
### Example 5: Setting Guidelines

This example demonstrates how to set guidelines in a relative layout using the [guideLine](arkts-arkui-relativecontainer-comp-attribute.md#guideline) API, with child components using these guidelines as anchors.


```

```TypeScript
### Example 6: Implementing Barriers

This example shows how to set barriers in a relative layout using the [barrier](arkts-arkui-relativecontainer-comp-attribute.md#barrier) API, with child components using these barriers as anchors.


```

```TypeScript
### Example 7: Creating Chains

This example uses the [chainMode](ts-universal-attributes-location.md#chainmode12) API to implement a horizontal [SPREAD](ts-universal-attributes-location.md#chainstyle12) chain, a [SPREAD_INSIDE](ts-universal-attributes-location.md#chainstyle12) chain, and a [PACKED](ts-universal-attributes-location.md#chainstyle12) chain from top to bottom.


```

```TypeScript
### Example 8: Creating a Chain with Offsets

This example uses the [chainMode](ts-universal-attributes-location.md#chainmode12) and [bias](ts-types.md#bias11) APIs to implement a horizontally biased [PACKED](ts-universal-attributes-location.md#chainstyle12) chain.


```

```TypeScript
### Example 9: Implementing a Mirror Effect

This example demonstrates how to use [LocalizedAlignRuleOptions](ts-universal-attributes-location.md#localizedalignruleoptions12) and [LocalizedBarrierDirection](arkts-arkui-localizedbarrierdirection-e.md) for alignment when using barriers as anchors in mirror mode (direction set to Direction.Rtl).


```

```TypeScript
### Example 10: Setting Component Weights in a Chain

This example demonstrates how to use [chainWeight](ts-universal-attributes-location.md#chainweight14) to set the size weights of components in a chain.

You must first set the chain alignment rules of child components through alignRules (to ensure that the components form a chain in the horizontal or vertical direction), and then set the chain style (such as SPREAD, SPREAD_INSIDE, and PACKED) through chainMode. chainWeight takes effect only in chain mode.
```
