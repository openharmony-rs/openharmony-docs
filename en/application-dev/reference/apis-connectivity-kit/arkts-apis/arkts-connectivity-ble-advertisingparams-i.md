# AdvertisingParams

```TypeScript
interface AdvertisingParams
```

Describes the advertising parameters.

**Since:** 11

<!--Device-ble-interface AdvertisingParams--><!--Device-ble-interface AdvertisingParams-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertisingData

```TypeScript
advertisingData: AdvertiseData
```

Indicates the advertising data.

**Type:** [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingParams-advertisingData: AdvertiseData--><!--Device-AdvertisingParams-advertisingData: AdvertiseData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## advertisingResponse

```TypeScript
advertisingResponse?: AdvertiseData
```

Indicates the advertising response.

**Type:** [AdvertiseData](arkts-connectivity-ble-advertisedata-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingParams-advertisingResponse?: AdvertiseData--><!--Device-AdvertisingParams-advertisingResponse?: AdvertiseData-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## advertisingSettings

```TypeScript
advertisingSettings: AdvertiseSetting
```

Indicates the advertising settings.

**Type:** [AdvertiseSetting](arkts-connectivity-ble-advertisesetting-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingParams-advertisingSettings: AdvertiseSetting--><!--Device-AdvertisingParams-advertisingSettings: AdvertiseSetting-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## duration

```TypeScript
duration?: number
```

Indicates the duration for advertising continuously. The duration, in 10ms unit. Valid range is from 1 (10ms) to 65535 (655,350 ms). If this parameter is not specified or is set to 0, advertisement is continuously sent.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-AdvertisingParams-duration?: int--><!--Device-AdvertisingParams-duration?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
