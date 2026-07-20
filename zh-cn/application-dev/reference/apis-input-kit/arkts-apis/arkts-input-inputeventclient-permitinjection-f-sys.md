# permitInjection（系统接口）

## 导入模块

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

<a id="permitinjection"></a>
## permitInjection

```TypeScript
function permitInjection(result: boolean): void
```

允许事件注入权限。

**起始版本：** 12

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
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | SystemAPI permission error. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

