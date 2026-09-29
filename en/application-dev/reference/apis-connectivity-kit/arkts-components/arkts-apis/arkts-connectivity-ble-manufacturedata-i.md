# ManufactureData

```TypeScript
interface ManufactureData
```

Describes the manufacturer data.

**Since:** 10

<!--Device-ble-interface ManufactureData--><!--Device-ble-interface ManufactureData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## manufactureId

```TypeScript
manufactureId: number
```

Indicates the manufacturer ID assigned by Bluetooth SIG

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ManufactureData-manufactureId: int--><!--Device-ManufactureData-manufactureId: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufactureValue

```TypeScript
manufactureValue: ArrayBuffer
```

Indicates the manufacturer data to add

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ManufactureData-manufactureValue: ArrayBuffer--><!--Device-ManufactureData-manufactureValue: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
