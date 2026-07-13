# getState（系统接口）

## getState

```TypeScript
function getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void
```

获取键鼠穿越开关的状态，使用callback异步回调。

> **说明：**
>
> 从 API version 9开始支持，从API version 23开始废弃。建议使用
> [cooperate.getCooperateSwitchState](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-1)
> 替代。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** getCooperateSwitchState

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |
| callback | AsyncCallback&lt;{ state: boolean }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = "descriptor";
          try {
            inputDeviceCooperate.getState(deviceDescriptor, (error: BusinessError, data: object) => {
              if (error) {
                console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
                return;
              }
              console.info(`Succeeded in getting status, data: ${JSON.stringify(data)}.`);
            });
          } catch (error) {
            console.error(`Failed to get status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```


## getState

```TypeScript
function getState(deviceDescriptor: string): Promise<{ state: boolean }>
```

获取键鼠穿越开关的状态，使用Promise异步回调。

> **说明：**
>
> 从 API version 9开始支持，从API version 23开始废弃。建议使用
> [cooperate.getCooperateSwitchState](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-getcooperateswitchstate-f-sys.md#getcooperateswitchstate-2)替
> 代。

**起始版本：** 9

**废弃版本：** 23

**替代接口：** getCooperateSwitchState

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ state: boolean }&gt; |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |

**示例：**

```TypeScript
import { inputDeviceCooperate } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let deviceDescriptor = "descriptor";
          inputDeviceCooperate.getState(deviceDescriptor).then((data: object) => {
            console.info(`Succeeded in getting the status, data: ${JSON.stringify(data)}.`);
          }).catch((error: BusinessError) => {
            console.error(`Failed to get the status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          });
        })
    }
  }
}

```

