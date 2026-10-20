# getInspectorByKey

## Modules to Import

```TypeScript
```

## getInspectorByKey

```TypeScript
export declare function getInspectorByKey(id: string): string
```

Obtains all attributes of the component with the specified ID, excluding the information about child components.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function getInspectorByKey(id: string): string--><!--Device-unnamed-export declare function getInspectorByKey(id: string): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | string | Yes | ID of the component whose attributes are to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| string | JSON string of the component attribute list.<br>**Note:** <br>The string information contains the tag and ID of the component, the position information (coordinates relative to the upper left corner of the window), and the attribute information contained in the component (for test inspection). For the meaning of each field in the component, see the return value description of getInspectorInfo. |
