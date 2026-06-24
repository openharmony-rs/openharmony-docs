# sendData

## sendData

```TypeScript
function sendData(channelId: number, data: ArrayBuffer): Promise<void>
```

��Զ˷������ݣ�ʹ��Promise�첽�ص���

**起始版本：** 20

**需要权限：** ohos.permission.ACCESS_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| channelId | number | 是 | �򿪴���ͨ��ʱ��ȡ��channelId�� |
| data | ArrayBuffer | 是 | ��Զ˷��͵��ֽ���Ϣ���������Ϊ4096���ֽڡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷���ֵ��Promise�Ķ��� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported because bluetooth proxy function has<br/>been trimmed.&lt;br&gt;**适用版本：** 26.0.0+ |
| [32390004](../../errorcode-universal.md#32390004-ChannelId) | ChannelId is invalid or unavailable. |
| [32390006](../../errorcode-universal.md#32390006-Parameter) | Parameter error. |
| [32390100](../../errorcode-universal.md#32390100-Internal) | Internal error. |
| [32390101](../../errorcode-universal.md#32390101-Call) | Call is restricted. |
| [32390103](../../errorcode-universal.md#32390103-Data) | Data too long. |
| [32390104](../../errorcode-universal.md#32390104-Send) | Send failed. |

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
          const data = new ArrayBuffer(10); // 创建一个长度为 10 的 ArrayBuffer
          try {
            proxyChannelManager.sendData(1, data)// 假设通道id为1
              .then(() => {
              })
              .catch((error: BusinessError) => {
                console.error(`getErr: ${error.code} ${error.message}`);
              });
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

