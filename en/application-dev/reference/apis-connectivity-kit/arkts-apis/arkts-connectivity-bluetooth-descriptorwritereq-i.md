# DescriptorWriteReq

```TypeScript
interface DescriptorWriteReq
```

Describes the parameters of the Gatt client's characteristic write request.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [DescriptorWriteRequest](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md)

<!--Device-bluetooth-interface DescriptorWriteReq--><!--Device-bluetooth-interface DescriptorWriteReq-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of the characteristic to which the descriptor belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [characteristicUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#characteristicuuid)

<!--Device-DescriptorWriteReq-characteristicUuid: string--><!--Device-DescriptorWriteReq-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## descriptorUuid

```TypeScript
descriptorUuid: string
```

The UUID of a DescriptorWriteReq instance

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [descriptorUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#descriptoruuid)

<!--Device-DescriptorWriteReq-descriptorUuid: string--><!--Device-DescriptorWriteReq-descriptorUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the write request

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#deviceid)

<!--Device-DescriptorWriteReq-deviceId: string--><!--Device-DescriptorWriteReq-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## isPrep

```TypeScript
isPrep: boolean
```

Whether this request should be pending for later operation

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isPrep](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#isprep)

<!--Device-DescriptorWriteReq-isPrep: boolean--><!--Device-DescriptorWriteReq-isPrep: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## needRsp

```TypeScript
needRsp: boolean
```

Whether the remote client need a response

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [needRsp](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#needrsp)

<!--Device-DescriptorWriteReq-needRsp: boolean--><!--Device-DescriptorWriteReq-needRsp: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for writing characteristic value

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [offset](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#offset)

<!--Device-DescriptorWriteReq-offset: number--><!--Device-DescriptorWriteReq-offset: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the descriptor belongs

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [serviceUuid](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#serviceuuid)

<!--Device-DescriptorWriteReq-serviceUuid: string--><!--Device-DescriptorWriteReq-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [transId](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#transid)

<!--Device-DescriptorWriteReq-transId: number--><!--Device-DescriptorWriteReq-transId: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be written

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [value](arkts-connectivity-bluetoothmanager-descriptorwriterequest-i.md#value)

<!--Device-DescriptorWriteReq-value: ArrayBuffer--><!--Device-DescriptorWriteReq-value: ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
