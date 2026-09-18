# Stack

The **Stack** component provides a stack container where child components are successively stacked and the latter one overwrites the previous one. > **NOTE** > > - The general attribute align supports the mirroring capability on this component. > > **Child Components** > > Supported

## Stack

```TypeScript
Stack(options?: StackOptions)
```


> **NOTE:** 
> 
> Excessive component nesting can lead to performance degradation. In some scenarios, using component attributes
> directly or leveraging system APIs can achieve the same effect as the stack container, reducing the number of
> nested components and optimizing performance. For best practices, see
> [Preferentially Using Component Properties Instead of Nested Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-component-nesting-optimization#section78181114123811)
> .

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [StackOptions](arkts-arkui-stackoptions-i.md) | No | Alignment of child components in the container. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [StackOptions](arkts-arkui-stackoptions-i.md) |  |

## Examples

```TypeScript
When the [alignContent](#aligncontent) attribute of the Stack component is set to Alignment.Bottom and [syncLoad](#syncload) is set to true, the child components are displayed horizontally centered at the bottom of the Stack component, and all child components are loaded within the same frame.

The syncLoad attribute is added since API version 26.0.0.
```
