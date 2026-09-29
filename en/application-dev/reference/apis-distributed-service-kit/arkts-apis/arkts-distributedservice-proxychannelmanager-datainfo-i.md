# DataInfo

```TypeScript
interface DataInfo
```

Represents the received data information, including the channel ID and data.

**Since:** 20

<!--Device-proxyChannelManager-interface DataInfo--><!--Device-proxyChannelManager-interface DataInfo-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## Modules to Import

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## channelId

```TypeScript
channelId: number
```

Channel ID of the proxy channel. The value range is 1 to 2147483647.

**Type:** number

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataInfo-channelId: int--><!--Device-DataInfo-channelId: int-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration

## data

```TypeScript
data: ArrayBuffer
```

Received byte data. The maximum length is 4096 bytes.

**Type:** ArrayBuffer

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataInfo-data: ArrayBuffer--><!--Device-DataInfo-data: ArrayBuffer-End-->

**System capability:** SystemCapability.DistributedSched.AppCollaboration
