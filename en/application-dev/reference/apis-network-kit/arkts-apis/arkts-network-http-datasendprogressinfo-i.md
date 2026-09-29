# DataSendProgressInfo

```TypeScript
export interface DataSendProgressInfo
```

Defines the data sending progress information.

**Since:** 11

<!--Device-http-export interface DataSendProgressInfo--><!--Device-http-export interface DataSendProgressInfo-End-->

**System capability:** SystemCapability.Communication.NetStack

## Modules to Import

```TypeScript
import { http } from '@kit.NetworkKit';
```

## sendSize

```TypeScript
sendSize: number
```

Amount of data to be sent each time, in bytes.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-DataSendProgressInfo-sendSize: int--><!--Device-DataSendProgressInfo-sendSize: int-End-->

**System capability:** SystemCapability.Communication.NetStack

## totalSize

```TypeScript
totalSize: number
```

Amount of data to be sent, in bytes.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 15.

<!--Device-DataSendProgressInfo-totalSize: int--><!--Device-DataSendProgressInfo-totalSize: int-End-->

**System capability:** SystemCapability.Communication.NetStack
