# closeProxyChannel

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## closeProxyChannel

```TypeScript
function closeProxyChannel(channelId: int): void
```

关闭已打开的代理通道。适用于手机侧应用不再需要与穿戴设备侧应用通信的场景，例如完成数据同步任务后主动释放通道资源等。此方法必须与 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)配对使用，在使用完毕后调用此方法关闭通道以释放资源。关闭通道后，已注册的receiveData和 channelStateChange回调将自动取消订阅，正在传输的数据将中断。未及时关闭代理通道可能导致通道资源泄漏。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function closeProxyChannel(channelId: int): void--><!--Device-proxyChannelManager-function closeProxyChannel(channelId: int): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | int | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32390 006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because bluetooth proxy function has been trimmed.<br>**适用版本：** 26.0.0+ |
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
      Button('测试')
        .onClick(() => {
          // 以下为使用 try/catch 判断
          try {
            proxyChannelManager.closeProxyChannel(channelId); // channelId通过openProxyChannel接口的Promise返回值获取
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to close proxy channel. Code: ${error.code}, message: ${error.message}`);
            // 如果返回的error.code为undefined且error.message为"Cannot read property closeProxyChannel of undefined"，则当前镜像不支持该API
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

