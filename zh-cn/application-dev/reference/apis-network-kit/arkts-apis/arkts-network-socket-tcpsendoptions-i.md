# TCPSendOptions

TCPSocket发送请求的参数。

**起始版本：** 7

<!--Device-socket-export interface TCPSendOptions--><!--Device-socket-export interface TCPSendOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## data

```TypeScript
data: string | ArrayBuffer
```

发送的数据。

**类型：** string \| ArrayBuffer

**起始版本：** 7

<!--Device-TCPSendOptions-data: string | ArrayBuffer--><!--Device-TCPSendOptions-data: string | ArrayBuffer-End-->

**系统能力：** SystemCapability.Communication.NetStack

## encoding

```TypeScript
encoding?: string
```

字符编码(UTF-8，UTF-16BE，UTF-16LE，UTF-16，US-ASCII，ISO-8859-1)，默认为UTF-8。

**类型：** string

**起始版本：** 7

<!--Device-TCPSendOptions-encoding?: string--><!--Device-TCPSendOptions-encoding?: string-End-->

**系统能力：** SystemCapability.Communication.NetStack

