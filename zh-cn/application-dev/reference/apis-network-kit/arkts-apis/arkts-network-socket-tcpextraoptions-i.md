# TCPExtraOptions

TCPSocket连接的其他属性。继承自[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)。

**继承/实现关系：** TCPExtraOptions extends [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)

**起始版本：** 7

<!--Device-socket-export interface TCPExtraOptions--><!--Device-socket-export interface TCPExtraOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## OOBInline

```TypeScript
OOBInline?: boolean
```

是否为OOB内联。默认为false。true：是OOB内联；false：不是OOB内联。

**类型：** boolean

**起始版本：** 7

<!--Device-TCPExtraOptions-OOBInline?: boolean--><!--Device-TCPExtraOptions-OOBInline?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## TCPNoDelay

```TypeScript
TCPNoDelay?: boolean
```

TCPSocket连接是否无时延。默认为false。true：无时延；false：有时延。

**类型：** boolean

**起始版本：** 7

<!--Device-TCPExtraOptions-TCPNoDelay?: boolean--><!--Device-TCPExtraOptions-TCPNoDelay?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## keepAlive

```TypeScript
keepAlive?: boolean
```

是否保持连接。默认为false。true：保持连接；false：断开连接。

**类型：** boolean

**起始版本：** 7

<!--Device-TCPExtraOptions-keepAlive?: boolean--><!--Device-TCPExtraOptions-keepAlive?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

## socketLinger

```TypeScript
socketLinger?: {on: boolean, linger: int}
```

socket是否继续逗留。 - on：是否逗留（true：逗留；false：不逗留）。 - linger：逗留时长，单位毫秒（ms），取值范围为0~65535。 当入参on设置为true时，才需要设置。

**类型：** {on: boolean, linger: int}

**起始版本：** 7

<!--Device-TCPExtraOptions-socketLinger?: {on: boolean, linger: int}--><!--Device-TCPExtraOptions-socketLinger?: {on: boolean, linger: int}-End-->

**系统能力：** SystemCapability.Communication.NetStack

## tcpFastOpen

```TypeScript
tcpFastOpen?: boolean
```

是否在TCPSocket连接中启用TCP快速打开（TCP Fast OPen， TFO），该功能允许客户端在首次握手时携带数据，从而减少连接建立的延迟，提升高频率短连接场景下的性能表现。默认为false。true：支持快速打开 属性；false：不支持快速打开属性。 当前参数只支持客户端配置。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TCPExtraOptions-tcpFastOpen?: boolean--><!--Device-TCPExtraOptions-tcpFastOpen?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

