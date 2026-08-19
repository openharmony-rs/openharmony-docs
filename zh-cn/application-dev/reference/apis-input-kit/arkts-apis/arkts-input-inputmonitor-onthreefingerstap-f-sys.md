# onThreeFingersTap（系统接口）

## 导入模块

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## onThreeFingersTap

```TypeScript
function onThreeFingersTap(receiver: Callback<ThreeFingersTap>): void
```

监听全局触控板的三指轻点事件。

**起始版本：** 23

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onThreeFingersTap(receiver: Callback<ThreeFingersTap>): void--><!--Device-inputMonitor-function onThreeFingersTap(receiver: Callback<ThreeFingersTap>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| receiver | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[ThreeFingersTap](arkts-input-multimodalinput-gestureevent-threefingerstap-i.md)&gt; | 是 | 回调函数，返回三指轻点输入事件。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |

**示例**

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor, ThreeFingersTap } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅三指点击事件
            let funCallback = (threeFingersTap: ThreeFingersTap) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(threeFingersTap)}.`);
            };
            inputMonitor.onThreeFingersTap(funCallback);
          } catch (error) {
            console.error(`Failed to monitor three fingers tap, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

