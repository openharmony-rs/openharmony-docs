# DescriptorWriteRequest

```TypeScript
interface DescriptorWriteRequest
```

Describes the parameters of the Gatt client's characteristic write request.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [DescriptorWriteRequest](arkts-connectivity-ble-descriptorwriterequest-i.md)

<!--Device-bluetoothManager-interface DescriptorWriteRequest--><!--Device-bluetoothManager-interface DescriptorWriteRequest-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of the characteristic to which the descriptor belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-descriptorwriterequest-i.md#characteristicuuid)

<!--Device-DescriptorWriteRequest-characteristicUuid: string--><!--Device-DescriptorWriteRequest-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

The UUID of a DescriptorWriteRequest instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [descriptorUuid](arkts-connectivity-ble-descriptorwriterequest-i.md#descriptoruuid)

<!--Device-DescriptorWriteRequest-descriptorUuid: string--><!--Device-DescriptorWriteRequest-descriptorUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the write request

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [deviceId](arkts-connectivity-ble-descriptorwriterequest-i.md#deviceid)

<!--Device-DescriptorWriteRequest-deviceId: string--><!--Device-DescriptorWriteRequest-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrep

```TypeScript
isPrep: boolean
```

Whether this request should be pending for later operation

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [isPrepared](arkts-connectivity-ble-descriptorwriterequest-i.md#isprepared)

<!--Device-DescriptorWriteRequest-isPrep: boolean--><!--Device-DescriptorWriteRequest-isPrep: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

Whether the remote client need a response

**Type:** boolean

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [needRsp](arkts-connectivity-ble-descriptorwriterequest-i.md#needrsp)

<!--Device-DescriptorWriteRequest-needRsp: boolean--><!--Device-DescriptorWriteRequest-needRsp: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for writing characteristic value

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [offset](arkts-connectivity-ble-descriptorwriterequest-i.md#offset)

<!--Device-DescriptorWriteRequest-offset: number--><!--Device-DescriptorWriteRequest-offset: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the descriptor belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-descriptorwriterequest-i.md#serviceuuid)

<!--Device-DescriptorWriteRequest-serviceUuid: string--><!--Device-DescriptorWriteRequest-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [transId](arkts-connectivity-ble-descriptorwriterequest-i.md#transid)

<!--Device-DescriptorWriteRequest-transId: number--><!--Device-DescriptorWriteRequest-transId: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be written

**Type:** ArrayBuffer

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [value](arkts-connectivity-ble-descriptorwriterequest-i.md#value)

<!--Device-DescriptorWriteRequest-value: ArrayBuffer--><!--Device-DescriptorWriteRequest-value: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
