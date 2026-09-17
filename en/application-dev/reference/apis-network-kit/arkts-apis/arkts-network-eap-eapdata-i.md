# EapData

Defines the EAP data.

​

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## Modules to Import

```TypeScript
import { eap } from '@kit.NetworkKit';
```

## bufferLen

```TypeScript
bufferLen: number
```

Data length.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## eapBuffer

```TypeScript
eapBuffer: Uint8Array
```

Raw EAP data starting from the EAP header, which is not encrypted.

**Type:** Uint8Array

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap

## msgId

```TypeScript
msgId: number
```

Pseudo random number used to associate the EAP data before and after processing.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Eap
