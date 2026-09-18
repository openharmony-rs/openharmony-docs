# createBleScanner

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## createBleScanner

```TypeScript
function createBleScanner(): BleScanner
```

Create a ble scanner instance. Each ble scanner instance can be independently started or stopped.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.Communication.Bluetooth.Core

**Return value:**

| Type | Description |
| --- | --- |
| [BleScanner](arkts-connectivity-ble-blescanner-i.md) | Returns the promise object. |

**Examples**

```TypeScript
import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
import { ble } from '@kit.ConnectivityKit';
let bleScanner: ble.BleScanner = ble.createBleScanner();
console.info('create bleScanner success');
```
