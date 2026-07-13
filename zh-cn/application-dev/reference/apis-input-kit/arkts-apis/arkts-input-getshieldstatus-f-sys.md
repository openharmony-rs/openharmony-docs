# getShieldStatus（系统接口）

## getShieldStatus

```TypeScript
function getShieldStatus(shieldMode: ShieldMode): boolean
```

获取系统快捷键屏蔽类型。

**起始版本：** 11

**需要权限：** ohos.permission.INPUT_CONTROL_DISPATCHING

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shieldMode | ShieldMode | 是 | 系统快捷键屏蔽类型，目前仅支持取值为'FACTORY_MODE'，表示屏蔽所有系统快捷键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 屏蔽类型生效状态，true代表屏蔽类型生效，false代表不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let FACTORY_MODE = 0;
            let shieldstatusResult:Boolean =  inputConsumer.getShieldStatus(FACTORY_MODE);
            console.info(`Succeeded in getting shield status, result:${JSON.stringify(shieldstatusResult)}.`);
          } catch (error) {
            console.error(`Failed to get shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}

```

