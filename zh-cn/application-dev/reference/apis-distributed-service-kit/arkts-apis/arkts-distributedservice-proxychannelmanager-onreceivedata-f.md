# onReceiveData

## onReceiveData

```TypeScript
function onReceiveData(channelId: int, callback: Callback<DataInfo>): void
```

订阅数据接收事件，使用Callback异步回调。适用于手机侧应用需要持续接收穿戴设备侧应用上报数据的场景，例如接收穿戴设备侧应用数据等。代理模块基于openProxyChannel时配置的对端UUID接收对端数据，将接收到的穿戴设 备侧应用数据通过回调传递给订阅者。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md#openproxychannel)成功打开代理通道后才能订阅数据接收事件。若需代理唤醒手机侧应用进程 以接收和处理对端数据，使用前请在module.json5中配置action字段"action.ohos.pull.listener"。订阅后需调用 [off('receiveData')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md#offreceivedata) 取消订阅，避免回调持续触发。

**起始版本：** 23

**ArkTS模式：** 起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function onReceiveData(channelId: int, callback: Callback<DataInfo>): void--><!--Device-proxyChannelManager-function onReceiveData(channelId: int, callback: Callback<DataInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | int | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32 390006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | 是 | 回调函数，用于接收代理通道的数据。回调参数为[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md#datainfo)对象，包含 channelId（通道ID）和data（接收到的字节数据）。需先通过openProxyChannel打开代理通道后才能接收数据。多次注册时，仅最后一次注册的生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

