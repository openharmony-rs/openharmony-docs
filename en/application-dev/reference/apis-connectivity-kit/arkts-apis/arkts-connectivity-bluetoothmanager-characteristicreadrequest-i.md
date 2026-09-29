# CharacteristicReadRequest

```TypeScript
interface CharacteristicReadRequest
```

Describes the parameters of the Gatt client's characteristic read request.

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [CharacteristicReadRequest](arkts-connectivity-ble-characteristicreadrequest-i.md)

<!--Device-bluetoothManager-interface CharacteristicReadRequest--><!--Device-bluetoothManager-interface CharacteristicReadRequest-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.ConnectivityKit';
```

## characteristicUuid

```TypeScript
characteristicUuid: string
```

The UUID of a CharacteristicReadRequest instance

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [characteristicUuid](arkts-connectivity-ble-characteristicreadrequest-i.md#characteristicuuid)

<!--Device-CharacteristicReadRequest-characteristicUuid: string--><!--Device-CharacteristicReadRequest-characteristicUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client that initiates the read request

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [deviceId](arkts-connectivity-ble-characteristicreadrequest-i.md#deviceid)

<!--Device-CharacteristicReadRequest-deviceId: string--><!--Device-CharacteristicReadRequest-deviceId: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for reading characteristic value

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [offset](arkts-connectivity-ble-characteristicreadrequest-i.md#offset)

<!--Device-CharacteristicReadRequest-offset: number--><!--Device-CharacteristicReadRequest-offset: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## serviceUuid

```TypeScript
serviceUuid: string
```

The UUID of the service to which the characteristic belongs

**Type:** string

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [serviceUuid](arkts-connectivity-ble-characteristicreadrequest-i.md#serviceuuid)

<!--Device-CharacteristicReadRequest-serviceUuid: string--><!--Device-CharacteristicReadRequest-serviceUuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the read request

**Type:** number

**Since:** 9

**Deprecated since:** 10

**Substitutes:** [transId](arkts-connectivity-ble-characteristicreadrequest-i.md#transid)

<!--Device-CharacteristicReadRequest-transId: number--><!--Device-CharacteristicReadRequest-transId: number-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
