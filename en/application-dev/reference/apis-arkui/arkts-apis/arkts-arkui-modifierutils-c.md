# ModifierUtils

ModifierUtils provides utility methods for modifier and attribute operations.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## isInstanceOf

```TypeScript
static isInstanceOf<T extends CommonMethod<T>>(instance: T, componentName: string): boolean
```

Checks if the given instance is of the specified component type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instance | T | Yes | The instance to check. |
| componentName | string | Yes | The name of the component type to check against. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the instance is of the specified component type. Otherwise, returns false. @static |
