# @ohos.distributedsched.proxyChannelManager

软总线具备常驻运行能力，可为跨设备通信提供稳定可靠的底层通道。本模块基于软总线进程开发，支持手机与穿戴设备间高效的数据互通，可为用户提供无缝的设备互联体验。使用场景：手机侧APP与手表侧APP协同时，当手机APP不在前台被使用，手机应用的下行消息经由通知服务器，通过代理模块发送给手表侧。模块核心功能包括：代理通道管理、数据路由管理、 应用状态感知和唤醒、链路状态监听。

- 代理通道管理：通过蓝牙 BR 协议建立手机与穿戴设备的双向数据通道，支持的数据通道 ID 范围是[1,2147483647] 。  
- 数据路由管理：基于 UUID 服务识别机制，精准转发穿戴设备数据。  
- 应用状态感知和唤醒：代理通道使能后，收到穿戴设备发送的数据后，动态分析和唤醒手机端对应应用进程。  
- 全链路状态监控：通过回调实时感知通道连接状态。

**起始版本：** 20

<!--Device-unnamed-declare namespace proxyChannelManager--><!--Device-unnamed-declare namespace proxyChannelManager-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md#closeproxychannel-1) | 关闭已打开的代理通道。 |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#off-1) | 取消订阅数据接收事件，停止接收数据。 |
| [off](arkts-distributedservice-proxychannelmanager-off-f.md#off-2) | 取消订阅通道状态事件。 |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#on-1) | 订阅数据接收事件，使用异步回调。 |
| [on](arkts-distributedservice-proxychannelmanager-on-f.md#on-2) | 订阅通道状态事件，使用callback进行异步回调。 |
| [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md#openproxychannel-1) | 打开代理通道，使用Promise异步回调返回结果。 |
| [sendData](arkts-distributedservice-proxychannelmanager-senddata-f.md#senddata-1) | 向对端发送数据，使用Promise异步回调。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | 打开代理通道函数的入参，包括对端设备的MAC地址和监听服务的UUID。 |
| [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | 当代理通道状态变化时，用于表示代理通道的连接状态。 |
| [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | 存放接收的数据信息，包括通道Id和数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | 通道状态发生变化时，代理通道上报的通道连接状态。 |
| [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md) | 链路类型。 |

