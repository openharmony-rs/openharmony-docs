# NetPortStatesInfo

系统当前监听的TCP、UDP端口信息。

**起始版本：** 24

<!--Device-connection-export interface NetPortStatesInfo--><!--Device-connection-export interface NetPortStatesInfo-End-->

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

<!--Device-NetPortStatesInfo-tcpPortStatesInfo?: Array<TcpNetPortStatesInfo>--><!--Device-NetPortStatesInfo-tcpPortStatesInfo?: Array<TcpNetPortStatesInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

## udpPortStatesInfo

```TypeScript
udpPortStatesInfo?: Array<UdpNetPortStatesInfo>
```

系统当前监听的UDP信息。

**类型：** Array&lt;[UdpNetPortStatesInfo](arkts-network-connection-udpnetportstatesinfo-i.md)&gt;

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetPortStatesInfo-udpPortStatesInfo?: Array<UdpNetPortStatesInfo>--><!--Device-NetPortStatesInfo-udpPortStatesInfo?: Array<UdpNetPortStatesInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

