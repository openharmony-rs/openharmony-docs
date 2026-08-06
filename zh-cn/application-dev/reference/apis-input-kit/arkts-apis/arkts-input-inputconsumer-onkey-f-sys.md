# onKey（系统接口）

## onKey

```TypeScript
function onKey(keyOptions: KeyOptions, callback: Callback<KeyOptions>): void
```

订阅系统快捷键，当满足条件的组合按键输入事件发生时，使用Callback异步方式上报组合按键数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-inputConsumer-function onKey(keyOptions: KeyOptions, callback: Callback<KeyOptions>): void--><!--Device-inputConsumer-function onKey(keyOptions: KeyOptions, callback: Callback<KeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组合键选项，支持triggerType参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;KeyOptions&gt; | 是 | 回调函数，返回组合按键数据 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

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
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}`);
          }
          try {
            // 订阅按键事件
            inputConsumer.onKey(keyOptions, callback);
          } catch (error) {
            console.error(`Failed to subscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```


## onKey

```TypeScript
function onKey(keyOptions: KeyOptions, callback:KeyCommandCallback): void
```

订阅组合按键（按键命令模式），支持通过triggerType指定不同的触发模式。当满足条件的组合按键输入事件发生时，使用callback异步回调。 与 [inputConsumer.on('key')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 现有接口的区别： - 本接口的keyOptions支持triggerType参数，可选择按键按下触发、重复按下触发、重复按下或抬起均会触发等模式。 - 本接口回调参数为KeyCommandCallback类型，同时接收KeyOptions和KeyEvent对象。 - 本接口采用事件消费机制，可通过事件消费阻止按键事件向后传递。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-inputConsumer-function onKey(keyOptions: KeyOptions, callback:KeyCommandCallback): void--><!--Device-inputConsumer-function onKey(keyOptions: KeyOptions, callback:KeyCommandCallback): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组合键选项，支持triggerType参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 回调函数，返回组合键选项和按键事件数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |

**示例：**

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftCtrlKey = 2072;
let cKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftCtrlKey],
  finalKey: cKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`keyOptions: ${keyOptions} keyEvents: ${keyEvents}`);
};
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [],
  finalKey: 2049,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.REPEAT_PRESSED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`Repeat key event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

```TypeScript
import { inputConsumer } from '@kit.InputKit';
import { BusinessError } from '@kit.BasicServicesKit';

let leftAltKey = 2045;
let tabKey = 2049;
let keyOptions: inputConsumer.KeyOptions = {
  preKeys: [leftAltKey],
  finalKey: tabKey,
  isFinalKeyDown: true,
  finalKeyDownDuration: 0,
  triggerType: inputConsumer.KeyCommandTriggerType.ALL_RELEASED
};
let callback: inputConsumer.KeyCommandCallback = (keyOptions, keyEvents): void => {
  console.info(`All released event`);
}
try {
  inputConsumer.onKey(keyOptions, callback);
} catch (error) {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to subscribe. Code: ${err.code}, message: ${err.message}`);
}
```

