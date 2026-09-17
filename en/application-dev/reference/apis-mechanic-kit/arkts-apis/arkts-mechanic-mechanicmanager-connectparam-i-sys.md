# ConnectParam (System API)

Definition of connect parameter.

**Since:** 26.0.0

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { mechanicManager } from '@kit.MechanicKit';
```

## custdata

```TypeScript
custdata: string
```

Data carried during device discovery Data must be in the following format:|type|value|type|value|.. value'len for each specific type is predefined length The following table lists the supported types and versions. ----------------------------------------------------------------- type | value | value len |api level ----------------------------------------------------------------- 0x01 | 3-axis gravity sensor value | 3Byte |26.0.0 ----------------------------------------------------------------- 0x02 | 1st byte offset of the MAC address | 1Byte |26.0.0 ----------------------------------------------------------------- 0x03 | Pairing broadcast | 1Byte |26.0.0 ----------------------------------------------------------------- 0x04 | Target device identifer | 4Byte |26.0.0 -----------------------------------------------------------------.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## deviceName

```TypeScript
deviceName?: string
```

Name of the mechanical device.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.

## identifier

```TypeScript
identifier?: number
```

Identifer of current device. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Mechanic.Core

**System API:** This is a system API.
