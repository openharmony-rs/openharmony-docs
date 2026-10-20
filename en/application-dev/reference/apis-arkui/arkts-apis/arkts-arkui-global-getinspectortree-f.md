# getInspectorTree

## Modules to Import

```TypeScript
```

## getInspectorTree

```TypeScript
export declare function getInspectorTree(): Object
```

Obtains the component tree and component attributes.<br>This API is intended for application testing purposes only. It is recommended that you call this API after application startup and layout completion. The API requires significant processing time. Avoid using it.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-unnamed-export declare function getInspectorTree(): Object--><!--Device-unnamed-export declare function getInspectorTree(): Object-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Object | JSON object of the component tree and component attribute list. For details about each field in the component, see the return value description of getInspectorInfo. |
