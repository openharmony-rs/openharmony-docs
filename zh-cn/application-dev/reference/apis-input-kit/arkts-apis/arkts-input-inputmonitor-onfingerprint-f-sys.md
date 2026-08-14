# onFingerprint（系统接口）

## onFingerprint

```TypeScript
function onFingerprint(receiver: Callback<FingerprintEvent>): void
```

监听指纹手势输入事件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.INPUT_MONITORING

<!--Device-inputMonitor-function onFingerprint(receiver: Callback<FingerprintEvent>): void--><!--Device-inputMonitor-function onFingerprint(receiver: Callback<FingerprintEvent>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| receiver | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FingerprintEvent](arkts-input-multimodalinput-shortkey-fingerprintevent-i-sys.md)&gt; | 是 | 用于接收上报数据的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permit error. |

## 示例

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputMonitor } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          try {
            // 订阅指纹事件
            inputMonitor.onFingerprint((FingerprintEvent) => {
              console.info(`Succeeded in monitoring on ${JSON.stringify(FingerprintEvent)}.`);
            });
          } catch (error) {
            console.error(`Failed to monitor finger print event, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

