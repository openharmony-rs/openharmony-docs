# off

## 导入模块

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
```

## off('receiveData')

```TypeScript
function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void
```

取消订阅数据接收事件，停止接收数据。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void--><!--Device-proxyChannelManager-function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | 设置订阅类型，固定取值为'receiveData'。 |
| channelId | number | 是 | 打开代理通道时获取的channelId。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<DataInfo> | 否 | 注册的回调函数。如果为空、undefined、null，则取消订阅所有的数据接收事件。如果不为空，传入最后一次注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

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
          try {
            proxyChannelManager.off('receiveData', channelId); // channelId通过openProxyChannel接口的Promise返回值获取
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


## off('channelStateChange')

```TypeScript
function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void
```

取消订阅通道状态事件。

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-proxyChannelManager-function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void--><!--Device-proxyChannelManager-function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'channelStateChange' | 是 | 设置订阅类型为'channelStateChange'。 |
| channelId | number | 是 | 打开代理通道时获取的channelId。 |
| callback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ChannelStateInfo> | 否 | 注册的回调函数。如果为空、undefined、null，则取消订阅所有的数据接收事件。如果不为空，传入最后一次注册的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [32390004](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390004-通道id非法或者不可用) | ChannelId is invalid or unavailable. |
| [32390006](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390006-参数错误) | Parameter error. |
| [32390100](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390100-内部异常) | Internal error. |
| [32390101](../../apis-distributedservice-kit/errorcode-proxyChannelManager.md#32390101-调用受限) | Call is restricted. |

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
          try {
            proxyChannelManager.off('channelStateChange', channelId); // channelId通过openProxyChannel接口的Promise返回值获取
          } catch (err) {
            let error = err as BusinessError;
            console.error(`Failed to unregister channelStateChange callback. Code: ${error.code}, message: ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

