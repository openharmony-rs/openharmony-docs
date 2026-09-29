# CharacteristicWriteRequest

```TypeScript
interface CharacteristicWriteRequest
```

Describes the parameters of the of the Gatt client's characteristic write request.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [CharacteristicWriteRequest](arkts-connectivity-ble-characteristicwriterequest-i.md)

<!--Device-bluetoothManager-interface CharacteristicWriteRequest--><!--Device-bluetoothManager-interface CharacteristicWriteRequest-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a CharacteristicWriteRequest instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-characteristicwriterequest-i.md#characteristicuuid)

<!--Device-CharacteristicWriteRequest-characteristicUuid: string--><!--Device-CharacteristicWriteRequest-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the write request

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [deviceId](arkts-connectivity-ble-characteristicwriterequest-i.md#deviceid)

<!--Device-CharacteristicWriteRequest-deviceId: string--><!--Device-CharacteristicWriteRequest-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrep

```TypeScript
isPrep: boolean
```

Whether this request should be pending for later operation

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [isPrepared](arkts-connectivity-ble-characteristicwriterequest-i.md#isprepared)

<!--Device-CharacteristicWriteRequest-isPrep: boolean--><!--Device-CharacteristicWriteRequest-isPrep: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

Whether the remote client need a response

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [needRsp](arkts-connectivity-ble-characteristicwriterequest-i.md#needrsp)

<!--Device-CharacteristicWriteRequest-needRsp: boolean--><!--Device-CharacteristicWriteRequest-needRsp: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for writing characteristic value

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [offset](arkts-connectivity-ble-characteristicwriterequest-i.md#offset)

<!--Device-CharacteristicWriteRequest-offset: number--><!--Device-CharacteristicWriteRequest-offset: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the characteristic belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-characteristicwriterequest-i.md#serviceuuid)

<!--Device-CharacteristicWriteRequest-serviceUuid: string--><!--Device-CharacteristicWriteRequest-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [transId](arkts-connectivity-ble-characteristicwriterequest-i.md#transid)

<!--Device-CharacteristicWriteRequest-transId: number--><!--Device-CharacteristicWriteRequest-transId: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be written

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [value](arkts-connectivity-ble-characteristicwriterequest-i.md#value)

<!--Device-CharacteristicWriteRequest-value: ArrayBuffer--><!--Device-CharacteristicWriteRequest-value: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
