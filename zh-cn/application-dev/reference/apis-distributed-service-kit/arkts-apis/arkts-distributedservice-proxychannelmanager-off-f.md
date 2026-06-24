# off

## off('receiveData')

```TypeScript
function off(type: 'receiveData', channelId: number, callback?: Callback<DataInfo>): void
```

ȡ���������ݽ����¼���ֹͣ�������ݡ�

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'receiveData' | 是 | ���ö������ͣ��̶�ȡֵΪ'receiveData'�� |
| channelId | number | 是 | �򿪴���ͨ��ʱ��ȡ��channelId�� |
| callback | Callback&lt;DataInfo&gt; | 否 | ע��Ļص����������Ϊ�ա�undefined��null����ȡ���������е����ݽ����¼���<br/>�����Ϊ�գ��������һ��ע��Ļص������� |

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
          try {
            proxyChannelManager.off('receiveData', 1); // 假设通道id为1
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


## off('channelStateChange')

```TypeScript
function off(type: 'channelStateChange', channelId: number, callback?: Callback<ChannelStateInfo>): void
```

ȡ������ͨ��״̬�¼���

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'channelStateChange' | 是 | ���ö�������Ϊ'channelStateChange'�� |
| channelId | number | 是 | �򿪴���ͨ��ʱ��ȡ��channelId�� |
| callback | Callback&lt;ChannelStateInfo&gt; | 否 | ע��Ļص����������Ϊ�ա�undefined��null��<br/>��ȡ���������е����ݽ����¼��������Ϊ�գ��������һ��ע��Ļص������� |

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
          try {
            proxyChannelManager.off('channelStateChange', 1); // 假设打开的通道id为1
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

