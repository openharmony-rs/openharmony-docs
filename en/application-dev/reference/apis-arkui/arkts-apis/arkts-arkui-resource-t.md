# Resource

```TypeScript
declare type Resource = import('../api/global/resource').Resource
```

Defines reference resources for component attributes. Resource files must be stored and managed in specific subdirectories. For examples of resource directories, see [Resource Categories](../../../quick-start/resource-categories-and-access.md#resource-categories).

> **NOTE:** 
> 
> - When a resource type is referenced, ensure that the data type in the resource type object is consistent with the type of the attribute method that uses the resource type as a parameter. For example, if an attribute method supports setting string | Resource, the data type should also be string when the Resource reference type is used.
> 
> - When a resource type is referenced, ensure that the usage of the resource type object is currently supported.Otherwise, the effect of the attribute that uses the resource type as a parameter will be the same as when the attribute is not set.
> 
> - &#36;rawfile does not support preview through the [Previewer](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-previewer-arkts-js).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Type:** import('../api/global/resource').Resource
