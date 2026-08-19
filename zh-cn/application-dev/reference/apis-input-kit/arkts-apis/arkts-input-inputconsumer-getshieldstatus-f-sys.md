# getShieldStatus（系统接口）

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## getShieldStatus

```TypeScript
function getShieldStatus(shieldMode: ShieldMode): boolean
```

获取系统快捷键屏蔽类型。

**起始版本：** 23

**需要权限：** ohos.permission.INPUT_CONTROL_DISPATCHING

<!--Device-inputConsumer-function getShieldStatus(shieldMode: ShieldMode): boolean--><!--Device-inputConsumer-function getShieldStatus(shieldMode: ShieldMode): boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shieldMode | [ShieldMode](arkts-input-inputconsumer-shieldmode-e-sys.md) | 是 | 系统快捷键屏蔽类型，目前仅支持取值为'FACTORY_MODE'，表示屏蔽所有系统快捷键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 屏蔽类型生效状态，true代表屏蔽类型生效，false代表不生效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

**示例**

ArkTS-Dyn示例：

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
            let shieldStatusResult: boolean = inputConsumer.getShieldStatus(FACTORY_MODE);
            console.info(`Succeeded in getting shield status, result: ${JSON.stringify(shieldStatusResult)}.`);
          } catch (error) {
            console.error(`Failed to get shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

ArkTS-Sta示例：

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputConsumer } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let mode = inputConsumer.ShieldMode.FACTORY_MODE;
          try {
            let shieldstatusResult: Boolean =  inputConsumer.getShieldStatus(mode);
            console.info(`Succeeded in getting shield status, result:${JSON.stringify(shieldstatusResult)}.`);
          } catch (error) {
            console.error(`Failed to get shield status, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

