# sendMessage

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

<a id="sendmessage"></a>
## sendMessage

```TypeScript
function sendMessage(sessionId: number, msg: string): Promise<void>
```

应用连接成功后，设备A或设备B可向对端设备发送文本信息。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function sendMessage(sessionId: int, msg: string): Promise<void>--><!--Device-abilityConnectionManager-function sendMessage(sessionId: int, msg: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 协同会话ID。 |
| msg | string | 是 | 文本信息内容（内容最大限制为1KB）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2.Incorrect parameter types. |

**示例：**

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit'; 
import { hilog } from '@kit.PerformanceAnalysisKit';

let sessionId = 100;
abilityConnectionManager.sendMessage(sessionId, "message send success").then(() => {
  hilog.info(0x0000, 'testTag', "sendMessage success");
}).catch(() => {
  hilog.error(0x0000, 'testTag', "sendMessage failed");
})

```

