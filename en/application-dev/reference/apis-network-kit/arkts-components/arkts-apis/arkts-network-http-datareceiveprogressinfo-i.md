# DataReceiveProgressInfo

```TypeScript
export interface DataReceiveProgressInfo
```

Defines the data receiving progress information.

**Since:** 11

<!--Device-http-export interface DataReceiveProgressInfo--><!--Device-http-export interface DataReceiveProgressInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## receiveSize

```TypeScript
receiveSize: number
```

Amount of data that has been received, in bytes.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-DataReceiveProgressInfo-receiveSize: int--><!--Device-DataReceiveProgressInfo-receiveSize: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalSize

```TypeScript
totalSize: number
```

Amount of data to be received, in bytes.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-DataReceiveProgressInfo-totalSize: int--><!--Device-DataReceiveProgressInfo-totalSize: int-End-->

**System capability:** SystemCapability.Communication.NetStack
