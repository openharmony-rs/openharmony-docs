# $rawfile

## $rawfile

```TypeScript
declare function $rawfile(value: string): Resource
```

global &#36;rawfile function

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | name of the file in the resources/rawfile directory of the project. When referencing resources of the Resource type, make sure the data type is the same as that of the attribute method. For example, if an attribute method supports the string &#124; Resource types, the data type of the Resource type must be string. |

**Return value:**

| Type | Description |
| --- | --- |
| [Resource](../arkts-apis/arkts-arkui-resource-t.md) |  |
