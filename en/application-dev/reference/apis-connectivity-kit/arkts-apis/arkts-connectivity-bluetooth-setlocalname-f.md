# setLocalName

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## setLocalName

```TypeScript
function setLocalName(name: string): boolean
```

Sets the Bluetooth friendly name of a device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setLocalName](arkts-connectivity-bluetoothmanager-setlocalname-f.md)

**Required permissions:** ohos.permission.DISCOVER_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Indicates a valid Bluetooth name. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the Bluetooth name is set successfully; returns `false` otherwise. |

**Examples**

```TypeScript
let ret : boolean = bluetooth.setLocalName('device_name');
```
