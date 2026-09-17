# ServerResponse

Describes the parameters of a response send by the server to a specified read or write request.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [ServerResponse](arkts-connectivity-bluetoothmanager-serverresponse-i.md)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { bluetooth } from '@kit.ConnectivityKit';
```

## deviceId

```TypeScript
deviceId: string
```

Indicates the address of the client to which to send the response

**Type:** string

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [deviceId](arkts-connectivity-bluetoothmanager-serverresponse-i.md#deviceid)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## offset

```TypeScript
offset: number
```

Indicates the byte offset of the start position for reading or writing operation

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [offset](arkts-connectivity-bluetoothmanager-serverresponse-i.md#offset)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## status

```TypeScript
status: number
```

Indicates the status of the read or write request, set this parameter to '0' in normal cases

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [status](arkts-connectivity-bluetoothmanager-serverresponse-i.md#status)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## transId

```TypeScript
transId: number
```

The Id of the write request

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [transId](arkts-connectivity-bluetoothmanager-serverresponse-i.md#transid)

**System capability:** SystemCapability.Communication.Bluetooth.Core

## value

```TypeScript
value: ArrayBuffer
```

Indicates the value to be sent

**Type:** ArrayBuffer

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [value](arkts-connectivity-bluetoothmanager-serverresponse-i.md#value)

**System capability:** SystemCapability.Communication.Bluetooth.Core
