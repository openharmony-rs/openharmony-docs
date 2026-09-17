# off（系统接口）

## 导入模块

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## off('key')

```TypeScript
function off(type: 'key', keyOptions: KeyOptions, callback?: Callback<KeyOptions>): void
```

取消订阅系统快捷键。使用callback异步回调。

**起始版本：** 8

**系统能力：** SystemCapability.MultimodalInput.Input.InputConsumer

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'key' | 是 | 事件类型，当前仅支持 'key'。 |
| keyOptions | [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | 是 | 组合键选项。从API版本26.0.0起keyOptions中新增参数[KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md)，本接口无需关注此参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md)&gt; | 否 | 需要取消订阅的回调函数。若不填，则取消当前应用组合键选项已订阅的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api.<br>**适用版本：** 12+ |
