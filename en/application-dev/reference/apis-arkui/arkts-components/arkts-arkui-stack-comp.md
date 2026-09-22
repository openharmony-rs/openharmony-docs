# Stack

Defines a stack container where child components are successively stacked and the latter one overwrites the previous one. The stacking order is based on the declaration order of child components in the parent container. A child component declared later has a higher rendering level and visually covers the preceding child components. It is suitable for scenarios that require layered layout, such as floating buttons or prompt messages on a page, text labels overlaid on images or videos, and multi-layer pop-up windows or dialog boxes. Compared with nesting multiple containers to achieve the layered effect, **Stack** provides a simpler and more efficient solution.

> **NOTE** > > - The general attribute [align](arkts-arkui-common-comp-commonmethod-c.md#align) supports the mirroring capability on > this component.

## Child Components

Supported.

## Stack

```TypeScript
Stack(options?: StackOptions)
```

Defines a stack container where child components are successively stacked and the latter one overwrites the previous one. The stacking order is based on the declaration order of child components in the parent container. A child component declared later has a higher rendering level and visually covers the preceding child components.

> **NOTE:** 
> 
> Excessive component nesting can lead to performance degradation. In scenarios where the same layout effect can be
> achieved through component attributes or system APIs, using these alternatives can reduce the nesting depth and
> thereby optimize performance. For best practices, see
> [Optimizing Component Nesting - Preferentially Using Component Properties Instead of Nested Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-component-nesting-optimization#section78181114123811).
> 
> When both the **alignContent** parameter of this API and [align](arkts-arkui-common-comp-commonmethod-c.md#align) are
> set, whichever is set last takes effect. When both the **alignContent** parameter of this API and the
> **alignContent** attribute are set, the value set by the attribute takes effect.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [StackOptions](arkts-arkui-stack-comp-stackoptions-i.md) | No | Alignment of child components in the container. Pass this parameter when child components need to be aligned to a specific position (such as top, bottom, or top-left corner) instead of being centered by default. If this parameter is not passed, the default configuration of **StackOptions** is used, in which **alignContent** defaults to **Alignment.Center**. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [StackOptions](arkts-arkui-stack-comp-stackoptions-i.md) | Sets the alignment method of the child component in the stack container. |

## Examples
