# sendData

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## sendData

```TypeScript
function sendData(channelId: number, data: ArrayBuffer): Promise<void>
```

向对端发送数据，使用Promise异步回调。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>--><!--Device-proxyChannelManager-function sendData(channelId: int, data: ArrayBuffer): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | number | 是 | 打开代理通道时获取的channelId。 |
| data | ArrayBuffer | 是 | 向对端发送的字节消息，长度最大为4096个字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回值的Promise的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because bluetooth proxy function has been trimmed.<br>**适用版本：** 26.0.0+ |
| [32390004](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |
| [32390103](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390103-发送数据超长) | Data too long. |
| [32390104](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390104-发送数据失败) | Send failed. |

**示例：**

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

