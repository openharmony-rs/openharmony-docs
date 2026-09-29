# ServiceData

```TypeScript
interface ServiceData
```

Describes the service data.

**Since:** 10

<!--Device-ble-interface ServiceData--><!--Device-ble-interface ServiceData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## serviceUuid

```TypeScript
serviceUuid: string
```

Indicates the UUID of the service data to add

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ServiceData-serviceUuid: string--><!--Device-ServiceData-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceValue

```TypeScript
serviceValue: ArrayBuffer
```

Indicates the service data to add

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ServiceData-serviceValue: ArrayBuffer--><!--Device-ServiceData-serviceValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
