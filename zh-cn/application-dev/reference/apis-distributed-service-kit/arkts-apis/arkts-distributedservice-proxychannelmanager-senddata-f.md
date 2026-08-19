# sendData

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## sendData

```TypeScript
function sendData(channelId: int, data: ArrayBuffer): Promise<void>
```

向对端发送数据，使用Promise异步回调。适用于手机侧应用通过代理通道向穿戴设备侧应用发送指令或数据的场景，例如发送配置更新、通知消息等。必须在 [openProxyChannel](arkts-distributedservice-proxychannelmanager-openproxychannel-f.md)成功打开代理通道后才能调用此方法发送数据。当代理通道处于不可用状态（如 [ChannelState](arkts-distributedservice-proxychannelmanager-channelstate-e.md).CHANNEL_WAIT_RESUME、CHANNEL_EXCEPTION_SOFTWARE_FAILED、 CHANNEL_BR_NO_PAIRED）时，调用此方法将失败，建议订阅 [on('channelStateChange')](arkts-distributedservice-proxychannelmanager-onreceivedata-f.md) 事件监测通道状态，在通道不可用时暂停数据发送，通道恢复后继续发送。数据通过已建立的代理通道经蓝牙BR链路传输至对端设备，数据长度最大为4096字节，超出将返回错误码32390103。

**起始版本：** 23

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>--><!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | int | 是 | 打开代理通道时获取的channelId，取值范围为1~2147483647。使用无效或已关闭的channelId将返回错误码32390004，超出取值范围时返回错误码32390 006。channelId仅在代理通道可用时生效，通道关闭或断连后将不可用。 |
| data | ArrayBuffer | 是 | 向对端发送的二进制数据，数据格式由应用层自定义，最大长度为4096字节。超出长度限制时返回错误码32390103。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because bluetooth proxy function has been trimmed.<br>**适用版本：** 26.0.0+ |
| [32390104](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390104-发送数据失败) | Send failed. |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390103](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390103-发送数据超长) | Data too long. |
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
          const data = new ArrayBuffer(10); // 创建一个长度为 10 的 ArrayBuffer
          try {
            proxyChannelManager.sendData(channelId, data) // channelId通过openProxyChannel接口的Promise返回值获取
              .then(() => {
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to send data. Code: ${error.code}, message: ${error.message}`);
              });
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to send data. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

