# TCPSendOptions

TCPSocket发送请求的参数。

**起始版本：** 7

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

**系统能力：** SystemCapability.Communication.NetStack

## encoding

```TypeScript
encoding?: string
```

字符编码(UTF-8，UTF-16BE，UTF-16LE，UTF-16，US-ASCII，ISO-8859-1)，默认为UTF-8。

**类型：** string

**起始版本：** 7

**系统能力：** SystemCapability.Communication.NetStack
