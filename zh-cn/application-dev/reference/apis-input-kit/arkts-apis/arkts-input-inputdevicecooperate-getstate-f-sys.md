# getState（系统接口）

## getState

```TypeScript
function getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void
```

获取键鼠穿越开关的状态，使用callback异步回调。 > **说明：** > > 从 API version 9开始支持，从API version 23开始废弃。建议使用 > [cooperate.getCooperateSwitchState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 23

**替代接口：** ohos.cooperate/cooperate#getCooperateSwitchState

<!--Device-inputDeviceCooperate-function getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void--><!--Device-inputDeviceCooperate-function getState(deviceDescriptor: string, callback: AsyncCallback<{ state: boolean }>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;{ state: boolean }&gt; | 是 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

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
          let deviceDescriptor = 'descriptor';
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

获取键鼠穿越开关的状态，使用Promise异步回调。 > **说明：** > > 从 API version 9开始支持，从API version 23开始废弃。建议使用 > [cooperate.getCooperateSwitchState]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替 > 代。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 23

**替代接口：** ohos.cooperate/cooperate#getCooperateSwitchState

<!--Device-inputDeviceCooperate-function getState(deviceDescriptor: string): Promise<{ state: boolean }>--><!--Device-inputDeviceCooperate-function getState(deviceDescriptor: string): Promise<{ state: boolean }>-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.Cooperator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceDescriptor | string | 是 | 键鼠穿越目标设备描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;{ state: boolean }&gt; | > } Promise used to return the state of the screen hopping switch. **true** if |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

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
          let deviceDescriptor = 'descriptor';
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

