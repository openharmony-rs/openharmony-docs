# AdvertiseData

Describes the advertising data.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## advertiseName

```TypeScript
advertiseName?: string
```

Indicates the local name data type in the advertisement packet. If both the property and [includeDeviceName](#includedevicename) property are used together, the [advertiseName](#advertisename) property will ultimately take effect.

**Type:** string

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_BLUETOOTH_ADVERTISER_NAME

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## includeDeviceName

```TypeScript
includeDeviceName?: boolean
```

Indicates whether the device name will be included in the advertisement packet.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## includeTxPower

```TypeScript
includeTxPower?: boolean
```

Indicates whether the tx power will be included in the advertisement packet.

**Type:** boolean

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## manufactureData

```TypeScript
manufactureData: Array<ManufactureData>
```

The specified manufacturer data list to this advertisement

**Type:** Array&lt;[ManufactureData](arkts-connectivity-ble-manufacturedata-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceData

```TypeScript
serviceData: Array<ServiceData>
```

The specified service data list to this advertisement

**Type:** Array&lt;[ServiceData](arkts-connectivity-ble-servicedata-i.md)&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuids

```TypeScript
serviceUuids: Array<string>
```

The specified service UUID list to this advertisement

**Type:** Array&lt;string&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.Bluetooth.Core
