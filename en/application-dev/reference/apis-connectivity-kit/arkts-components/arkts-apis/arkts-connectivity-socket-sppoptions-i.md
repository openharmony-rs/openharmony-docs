# SppOptions

```TypeScript
interface SppOptions
```

Describes the spp parameters.

**Since:** 10

<!--Device-socket-interface SppOptions--><!--Device-socket-interface SppOptions-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { socket } from '@kit.ConnectivityKit';
```

## psm

```TypeScript
psm?: number
```

l2cap protocol service multiplexer

**Type:** number

**Since:** 20

<!--Device-SppOptions-psm?: int--><!--Device-SppOptions-psm?: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## secure

```TypeScript
secure: boolean
```

Indicates secure channel or not

**Type:** boolean

**Since:** 10

<!--Device-SppOptions-secure: boolean--><!--Device-SppOptions-secure: boolean-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## type

```TypeScript
type: SppType
```

Spp link type

**Type:** [SppType](arkts-connectivity-socket-spptype-e.md)

**Since:** 10

<!--Device-SppOptions-type: SppType--><!--Device-SppOptions-type: SppType-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## uuid

```TypeScript
uuid: string
```

Indicates the UUID in the SDP record.

**Type:** string

**Since:** 10

<!--Device-SppOptions-uuid: string--><!--Device-SppOptions-uuid: string-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
