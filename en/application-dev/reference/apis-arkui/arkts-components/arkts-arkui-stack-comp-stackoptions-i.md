# StackOptions

```TypeScript
declare interface StackOptions
```

Sets the alignment method of the child component in the stack container.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. The
> initial version information of the historical anonymous objects has been retained, which may result in the outer
> element's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent?: Alignment
```

Alignment of child components in the container. When this attribute and the constructor input parameter are set at the same time, the value set by this attribute takes effect.

Default value: **Alignment.Center**

Invalid value: The default value is used.

**Note:** When this parameter and [align](arkts-arkui-common-comp-commonmethod-c.md#align) are set at the same time, the attribute value set later overrides the one set earlier.

**Type:** [Alignment](../arkts-apis/arkts-arkui-alignment-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
