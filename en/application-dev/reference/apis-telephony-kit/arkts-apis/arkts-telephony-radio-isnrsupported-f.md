# isNRSupported

## Modules to Import

```TypeScript
import { radio } from '@kit.TelephonyKit';
```

## isNRSupported

```TypeScript
function isNRSupported(): boolean
```

Checks whether the current device supports NR.

**Since:** 9

**System capability:** SystemCapability.Telephony.CoreService

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: supported<br>- **false**: not supported |

**Examples**

```TypeScript
let result: boolean = radio.isNRSupported();
console.info("Result: "+ result);
```


<a id="isnrsupported-1"></a>

## isNRSupported

```TypeScript
function isNRSupported(slotId: number): boolean
```

Checks whether the SIM card in the specified slot supports NR.

**Since:** 9

**System capability:** SystemCapability.Telephony.CoreService

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| slotId | number | Yes | Card slot ID.<br>- **0**: card slot 1. <br>- **1**: card slot 2 |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | **true**: supported<br>- **false**: not supported |

**Examples**

```TypeScript
let slotId: number = 0;
let result: boolean = radio.isNRSupported(slotId);
console.info("Result: "+ result);
```
