# offReceiveData

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## offReceiveData

```TypeScript
function offReceiveData(channelId: int, callback?: Callback<DataInfo>): void
```

取消订阅数据接收事件，不再通过回调接收数据。适用于手机侧应用不再需要接收穿戴设备侧应用数据的场景，例如用户切换到其他功能模块等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能取消订阅。此方法必须与 [on('receiveData')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 配对使用，用于取消之前通过on('receiveData')注册的数据接收回调。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function offReceiveData(channelId: int, callback?: Callback<DataInfo>): void--><!--Device-proxyChannelManager-function offReceiveData(channelId: int, callback?: Callback<DataInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | int | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32 390006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[DataInfo](arkts-distributedservice-proxychannelmanager-datainfo-i.md)&gt; | 否 | 注册的回调函数。默认效果：不传入此参数时取消订阅所有的数据接收事件。需传入on方法最后一次注册的回调函数，用于取消该回调的订阅；传入其他回调函数 不会生效。 |

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
          try {
            proxyChannelManager.offReceiveData(channelId); // channelId通过openProxyChannel接口的Promise返回值获取
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to unregister receiveData callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

