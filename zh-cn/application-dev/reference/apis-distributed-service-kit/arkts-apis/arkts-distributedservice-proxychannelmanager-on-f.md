# on

## on('receiveData')

```TypeScript
function on(type: 'receiveData', channelId: number, callback: Callback<DataInfo>): void
```

�������ݽ����¼���ʹ���첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | ���ö������ͣ��̶�ȡֵΪ'receiveData'�� |
| channelId | number | 是 | �򿪴���ͨ��ʱ��ȡ��channelId�� |
| callback | Callback&lt;DataInfo&gt; | 是 | �ص����������ؽ��յ������ݡ����ע��ص����������һ��ע��Ļص�������Ч�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [32390004](../../errorcode-universal.md#32390004-ChannelId) | ChannelId is invalid or unavailable. |
| [32390006](../../errorcode-universal.md#32390006-Parameter) | Parameter error. |
| [32390100](../../errorcode-universal.md#32390100-Internal) | Internal error. |
| [32390101](../../errorcode-universal.md#32390101-Call) | Call is restricted. |

**示例：**

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Button("测试")
        .onClick(() => {
          const receiveDataCallback = (dataInfo: proxyChannelManager.DataInfo) => {
          };
          try {
            proxyChannelManager.on('receiveData', 1, receiveDataCallback); // 假设通道id为1
          } catch (err) {
            let error = err as BusinessError;
            console.error(`register receiveData error: ${error.code} ${error.message}`);
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

����ͨ��״̬�¼���ʹ��callback�����첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'channelStateChange' | 是 | ���ö������ͣ��̶�ȡֵΪ'channelStateChange'�� |
| channelId | number | 是 | �򿪴���ͨ��ʱ��ȡ��channelId�� |
| callback | Callback&lt;ChannelStateInfo&gt; | 是 | �ص����������ؽ��յ���ͨ��״̬�����ע��callback��<br/>���һ��ע���callback��Ч |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [32390004](../../errorcode-universal.md#32390004-ChannelId) | ChannelId is invalid or unavailable. |
| [32390006](../../errorcode-universal.md#32390006-Parameter) | Parameter error. |
| [32390100](../../errorcode-universal.md#32390100-Internal) | Internal error. |
| [32390101](../../errorcode-universal.md#32390101-Call) | Call is restricted. |

**示例：**

```TypeScript
import { proxyChannelManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

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
            proxyChannelManager.on('channelStateChange', 1, receiveStatusCallback); // 假设打开的通道id为1
          } catch (err) {
            let error = err as BusinessError;
            console.error(`getErr: ${error.code} ${error.message}`);
          }
        })
    }
    .height('100%')
    .width('100%')
  }
}

```

