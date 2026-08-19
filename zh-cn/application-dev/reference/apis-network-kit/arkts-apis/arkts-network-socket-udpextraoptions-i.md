# UDPExtraOptions

UDPSocket连接的其他属性。继承自[ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)。

**继承/实现关系：** UDPExtraOptions extends [ExtraOptionsBase](arkts-network-socket-extraoptionsbase-i.md)

**起始版本：** 7

<!--Device-socket-export interface UDPExtraOptions--><!--Device-socket-export interface UDPExtraOptions-End-->

**系统能力：** SystemCapability.Communication.NetStack

## 导入模块

```TypeScript
import { socket } from '@kit.NetworkKit';
```

## broadcast

```TypeScript
broadcast?: boolean
```

是否可以发送广播。true表示可发送广播，false表示不可发送广播。默认为false。

**类型：** boolean

**起始版本：** 7

<!--Device-UDPExtraOptions-broadcast?: boolean--><!--Device-UDPExtraOptions-broadcast?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetStack

