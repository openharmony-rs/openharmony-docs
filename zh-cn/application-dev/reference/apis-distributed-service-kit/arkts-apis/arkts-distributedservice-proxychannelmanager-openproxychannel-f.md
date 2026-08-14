# openProxyChannel

## openProxyChannel

```TypeScript
function openProxyChannel(channelInfo: ChannelInfo): Promise<int>
```

打开代理通道，使用Promise异步回调返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function openProxyChannel(channelInfo: ChannelInfo): Promise<int>--><!--Device-proxyChannelManager-function openProxyChannel(channelInfo: ChannelInfo): Promise<int>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelInfo | [ChannelInfo](arkts-distributedservice-proxychannelmanager-channelinfo-i.md) | 是 | 对端设备及服务的MAC和UUID信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 返回代理通道的channelId，取值范围为1~2147483647。channelId的生命周期和代理通道生命周期相同， 不关闭代理时，传入相同入参将返回相同channelId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because bluetooth proxy function has been trimmed.<br>**适用版本：** 26.0.0+ |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390102](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390102-操作失败或者连接超时) | Operation failed or Connection timed out. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |
| [32390002](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390002-设备未配对) | Device not paired. |
| [32390001](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390001-蓝牙已关闭) | BR is disabled. |

## 示例

ArkTS-Dyn示例:

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
          let channelInfo: proxyChannelManager.ChannelInfo = {
            linkType: proxyChannelManager.LinkType.LINK_BR,
            peerDevAddr: 'xx:xx:xx:xx:xx:xx', // 穿戴设备蓝牙MAC
            peerUuid: 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', // 穿戴侧监听的UUID
          };
          // 以下为使用 try/catch 判断
          try {
            proxyChannelManager.openProxyChannel(channelInfo)
              .then((channelId: number) => {
                // 获得通道ID
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
              });
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
            // 如果返回的error.code为undefined且error.message为"Cannot read property openProxyChannel of undefined"，则当前镜像不支持该API
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

ArkTS-Sta示例:

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
          let channelInfo: proxyChannelManager.ChannelInfo = {
            linkType: proxyChannelManager.LinkType.LINK_BR,
            peerDevAddr: 'xx:xx:xx:xx:xx:xx', // 穿戴设备蓝牙MAC
            peerUuid: 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx', // 穿戴侧监听的UUID
          };
          // 以下为使用 try/catch 判断
          try {
            proxyChannelManager.openProxyChannel(channelInfo)
              .then((channelId: int) => {
                // 获得通道ID
              })
              .catch((error: BusinessError) => {
                console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
              });
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to open proxy channel. Code: ${error.code}, message: ${error.message}`);
            // 如果返回的error.code为undefined且error.message为"Cannot read property openProxyChannel of undefined"，则当前镜像不支持该API
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

