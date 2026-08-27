# @ohos.distributedsched.proxyChannelManager(代理通道管理)

###### 使用说明
 调用模块接口前，需要完成如下配置：
 1. 申请ohos.permission.ACCESS_BLUETOOTH权限。如何配置和申请权限，具体操作请参考[声明权限](../../../security/AccessToken/declare-permissions.md)和[向用户申请授权](../../../security/AccessToken/request-user-authorization.md)。
 2. 在module.json5文件中配置action字段"action.ohos.pull.listener"，用于需要被代理拉起的手机侧应用进程。
 典型调用流程：
 1. 调用openProxyChannel打开代理通道，获取channelId。
 2. 调用sendData发送数据，并根据业务需求订阅事件：调用on('receiveData')接收对端数据，调用on('channelStateChange')感知通道连接状态变化（断连、恢复等）。两者可同时订阅，建议在数据传输场景中同时使用，以便通道异常时及时暂停发送并处理断连恢复逻辑。
 3. 使用完毕后，调用off('receiveData')/off('channelStateChange')取消订阅。
 4. 调用closeProxyChannel关闭代理通道释放资源。


**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [closeProxyChannel(代理通道管理)](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md) | 关闭已打开的代理通道。适用于手机侧应用不再需要与穿戴设备侧应用通信的场景，例如完成数据同步任务后主动释放通道资源等。此方法必须与 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)配对使用，在使用完毕后调用此方法关闭通道以释放资源。关闭通道后，已注册的receiveData和 channelStateChange回调将自动取消订阅，正在传输的数据将中断。未及时关闭代理通道可能导致通道资源泄漏。 |
| [off(代理通道管理)](arkts-distributedservice-proxychannelmanager-off-f.md#offreceivedata) | 取消订阅数据接收事件，不再通过回调接收数据。适用于手机侧应用不再需要接收穿戴设备侧应用数据的场景，例如用户切换到其他功能模块等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 on('receiveData') 配对使用，用于取消之前通过on('receiveData')注册的数据接收回调。 |
| [off(代理通道管理)](arkts-distributedservice-proxychannelmanager-off-f.md#offchannelstatechange) | 取消订阅通道状态事件。适用于手机侧应用不再需要监听代理通道连接状态变化的场景，例如用户退出相关业务页面、完成数据传输流程后等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 on('channelStateChange') 配对使用，用于取消之前通过on('channelStateChange')注册的通道状态回调。 |
| [on(代理通道管理)](arkts-distributedservice-proxychannelmanager-on-f.md#onreceivedata) | 订阅数据接收事件，使用Callback异步回调。适用于手机侧应用需要持续接收穿戴设备侧应用上报数据的场景，例如接收穿戴设备侧应用数据等。代理模块基于openProxyChannel时配置的对端UUID接收对端数据，将接收到的穿戴设 备侧应用数据通过回调传递给订阅者。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅数据接收事件。若需代理唤醒手机侧应用进程 以接收和处理对端数据，使用前请在module.json5中配置action字段"action.ohos.pull.listener"。订阅后需调用 off('receiveData') 取消订阅，避免回调持续触发。 |
| [on(代理通道管理)](arkts-distributedservice-proxychannelmanager-on-f.md#onchannelstatechange) | 订阅通道状态事件，使用Callback异步回调。适用于手机侧应用需要实时感知代理通道连接状态的场景，例如监测通道断开后暂停数据发送、通道恢复后自动重试业务等。代理模块实时监控蓝牙BR链路状态变化，当发生连接恢复、异常断连、配对关系 删除等事件时通过回调上报ChannelStateInfo。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅通道状态事件。订 阅后需调用 off('channelStateChange') 取消订阅，避免回调持续触发。调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道后，已注册的channelStateChange回调将自动取消 订阅。 |
| [openProxyChannel(代理通道管理)](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md) | 打开代理通道，使用Promise异步回调。基于ChannelInfo中配置的链路类型和对端设备信息，通过蓝牙BR协议与对端设备协商建立双向数据通道，并返回唯一标识该通道的channelId。适用于手机侧应用需要与穿戴设备侧应用建立 双向数据通道的场景，例如消息通知转发等。调用此方法后，必须在不再使用代理通道时调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道以释放资源。 |
| [sendData(代理通道管理)](arkts-distributedservice-proxychannelmanager-senddata-f.md) | 向对端发送数据，使用Promise异步回调。适用于手机侧应用通过代理通道向穿戴设备侧应用发送指令或数据的场景，例如发送配置更新、通知消息等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能调用此方法发送数据。当代理通道处于不可用状态（如 [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md).CHANNEL_WAIT_RESUME、CHANNEL_EXCEPTION_SOFTWARE_FAILED、 CHANNEL_BR_NO_PAIRED）时，调用此方法将失败，建议订阅 on('channelStateChange') 事件监测通道状态，在通道不可用时暂停数据发送，通道恢复后继续发送。数据通过已建立的代理通道经蓝牙BR链路传输至对端设备，数据长度最大为4096字节，超出将返回错误码32390103。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChannelInfo(代理通道管理)](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | 打开代理通道函数的入参，包括代理通道的链路类型、对端设备的MAC地址和监听服务的UUID。 |
| [ChannelStateInfo(代理通道管理)](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md) | 当代理通道状态变化时，用于表示代理通道的连接状态。 |
| [DataInfo(代理通道管理)](arkts-distributedservice-proxychannelmanager-datainfo-i.md) | 存放接收的数据信息，包括通道ID和数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ChannelState(代理通道管理)](arkts-distributedservice-proxychannelmanager-channelstate-e.md) | 通道状态发生变化时，代理通道上报的通道连接状态。 |
| [LinkType(代理通道管理)](arkts-distributedservice-proxychannelmanager-linktype-e.md) | 链路类型。 |
