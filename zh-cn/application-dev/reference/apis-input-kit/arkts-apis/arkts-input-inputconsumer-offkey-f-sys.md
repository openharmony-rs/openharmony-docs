# offKey（系统接口）

## offKey

```TypeScript
function offKey(keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void
```

取消订阅系统快捷键。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-inputConsumer-function offKey(keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void--><!--Device-inputConsumer-function offKey(keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOptions | KeyOptions | 是 | 组合键选项。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;KeyOptions&gt; | 否 | 需要取消订阅的回调函数。若不填，则取消当前应用组合键选项已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { Entry, Text, RelativeContainer, Component } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
import { inputConsumer, KeyCode } from '@kit.InputKit';

@Entry
@Component
struct Index {
  build() {
    RelativeContainer() {
      Text()
        .onClick(() => {
          let leftAltKey = 2045;
          let tabKey = 2049;
          let keyOptions: inputConsumer.KeyOptions = {
            preKeys: [ leftAltKey ],
            finalKey: tabKey,
            isFinalKeyDown: true,
            finalKeyDownDuration: 0
          };
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          }
          try {
            // 订阅按键事件
            inputConsumer.onKey(keyOptions, callback);
            // 取消监听单个回调函数
            inputConsumer.offKey(keyOptions, callback);
            // 取消监听所有回调函数
            inputConsumer.offKey(keyOptions);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## offKey

```TypeScript
function offKey(keyOptions: KeyOptions, callback?: KeyCommandCallback): void
```

取消订阅系统快捷键。使用callback异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputConsumer-function offKey(keyOptions: KeyOptions, callback?: KeyCommandCallback): void--><!--Device-inputConsumer-function offKey(keyOptions: KeyOptions, callback?: KeyCommandCallback): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOptions | KeyOptions | 是 | 组合键选项，需与订阅时传入的keyOptions一致。 |
| callback | [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | 否 | 需要取消订阅的回调函数。若不填，则取消当前应用组合键选项已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

## 示例

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Unsubscribe a single callback
let leftCtrlKey = 2072;
let cKey = 2049;
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`KeyEvent received`);
}
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.onKey(keyOptions, callback);
  inputConsumer.offKey(keyOptions, callback);
  console.info(`Unsubscribe success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Unsubscribe all callbacks for the specified keyOptions
let leftCtrlKey = 2072;
let cKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
try {
  inputConsumer.offKey(keyOptions);
  console.info(`Unsubscribe all success`);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to execute operation. Code: ${err.code}, message: ${err.message}`);
}
```

