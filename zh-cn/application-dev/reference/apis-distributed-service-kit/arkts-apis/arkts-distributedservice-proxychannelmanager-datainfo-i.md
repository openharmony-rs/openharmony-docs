# DataInfo

存放接收的数据信息，包括通道ID和数据。

**起始版本：** 23

<!--Device-proxyChannelManager-interface DataInfo--><!--Device-proxyChannelManager-interface DataInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## channelId

```TypeScript
channelId: int
```

代理通道的channelId，取值范围为1~2147483647。

**类型：** int

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataInfo-channelId: int--><!--Device-DataInfo-channelId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## data

```TypeScript
data: ArrayBuffer
```

接收到的字节数据，长度最大为4096字节。

**类型：** ArrayBuffer

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataInfo-data: ArrayBuffer--><!--Device-DataInfo-data: ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

