# on

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## on('receiveData')

```TypeScript
function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void
```

订阅数据接收事件，使用Callback异步回调。适用于手机侧应用需要持续接收穿戴设备侧应用上报数据的场景，例如接收穿戴设备侧应用数据等。代理模块基于openProxyChannel时配置的对端UUID接收对端数据，将接收到的穿戴设 备侧应用数据通过回调传递给订阅者。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅数据接收事件。若需代理唤醒手机侧应用进程 以接收和处理对端数据，使用前请在module.json5中配置action字段"action.ohos.pull.listener"。订阅后需调用 off('receiveData') 取消订阅，避免回调持续触发。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | 设置订阅类型，固定取值为'receiveData'。 |
| channelId | number | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32 390006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | 是 | 回调函数，用于接收代理通道的数据。回调参数为[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)对象，包含 channelId（通道ID）和data（接收到的字节数据）。需先通过openProxyChannel打开代理通道后才能接收数据。多次注册时，仅最后一次注册的生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

**示例**

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('测试')
        .onClick(() => {
          const receiveDataCallback = (dataInfo: proxyChannelManager.DataInfo) => {
          };
          try {
            proxyChannelManager.on('receiveData', channelId, receiveDataCallback); // channelId通过openProxyChannel接口的Promise返回值获取
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to register receiveData callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```


## on('channelStateChange')

```TypeScript
function on(type: 'channelStateChange', channelId: number, callback: Callback<ChannelStateInfo>): void
```

订阅通道状态事件，使用Callback异步回调。适用于手机侧应用需要实时感知代理通道连接状态的场景，例如监测通道断开后暂停数据发送、通道恢复后自动重试业务等。代理模块实时监控蓝牙BR链路状态变化，当发生连接恢复、异常断连、配对关系 删除等事件时通过回调上报ChannelStateInfo。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅通道状态事件。订 阅后需调用 off('channelStateChange') 取消订阅，避免回调持续触发。调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道后，已注册的channelStateChange回调将自动取消 订阅。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'channelStateChange' | 是 | 设置订阅类型，固定取值为'channelStateChange'。 |
| channelId | number | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32 390006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | 是 | 回调函数，用于接收代理通道的状态变更信息。回调参数为 [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)对象，包含channelId（通道ID）和state（通道连接状态）。需先通过 openProxyChannel打开代理通道后才能接收通道状态。多次注册时，仅最后一次注册的回调函数生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390006](../errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390100](../errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

**示例**

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button('测试')
        .onClick(() => {
          const channelStateChangeCallback = (channelStateInfo: proxyChannelManager.ChannelStateInfo) => {
          };
          try {
            proxyChannelManager.on('channelStateChange', channelId, channelStateChangeCallback); // channelId通过openProxyChannel接口的Promise返回值获取
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to register channelStateChange callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
