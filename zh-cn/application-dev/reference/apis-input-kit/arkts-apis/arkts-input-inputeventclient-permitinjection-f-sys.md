# permitInjection（系统接口）

## permitInjection

```TypeScript
function permitInjection(result: boolean): void
```

允许事件注入权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INJECT_INPUT_EVENT

<!--Device-inputEventClient-function permitInjection(result: boolean): void--><!--Device-inputEventClient-function permitInjection(result: boolean): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputSimulator

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | boolean | 是 | 授权结果（true表示：允许事件注入，false表示：不允许事件注入）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { inputEventClient } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let result = true;
            // 授权事件注入
            inputEventClient.permitInjection(result);
          }catch(error){
            console.error(`Failed to permit injection, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
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
import { inputEventClient } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            let result = true;
            // 授权事件注入
            inputEventClient.permitInjection(result);
          }catch(error){
            console.error(`Failed to get inject permission, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

