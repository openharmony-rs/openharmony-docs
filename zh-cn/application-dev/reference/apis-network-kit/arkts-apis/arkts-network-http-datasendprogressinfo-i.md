# DataSendProgressInfo

数据发送信息。

**起始版本：** 11

<!--Device-http-export interface DataSendProgressInfo--><!--Device-http-export interface DataSendProgressInfo-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { http } from '@kit.NetworkKit';
```

## sendSize

```TypeScript
sendSize: int
```

每次发送的数据量(单位：Byte)。

**类型：** int

**起始版本：** 11

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DataSendProgressInfo-sendSize: int--><!--Device-DataSendProgressInfo-sendSize: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

## totalSize

```TypeScript
totalSize: int
```

总共要发送的数据量(单位：Byte)。

**类型：** int

**起始版本：** 11

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-DataSendProgressInfo-totalSize: int--><!--Device-DataSendProgressInfo-totalSize: int-End-->

**系统能力：** SystemCapability.Communication.NetStack

