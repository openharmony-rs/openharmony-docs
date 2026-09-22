# FolderStackOptions

```TypeScript
interface FolderStackOptions
```

Configuration object for the **FolderStack** hover status, which describes the information about child components that need to be moved to the upper screen in hover status.

> **NOTE:** 
> 
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18.
> While historical version information is preserved for anonymous objects, there may be cases where the outer element
> 's

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## upperItems

```TypeScript
upperItems?: Array<string>
```

Array of IDs of child components that will be moved to the upper half-screen in hover status.

Default value: **[]**

When hover is triggered, the child components in the **upperItems** array automatically avoid the foldable screen crease area and move to the upper half-screen, while other components are stacked in the lower half-screen area.

**Type:** Array&lt;string&gt;

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
