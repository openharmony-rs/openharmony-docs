# CharacteristicWriteReq

```TypeScript
interface CharacteristicWriteReq
```

Describes the parameters of the of the Gatt client's characteristic write request.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [CharacteristicWriteRequest](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md)

<!--Device-bluetooth-interface CharacteristicWriteReq--><!--Device-bluetooth-interface CharacteristicWriteReq-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a CharacteristicWriteReq instance

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristicUuid](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#characteristicuuid)

<!--Device-CharacteristicWriteReq-characteristicUuid: string--><!--Device-CharacteristicWriteReq-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the write request

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#deviceid)

<!--Device-CharacteristicWriteReq-deviceId: string--><!--Device-CharacteristicWriteReq-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrep

```TypeScript
isPrep: boolean
```

Whether this request should be pending for later operation

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isPrep](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#isprep)

<!--Device-CharacteristicWriteReq-isPrep: boolean--><!--Device-CharacteristicWriteReq-isPrep: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

Whether the remote client need a response

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [needRsp](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#needrsp)

<!--Device-CharacteristicWriteReq-needRsp: boolean--><!--Device-CharacteristicWriteReq-needRsp: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for writing characteristic value

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [offset](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#offset)

<!--Device-CharacteristicWriteReq-offset: number--><!--Device-CharacteristicWriteReq-offset: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the characteristic belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [serviceUuid](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#serviceuuid)

<!--Device-CharacteristicWriteReq-serviceUuid: string--><!--Device-CharacteristicWriteReq-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [transId](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#transid)

<!--Device-CharacteristicWriteReq-transId: number--><!--Device-CharacteristicWriteReq-transId: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be written

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [value](arkts-connectivity-bluetoothmanager-characteristicwriterequest-i.md#value)

<!--Device-CharacteristicWriteReq-value: ArrayBuffer--><!--Device-CharacteristicWriteReq-value: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
