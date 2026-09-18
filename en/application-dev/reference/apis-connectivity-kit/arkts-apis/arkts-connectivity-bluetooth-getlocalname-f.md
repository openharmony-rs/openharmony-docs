# getLocalName

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## getLocalName

```TypeScript
function getLocalName(): string
```

Obtains the Bluetooth local name of a device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getLocalName](arkts-connectivity-bluetoothmanager-getlocalname-f.md)

**Required permissions:** ohos.permission.USE_BLUETOOTH

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the name the device. |

**Examples**

```TypeScript
let localName : string = bluetooth.getLocalName();
```
