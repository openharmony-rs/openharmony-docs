# AdvertisingEnableParams

```TypeScript
interface AdvertisingEnableParams
```

Parameter for dynamically enable advertising.

**Since:** 11

<!--Device-ble-interface AdvertisingEnableParams--><!--Device-ble-interface AdvertisingEnableParams-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertisingId

```TypeScript
advertisingId: number
```

Indicates the ID of current advertising.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingEnableParams-advertisingId: int--><!--Device-AdvertisingEnableParams-advertisingId: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## duration

```TypeScript
duration?: number
```

Indicates the duration for advertising continuously. The duration, in 10ms unit. Valid range is from 1 (10ms) to 65535 (655,350 ms). If this parameter is not specified or is set to 0, advertise is continuously sent.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingEnableParams-duration?: int--><!--Device-AdvertisingEnableParams-duration?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
