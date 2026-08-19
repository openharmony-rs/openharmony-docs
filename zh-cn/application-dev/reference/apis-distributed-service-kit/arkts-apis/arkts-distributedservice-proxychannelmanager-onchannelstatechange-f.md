# onChannelStateChange

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## onChannelStateChange

```TypeScript
function onChannelStateChange(channelId: int, callback: Callback<ChannelStateInfo>): void
```

订阅通道状态事件，使用Callback异步回调。适用于手机侧应用需要实时感知代理通道连接状态的场景，例如监测通道断开后暂停数据发送、通道恢复后自动重试业务等。代理模块实时监控蓝牙BR链路状态变化，当发生连接恢复、异常断连、配对关系 删除等事件时通过回调上报ChannelStateInfo。必须在[openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能订阅通道状态事件。订 阅后需调用 [off('channelStateChange')](arkts-distributedservice-proxychannelmanager-offreceivedata-f.md) 取消订阅，避免回调持续触发。调用[closeProxyChannel](arkts-distributedservice-proxychannelmanager-closeproxychannel-f.md)关闭通道后，已注册的channelStateChange回调将自动取消 订阅。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function onChannelStateChange(channelId: int, callback: Callback<ChannelStateInfo>): void--><!--Device-proxyChannelManager-function onChannelStateChange(channelId: int, callback: Callback<ChannelStateInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | int | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32 390006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)&gt; | 是 | 回调函数，用于接收代理通道的状态变更信息。回调参数为 [ChannelStateInfo](arkts-distributedservice-proxychannelmanager-channelstateinfo-i.md)对象，包含channelId（通道ID）和state（通道连接状态）。需先通过 openProxyChannel打开代理通道后才能接收通道状态。多次注册时，仅最后一次注册的回调函数生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

**示例**

```TypeScript
import proxyChannelManager from '@ohos.distributedsched.proxyChannelManager';
import { BusinessError } from '@ohos.base';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("测试")
        .onClick(() => {
          const receiveStatusCallback = (channelStateInfo: proxyChannelManager.ChannelStateInfo) => {
          };
          try {
            proxyChannelManager.onChannelStateChange(channelId, receiveStatusCallback); // channelId通过openProxyChannel接口的Promise返回值获取
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

