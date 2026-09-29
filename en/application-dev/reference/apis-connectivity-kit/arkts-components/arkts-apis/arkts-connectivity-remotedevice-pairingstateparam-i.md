# PairingStateParam

```TypeScript
interface PairingStateParam
```

Describes the pairing state parameters.

**Since:** 26.0.0

<!--Device-remoteDevice-interface PairingStateParam--><!--Device-remoteDevice-interface PairingStateParam-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## address

```TypeScript
address: string
```

Indicates the device address. The length must be 17, The value consists of hexadecimal digits and colons (:), for example, 11:22:33:AA:BB:FF.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PairingStateParam-address: string--><!--Device-PairingStateParam-address: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## preState

```TypeScript
preState: PairingState
```

Indicates the previous pairing state.

**Type:** [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PairingStateParam-preState: PairingState--><!--Device-PairingStateParam-preState: PairingState-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## reason

```TypeScript
reason: PairingReason
```

Indicates the pairing state reason.

**Type:** [PairingReason](arkts-connectivity-remotedevice-pairingreason-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PairingStateParam-reason: PairingReason--><!--Device-PairingStateParam-reason: PairingReason-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## reasonMsg

```TypeScript
reasonMsg?: string
```

Indicates reason message. This field is intended for log information only and should not be used for logic processing.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PairingStateParam-reasonMsg?: string--><!--Device-PairingStateParam-reasonMsg?: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## state

```TypeScript
state: PairingState
```

Indicates the current pairing state.

**Type:** [PairingState](arkts-connectivity-remotedevice-pairingstate-t.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PairingStateParam-state: PairingState--><!--Device-PairingStateParam-state: PairingState-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
