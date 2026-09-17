# ResourceUsageObserver

```TypeScript
export type ResourceUsageObserver = (resourceType: ResourceType, resourceSize: number, detailInfo?: Record<string, number>) => void
```

The observer will be called by the system when resource usage exceed threshold.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resourceType | [ResourceType](arkts-ability-errormanager-resourcetype-e.md) | Yes | The type of resource. |
| resourceSize | number | Yes | The amount of resources occupied. The value must be greater than **0**.<br>Unit: KB. |
| detailInfo | Record&lt;string, number&gt; | No | Key-value pair of the resource type and its size.<br>This parameter is available only when resourceType is set to PSS_MEMORY. If resourceType is set to other types or default values, this parameter is left blank. The key is the lowercase memory type, and the value is the resource size of the corresponding subdivision item. The keys of subdivision items include arkts, native, ion, gpu, ashmem, and other. The second value must be greater than * * 0 * *, in KB. |
