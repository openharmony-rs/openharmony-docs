# @ohos.distributedsched.abilityConnectionManager

abilityConnectionManager模块提供了应用协同接口管理能力。设备组网成功（需登录同账号、双端打开蓝牙）后， 系统应用和三方应用可以跨设备拉起同应用的一个[UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md)， 拉起并连接成功后可实现跨设备数据传输（文本信息）。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [acceptConnect](arkts-distributedservice-abilityconnectionmanager-acceptconnect-f.md) | 设备B上的应用，在创建协同会话成功并获得会话ID后，调用acceptConnect()方法接受连接。 调用此接口前，需先在两端设备分别创建协同会话。必须与设备A的connect方法配合使用： 设备A调用connect会拉起设备B应用，设备B在onCollaborate生命周期中创建会话后调用acceptConnect。 使用Promise异步回调。 |
| [connect](arkts-distributedservice-abilityconnectionmanager-connect-f.md) | 创建协同会话成功并获得会话ID后，设备A上可进行UIAbility的连接。调用此接口前， 需先在两端设备分别创建协同会话。connect接口通过底层分布式通信服务建立连接， 必须与设备B的acceptConnect配合使用才能建立成功连接，调用connect会拉起设备B应用。 连接过程会触发'connect'事件通知状态变化。使用Promise异步回调。 连接失败时，返回的ConnectResult对象中的errorCode字段包含具体的错误信息， 可参考ConnectErrorCode枚举了解错误原因。 |
| [createAbilityConnectionSession](arkts-distributedservice-abilityconnectionmanager-createabilityconnectionsession-f.md) | 创建应用间的协同会话。协同会话用于管理跨设备通信的连接状态， 需要先在两端设备分别创建会话，然后通过connect建立连接。 |
| [destroyAbilityConnectionSession](arkts-distributedservice-abilityconnectionmanager-destroyabilityconnectionsession-f.md) | 销毁应用间的协同会话，与createAbilityConnectionSession配对使用用于释放会话资源。 此接口需在成功创建协同会话后调用。销毁会话会释放相关资源，建议先调用disconnect断开连接后再销毁会话。 不调用此方法会导致资源泄漏。 |
| [disconnect](arkts-distributedservice-abilityconnectionmanager-disconnect-f.md) | 创建协同会话成功、应用连接成功、协同业务执行完毕后，协同双端的任意一台设备，应断开UIAbility的连接， 结束协同状态。需在connect()建立连接后调用。 |
| [getPeerInfoById](arkts-distributedservice-abilityconnectionmanager-getpeerinfobyid-f.md) | 获取指定会话中对端应用信息。此接口需在成功创建协同会话后调用。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#offconnect) | 取消connect事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#offdisconnect) | 取消disconnect事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#offreceivemessage) | 取消receiveMessage事件的回调监听。 |
| [off](arkts-distributedservice-abilityconnectionmanager-off-f.md#offreceivedata) | 取消receiveData事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#onconnect) | 注册connect事件的回调监听。当connect接口调用成功后会触发该事件。使用callback异步回调。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#ondisconnect) | 注册disconnect事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#onreceivemessage) | 注册receiveMessage事件的回调监听。 |
| [on](arkts-distributedservice-abilityconnectionmanager-on-f.md#onreceivedata) | 注册receiveData事件的回调监听。 |
| [reject](arkts-distributedservice-abilityconnectionmanager-reject-f.md) | 在跨端应用协同过程中，在拒绝对端的连接请求后，向对端发送拒绝原因。 |
| [sendData](arkts-distributedservice-abilityconnectionmanager-senddata-f.md) | 创建协同会话成功并获得会话ID、应用连接成功后，设备A或设备B可向对端设备发送 [ArrayBuffer](../../../arkts-utils/arraybuffer-object.md)字节流。使用Promise异步回调。 |
| [sendMessage](arkts-distributedservice-abilityconnectionmanager-sendmessage-f.md) | 创建协同会话成功并获得会话ID、调用connect接口建立连接成功后，设备A或设备B可向对端设备发送文本信息。 使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createStream](arkts-distributedservice-abilityconnectionmanager-createstream-f-sys.md) | 应用连接成功后，设备A或设备B可创建传输流，发送图片和视频流，使用Promise异步回调。 |
| [destroyStream](arkts-distributedservice-abilityconnectionmanager-destroystream-f-sys.md) | 发送图片和视频流等业务结束后，创建传输流的应用应及时销毁传输流，否则会增加系统功耗。 需与createStream()方法配对使用，在业务结束后必须调用此方法销毁传输流以释放资源。 |
| [getSurfaceId](arkts-distributedservice-abilityconnectionmanager-getsurfaceid-f-sys.md) | 获取指定传输流绑定的Surface的唯一标识符。Surface ID可用于将Surface与组件关联，实现音视频数据的显示。 |
| off | 取消receiveImage事件的回调监听。 |
| off | 取消collaborateEvent事件的回调监听。 |
| on | 注册receiveImage事件的回调监听。 |
| on | 注册collaborateEvent事件的回调监听。 |
| [sendImage](arkts-distributedservice-abilityconnectionmanager-sendimage-f-sys.md) | 应用连接成功并创建传输流后，设备A或设备B可向对端设备发送图片。 图片会根据指定的压缩质量进行编码后，通过传输流通道发送至对端设备。 发送成功后，对端设备可通过注册的回调接收图片，使用Promise异步回调。 业务结束后应及时销毁传输流，否则会增加系统功耗，使用场景包括跨设备视频通话中发送视频帧、 远程协作时发送截图、跨设备图片共享等需要向对端发送图片数据的场景。 |
| [setSurfaceId](arkts-distributedservice-abilityconnectionmanager-setsurfaceid-f-sys.md) | 设置传输流与Surface的绑定关系。Surface用于承载音视频数据的显示或采集， 绑定后传输流的音视频数据将直接渲染到Surface上或从Surface采集数据。 |
| [startStream](arkts-distributedservice-abilityconnectionmanager-startstream-f-sys.md) | 启动指定传输流，使传输流开始发送或接收视频数据。启动前需确保传输流已完成Surface绑定， 否则无法正常启动。需与stopStream()方法配对使用，使用完毕后应调用stopStream()停止传输流， 最后调用destroyStream()销毁传输流以释放资源。 |
| [stopStream](arkts-distributedservice-abilityconnectionmanager-stopstream-f-sys.md) | 停止指定传输流，使传输流停止发送或接收视频数据。需与startStream()方法配对使用， 在不需要传输数据时应调用此方法停止传输流，最后调用destroyStream()销毁传输流以释放资源。 使用场景包括视频通话暂停、用户关闭摄像头、切换前后摄像头等需要临时停止视频传输时调用。 |
| [updateSurfaceParam](arkts-distributedservice-abilityconnectionmanager-updatesurfaceparam-f-sys.md) | 更新与传输流绑定的Surface的配置信息，使新的配置参数生效。 |
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
| [StreamParam](arkts-distributedservice-abilityconnectionmanager-streamparam-i-sys.md) | 流传输配置的参数。用于配置传输流的传输方式和参数。其中role参数区分发送流（SOURCE）和接收流（SINK）， 发送流需要配置bitrate和colorSpaceConversionTarget等参数。@interface StreamParam |
| [SurfaceParam](arkts-distributedservice-abilityconnectionmanager-surfaceparam-i-sys.md) | Surface配置参数。@interface SurfaceParam |
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
| [FlipOptions](arkts-distributedservice-abilityconnectionmanager-flipoptions-e-sys.md) | 翻转选项。 |
| [StartOptionParams](arkts-distributedservice-abilityconnectionmanager-startoptionparams-e-sys.md) | 启动选项参数的枚举。 |
| [StreamRole](arkts-distributedservice-abilityconnectionmanager-streamrole-e-sys.md) | 流传输角色。 |
| [VideoPixelFormat](arkts-distributedservice-abilityconnectionmanager-videopixelformat-e-sys.md) | 视频像素格式配置选项。 |
<!--DelEnd-->
