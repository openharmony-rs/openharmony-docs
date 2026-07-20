# @ohos.distributedsched.abilityConnectionManager

abilityConnectionManager模块提供了应用协同接口管理能力。设备组网成功（需登录同账号、双端打开蓝牙）后，系统应用和三方应用可以跨设备拉起同应用的一个[UIAbility](../../apis-ability-kit/arkts-apis/arkts-app-ability-uiability.md)，拉起并连接成功后可实现跨设备数据传输（文本信息）。

**起始版本：** 18

<!--Device-unnamed-declare namespace abilityConnectionManager--><!--Device-unnamed-declare namespace abilityConnectionManager-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acceptConnect](arkts-distributedservice-abilityconnectionmanager-acceptconnect-f.md#acceptconnect) | 设备B上的应用，在创建协同会话成功并获得会话ID后，调用acceptConnect()方法接受连接。使用Promise异步回调。 |
| [connect](arkts-distributedservice-abilityconnectionmanager-connect-f.md#connect) | 创建协同会话成功并获得会话ID后，设备A上可进行UIAbility的连接。使用Promise异步回调。 |
| [createAbilityConnectionSession](arkts-distributedservice-abilityconnectionmanager-createabilityconnectionsession-f.md#createabilityconnectionsession) | 创建应用间的协同会话。 |
| [destroyAbilityConnectionSession](arkts-distributedservice-abilityconnectionmanager-destroyabilityconnectionsession-f.md#destroyabilityconnectionsession) | 销毁应用间的协同会话。 |
| [disconnect](arkts-distributedservice-abilityconnectionmanager-disconnect-f.md#disconnect) | 当协同业务执行完毕后，协同双端的任意一台设备，应断开UIAbility的连接，结束协同状态。 |
| [getPeerInfoById](arkts-distributedservice-abilityconnectionmanager-getpeerinfobyid-f.md#getpeerinfobyid) | 获取指定会话中对端应用信息。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#off) | 取消connect事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#off-1) | 取消disconnect事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#off-2) | 取消receiveMessage事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#off-3) | 取消receiveData事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#on) | 注册connect事件的回调监听。使用callback异步回调。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#on-1) | 注册disconnect事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#on-2) | 注册receiveMessage事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#on-3) | 注册receiveData事件的回调监听。 |
| [reject](arkts-distributedservice-abilityconnectionmanager-reject-f.md#reject) | 在跨端应用协同过程中，在拒绝对端的连接请求后，向对端发送拒绝原因。 |
| [sendData](arkts-distributedservice-abilityconnectionmanager-senddata-f.md#senddata) | 应用连接成功后，设备A或设备B可向对端设备发送[ArrayBuffer](docroot://arkts-utils/arraybuffer-object.md)字节流。 |
| [sendMessage](arkts-distributedservice-abilityconnectionmanager-sendmessage-f.md#sendmessage) | 应用连接成功后，设备A或设备B可向对端设备发送文本信息。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createStream](arkts-distributedservice-abilityconnectionmanager-createstream-f-sys.md#createstream) | Creating a Stream. |
| [destroyStream](arkts-distributedservice-abilityconnectionmanager-destroystream-f-sys.md#destroystream) | Destroy the Stream. |
| [getSurfaceId](arkts-distributedservice-abilityconnectionmanager-getsurfaceid-f-sys.md#getsurfaceid) | Obtains the transmission surface. |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f-sys.md#off-4) | Unregisters receiveImage event. |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f-sys.md#off-5) | Unregisters collaborateEvent event. |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f-sys.md#off-6) | Unregisters collaborateEvent event. |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f-sys.md#on-4) | Registers receiveImage event. |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f-sys.md#on-5) | Registers collaborateEvent event. |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f-sys.md#on-6) | Registers collaborateEvent event. |
| [sendImage](arkts-distributedservice-abilityconnectionmanager-sendimage-f-sys.md#sendimage) | Send image data. |
| [setSurfaceId](arkts-distributedservice-abilityconnectionmanager-setsurfaceid-f-sys.md#setsurfaceid) | Sets the transmission surface. |
| [startStream](arkts-distributedservice-abilityconnectionmanager-startstream-f-sys.md#startstream) | Start Streaming |
| [stopStream](arkts-distributedservice-abilityconnectionmanager-stopstream-f-sys.md#stopstream) | Stop Streaming |
| [updateSurfaceParam](arkts-distributedservice-abilityconnectionmanager-updatesurfaceparam-f-sys.md#updatesurfaceparam) | Update surface parameters. |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [CollaborateEventInfo](arkts-distributedservice-abilityconnectionmanager-collaborateeventinfo-i.md) | 协同事件信息。 |
| [ConnectOptions](arkts-distributedservice-abilityconnectionmanager-connectoptions-i.md) | 应用连接时所需的连接选项。 |
| [ConnectResult](arkts-distributedservice-abilityconnectionmanager-connectresult-i.md) | 连接的结果。 |
| [EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i.md) | 回调方法的接收信息。 |
| [PeerInfo](arkts-distributedservice-abilityconnectionmanager-peerinfo-i.md) | 应用协同信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ConnectOptions](arkts-distributedservice-abilityconnectionmanager-connectoptions-i-sys.md) | 应用连接时所需的连接选项。 |
| [EventCallbackInfo](arkts-distributedservice-abilityconnectionmanager-eventcallbackinfo-i-sys.md) | 回调方法的接收信息。 |
| [StreamParam](arkts-distributedservice-abilityconnectionmanager-streamparam-i-sys.md) | Streaming configuration parameters. |
| [SurfaceParam](arkts-distributedservice-abilityconnectionmanager-surfaceparam-i-sys.md) | Surface configuration parameters. |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CollaborateEventType](arkts-distributedservice-abilityconnectionmanager-collaborateeventtype-e.md) | 协同事件类型的枚举。 |
| [CollaborationKeys](arkts-distributedservice-abilityconnectionmanager-collaborationkeys-e.md) | 应用协作键值的枚举。 |
| [CollaborationValues](arkts-distributedservice-abilityconnectionmanager-collaborationvalues-e.md) | 应用协作键值的枚举。 |
| [ConnectErrorCode](arkts-distributedservice-abilityconnectionmanager-connecterrorcode-e.md) | 连接的错误码。 |
| [DisconnectReason](arkts-distributedservice-abilityconnectionmanager-disconnectreason-e.md) | 当前断连原因的枚举。 |
| [StartOptionParams](arkts-distributedservice-abilityconnectionmanager-startoptionparams-e.md) | 启动选项参数的枚举。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [FlipOptions](arkts-distributedservice-abilityconnectionmanager-flipoptions-e-sys.md) | Flip option. |
| [StartOptionParams](arkts-distributedservice-abilityconnectionmanager-startoptionparams-e-sys.md) | 启动选项参数的枚举。 |
| [StreamRole](arkts-distributedservice-abilityconnectionmanager-streamrole-e-sys.md) | Stream transmission role. |
| [VideoPixelFormat](arkts-distributedservice-abilityconnectionmanager-videopixelformat-e-sys.md) | Video pixelFormat Configuration Options. |
<!--DelEnd-->

