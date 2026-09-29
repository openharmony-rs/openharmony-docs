# GattProperties

```TypeScript
interface GattProperties
```

Describes the properties of a gatt characteristic.

**Since:** 10

<!--Device-ble-interface GattProperties--><!--Device-ble-interface GattProperties-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## authenticatedSignedWrite

```TypeScript
authenticatedSignedWrite?: boolean
```

Support authenticated signed write property of the characteristic.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattProperties-authenticatedSignedWrite?: boolean--><!--Device-GattProperties-authenticatedSignedWrite?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## broadcast

```TypeScript
broadcast?: boolean
```

Support broadcast property of the characteristic.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattProperties-broadcast?: boolean--><!--Device-GattProperties-broadcast?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## extendedProperties

```TypeScript
extendedProperties?: boolean
```

Support extended properties property of the characteristic.

**Type:** boolean

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-GattProperties-extendedProperties?: boolean--><!--Device-GattProperties-extendedProperties?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## indicate

```TypeScript
indicate?: boolean
```

Support indicate property of the characteristic.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattProperties-indicate?: boolean--><!--Device-GattProperties-indicate?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## notify

```TypeScript
notify?: boolean
```

Support notify property of the characteristic.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattProperties-notify?: boolean--><!--Device-GattProperties-notify?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## read

```TypeScript
read?: boolean
```

Support read property of the characteristic.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattProperties-read?: boolean--><!--Device-GattProperties-read?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## write

```TypeScript
write?: boolean
```

Support write property of the characteristic.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattProperties-write?: boolean--><!--Device-GattProperties-write?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## writeNoResponse

```TypeScript
writeNoResponse?: boolean
```

Support write no response property of the characteristic.

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-GattProperties-writeNoResponse?: boolean--><!--Device-GattProperties-writeNoResponse?: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
