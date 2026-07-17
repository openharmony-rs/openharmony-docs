# DataInfo

存放接收的数据信息，包括通道Id和数据。

**起始版本：** 20

<!--Device-proxyChannelManager-interface DataInfo--><!--Device-proxyChannelManager-interface DataInfo-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## channelId

```TypeScript
channelId: number
```

代理通道的channelId。

**类型：** number

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataInfo-channelId: int--><!--Device-DataInfo-channelId: int-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## data

```TypeScript
data: ArrayBuffer
```

接收到的字节数据。

**类型：** ArrayBuffer

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataInfo-data: ArrayBuffer--><!--Device-DataInfo-data: ArrayBuffer-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

