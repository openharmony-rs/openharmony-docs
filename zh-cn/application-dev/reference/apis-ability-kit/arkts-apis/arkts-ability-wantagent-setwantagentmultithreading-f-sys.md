# setWantAgentMultithreading（系统接口）

## 导入模块

```TypeScript
import { WantAgent } from '@kit.AbilityKit';
```

<a id="setwantagentmultithreading"></a>
## setWantAgentMultithreading

```TypeScript
function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void
```

开启或者关闭WantAgent多线程传递功能。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wantAgent-function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void--><!--Device-wantAgent-function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMultithreadingSupported | boolean | 是 | 表示是否开启多线程传递功能。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not System App. Interface caller is not a system app. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

