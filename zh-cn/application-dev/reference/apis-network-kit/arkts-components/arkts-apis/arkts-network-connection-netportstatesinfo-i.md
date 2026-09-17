# NetPortStatesInfo

系统当前监听的TCP、UDP端口信息。

**起始版本：** 24

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## tcpPortStatesInfo

```TypeScript
tcpPortStatesInfo?: Array<TcpNetPortStatesInfo>
```

系统当前监听的TCP信息。

**类型：** Array&lt;[TcpNetPortStatesInfo](arkts-network-connection-tcpnetportstatesinfo-i.md)&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## udpPortStatesInfo

```TypeScript
udpPortStatesInfo?: Array<UdpNetPortStatesInfo>
```

系统当前监听的UDP信息。

**类型：** Array&lt;[UdpNetPortStatesInfo](arkts-network-connection-udpnetportstatesinfo-i.md)&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
