# off (System API)

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## off

```TypeScript
function off(type: string): boolean
```

Remove registered event

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | string | Yes | Remove the type of registered event. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return removed result. |
