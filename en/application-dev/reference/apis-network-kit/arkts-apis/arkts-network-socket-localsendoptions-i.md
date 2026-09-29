# LocalSendOptions

```TypeScript
export interface LocalSendOptions
```

Defines the request parameters for the **LocalSocket** object.

**Since:** 11

<!--Device-socket-export interface LocalSendOptions--><!--Device-socket-export interface LocalSendOptions-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## data

```TypeScript
data: string | ArrayBuffer
```

Data to be transmitted.

**Type:** string &#124; ArrayBuffer

**Since:** 11

<!--Device-LocalSendOptions-data: string | ArrayBuffer--><!--Device-LocalSendOptions-data: string | ArrayBuffer-End-->

**System capability:** SystemCapability.Communication.NetStack

## encoding

```TypeScript
encoding?: string
```

Encoding format of the string.

**Type:** string

**Since:** 11

<!--Device-LocalSendOptions-encoding?: string--><!--Device-LocalSendOptions-encoding?: string-End-->

**System capability:** SystemCapability.Communication.NetStack
