# off（系统接口）

## off('key')

```TypeScript
function off(type: 'key', keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void
```

取消订阅系统快捷键。使用callback异步回调。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

<!--Device-inputConsumer-function off(type: 'key', keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void--><!--Device-inputConsumer-function off(type: 'key', keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'key' | 是 | 事件类型，当前仅支持 'key'。 |
| keyOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 组合键选项。从API版本26.0.0起keyOptions中新增参数[KeyCommandTriggerType]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_，本接口无需关注此参数。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;KeyOptions&gt; | 否 | 需要取消订阅的回调函数。若不填，则取消当前应用组合键选项已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.\_\_\_HTML\_TAG\_USD\_0\_\_\_**适用版本：** 12+ |

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
          let leftAltKey = 2045;
          let tabKey = 2049;
          // 取消订阅单个回调函数
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          };
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            // 订阅按键事件
            inputConsumer.on('key', keyOption, callback);
            // 取消订阅按键事件
            inputConsumer.off('key', keyOption, callback);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

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
          let leftAltKey = 2045;
          let tabKey = 2049;
          // 取消订阅所有回调函数
          let callback = (keyOptions: inputConsumer.KeyOptions) => {
            console.info(`Succeeded in consuming key, keyOptions: ${JSON.stringify(keyOptions)}.`);
          };
          let keyOption: inputConsumer.KeyOptions = {preKeys: [leftAltKey], finalKey: tabKey, isFinalKeyDown: true, finalKeyDownDuration: 0};
          try {
            // 订阅按键事件
            inputConsumer.on('key', keyOption, callback);
            // 取消订阅按键事件
            inputConsumer.off('key', keyOption);
            console.info(`Succeeded in unsubscribing.`);
          } catch (error) {
            console.error(`Failed to unsubscribe, Code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}.`);
          }
        })
    }
  }
}
```

