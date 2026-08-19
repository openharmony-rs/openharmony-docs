# NetBlockStatusInfo

获取网络状态信息。

**起始版本：** 23

<!--Device-connection-export interface NetBlockStatusInfo--><!--Device-connection-export interface NetBlockStatusInfo-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## blocked

```TypeScript
blocked: boolean
```

标识当前网络是否是堵塞状态。true：标识当前网络是堵塞状态；false：标识当前网络不是堵塞状态。

**类型：** boolean

**起始版本：** 23

<!--Device-NetBlockStatusInfo-blocked: boolean--><!--Device-NetBlockStatusInfo-blocked: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## netHandle

```TypeScript
netHandle: NetHandle
```

网络句柄。

**类型：** NetHandle

**起始版本：** 23

<!--Device-NetBlockStatusInfo-netHandle: NetHandle--><!--Device-NetBlockStatusInfo-netHandle: NetHandle-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

