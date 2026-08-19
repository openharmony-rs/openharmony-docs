# @ohos.distributedsched.proxyChannelManager

软总线具备常驻运行能力，可为跨设备通信提供稳定可靠的底层通道。本模块基于软总线进程开发，支持手机与穿戴设备间的数据互通，可为用户提供无缝的设备互联体验，同时降低开发者跨设备通信的实现复杂度，无需自行处理底层通信协议和进程唤醒逻辑。使用 场景：手机侧应用与穿戴设备侧应用协同时，当手机侧应用不在前台时，手机侧应用的下行消息经由通知服务器，通过代理模块发送给穿戴设备侧；当穿戴设备向手机发送数据时，代理模块可动态唤醒手机侧对应应用进程以接收和处理数据。模块核心功能包括：代理 通道管理、数据路由管理、应用状态感知和唤醒、全链路状态监控。 - 代理通道管理：通过蓝牙 BR 协议建立手机与穿戴设备的双向数据通道，确保跨设备间可靠的双向数据通信，无需开发者自行实现底层通信协议。支持的数据通道ID范围是1~2147483647。 - 数据路由管理：基于 UUID 服务识别机制转发穿戴设备侧应用数据，实现数据的精准路由至目标服务端口，避免数据丢失或错发。UUID用于唯一标识对端设备上监听的服务，代理模块根据对端设备的UUID将数据路由至对应服务端口。 - 应用状态感知和唤醒：代理通道使能并收到穿戴设备侧应用数据后，代理模块根据module.json5中配置的action字段（如'action.ohos.pull.listener'）识别目标应用，并代理拉起对应手机侧应用进程以处理数 据，无需应用常驻前台即可接收数据，节省系统资源。 - 全链路状态监控：通过回调实时感知代理通道全生命周期的连接状态变化，帮助手机侧应用及时响应连接异常并调整业务策略，提升数据传输可靠性。包括连接恢复、异常断连、配对关系删除等事件。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

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
| [closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) | 关闭已打开的代理通道。适用于手机侧应用不再需要与穿戴设备侧应用通信的场景，例如完成数据同步任务后主动释放通道资源等。此方法必须与 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)配对使用，在使用完毕后调用此方法关闭通道以释放资源。关闭通道后，已注册的receiveData和 channelStateChange回调将自动取消订阅，正在传输的数据将中断。未及时关闭代理通道可能导致通道资源泄漏。 |
| [offChannelStateChange](arkts-distributedservice-proxychannelmanager-offchannelstatechange-f.md) | 取消订阅通道状态事件。适用于手机侧应用不再需要监听代理通道连接状态变化的场景，例如用户退出相关业务页面、完成数据传输流程后等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 配对使用，用于取消之前通过on('channelStateChange')注册的通道状态回调。 |
| [offReceiveData](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) | 取消订阅数据接收事件，不再通过回调接收数据。适用于手机侧应用不再需要接收穿戴设备侧应用数据的场景，例如用户切换到其他功能模块等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 [on('receiveData')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 配对使用，用于取消之前通过on('receiveData')注册的数据接收回调。 |
| [off_channelStateChange](arkts-distributedservice-proxychannelmanager-offchannelstatechange-f.md) | 取消订阅通道状态事件。适用于手机侧应用不再需要监听代理通道连接状态变化的场景，例如用户退出相关业务页面、完成数据传输流程后等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 配对使用，用于取消之前通过on('channelStateChange')注册的通道状态回调。 |
| [off_receiveData](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) | 取消订阅数据接收事件，不再通过回调接收数据。适用于手机侧应用不再需要接收穿戴设备侧应用数据的场景，例如用户切换到其他功能模块等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 [on('receiveData')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 配对使用，用于取消之前通过on('receiveData')注册的数据接收回调。 |
| [onChannelStateChange](arkts-distributedservice-proxychannelmanager-onchannelstatechange-f.md) | 订阅通道状态事件，使用Callback异步回调。适用于手机侧应用需要实时感知代理通道连接状态的场景，例如监测通道断开后暂停数据发送、通道恢复后自动重试业务等。代理模块实时监控蓝牙BR链路状态变化，当发生连接恢复、异常断连、配对关系 删除等事件时通过回调上报ChannelStateInfo。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅通道状态事件。订 阅后需调用 [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) 取消订阅，避免回调持续触发。调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道后，已注册的channelStateChange回调将自动取消 订阅。 |
| [onReceiveData](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) | 订阅数据接收事件，使用Callback异步回调。适用于手机侧应用需要持续接收穿戴设备侧应用上报数据的场景，例如接收穿戴设备侧应用数据等。代理模块基于openProxyChannel时配置的对端UUID接收对端数据，将接收到的穿戴设 备侧应用数据通过回调传递给订阅者。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅数据接收事件。若需代理唤醒手机侧应用进程 以接收和处理对端数据，使用前请在module.json5中配置action字段"action.ohos.pull.listener"。订阅后需调用 [off('receiveData')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) 取消订阅，避免回调持续触发。 |
| [on_channelStateChange](arkts-distributedservice-proxychannelmanager-onchannelstatechange-f.md) | 订阅通道状态事件，使用Callback异步回调。适用于手机侧应用需要实时感知代理通道连接状态的场景，例如监测通道断开后暂停数据发送、通道恢复后自动重试业务等。代理模块实时监控蓝牙BR链路状态变化，当发生连接恢复、异常断连、配对关系 删除等事件时通过回调上报ChannelStateInfo。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅通道状态事件。订 阅后需调用 [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) 取消订阅，避免回调持续触发。调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道后，已注册的channelStateChange回调将自动取消 订阅。 |
| [on_receiveData](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) | 订阅数据接收事件，使用Callback异步回调。适用于手机侧应用需要持续接收穿戴设备侧应用上报数据的场景，例如接收穿戴设备侧应用数据等。代理模块基于openProxyChannel时配置的对端UUID接收对端数据，将接收到的穿戴设 备侧应用数据通过回调传递给订阅者。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅数据接收事件。若需代理唤醒手机侧应用进程 以接收和处理对端数据，使用前请在module.json5中配置action字段"action.ohos.pull.listener"。订阅后需调用 [off('receiveData')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) 取消订阅，避免回调持续触发。 |
| [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) | 打开代理通道，使用Promise异步回调。基于ChannelInfo中配置的链路类型和对端设备信息，通过蓝牙BR协议与对端设备协商建立双向数据通道，并返回唯一标识该通道的channelId。适用于手机侧应用需要与穿戴设备侧应用建立 双向数据通道的场景，例如消息通知转发等。调用此方法后，必须在不再使用代理通道时调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道以释放资源。 |
| [sendData](arkts-distributedservice-proxychannelmanager-senddata-f.md) | 向对端发送数据，使用Promise异步回调。适用于手机侧应用通过代理通道向穿戴设备侧应用发送指令或数据的场景，例如发送配置更新、通知消息等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能调用此方法发送数据。当代理通道处于不可用状态（如 [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md).CHANNEL_WAIT_RESUME、CHANNEL_EXCEPTION_SOFTWARE_FAILED、 CHANNEL_BR_NO_PAIRED）时，调用此方法将失败，建议订阅 [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 事件监测通道状态，在通道不可用时暂停数据发送，通道恢复后继续发送。数据通过已建立的代理通道经蓝牙BR链路传输至对端设备，数据长度最大为4096字节，超出将返回错误码32390103。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | 打开代理通道函数的入参，包括代理通道的链路类型、对端设备的MAC地址和监听服务的UUID。 |
| [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | 当代理通道状态变化时，用于表示代理通道的连接状态。 |
| [DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | 存放接收的数据信息，包括通道ID和数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | 通道状态发生变化时，代理通道上报的通道连接状态。 |
| [LinkType](arkts-distributedservice-proxychannelmanager-linktype-e.md) | 链路类型。 |

