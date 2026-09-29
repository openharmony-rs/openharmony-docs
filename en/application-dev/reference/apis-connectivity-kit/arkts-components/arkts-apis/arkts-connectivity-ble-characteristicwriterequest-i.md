# CharacteristicWriteRequest

```TypeScript
interface CharacteristicWriteRequest
```

Describes the parameters of the of the Gatt client's characteristic write request.

**Since:** 10

<!--Device-ble-interface CharacteristicWriteRequest--><!--Device-ble-interface CharacteristicWriteRequest-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { ble } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a CharacteristicWriteRequest instance

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-characteristicUuid: string--><!--Device-CharacteristicWriteRequest-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the write request

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-deviceId: string--><!--Device-CharacteristicWriteRequest-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrepared

```TypeScript
isPrepared: boolean
```

Whether this request should be pending for later operation

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-isPrepared: boolean--><!--Device-CharacteristicWriteRequest-isPrepared: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

Whether the remote client need a response

**Type:** boolean

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-needRsp: boolean--><!--Device-CharacteristicWriteRequest-needRsp: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for writing characteristic value

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-offset: int--><!--Device-CharacteristicWriteRequest-offset: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the characteristic belongs

**Type:** string

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-serviceUuid: string--><!--Device-CharacteristicWriteRequest-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-transId: int--><!--Device-CharacteristicWriteRequest-transId: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be written

**Type:** ArrayBuffer

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CharacteristicWriteRequest-value: ArrayBuffer--><!--Device-CharacteristicWriteRequest-value: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
