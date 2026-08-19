# connect

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## connect

```TypeScript
function connect(sessionId: int): Promise<ConnectResult>
```

创建协同会话成功并获得会话ID后，设备A上可进行UIAbility的连接。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityConnectionManager-function connect(sessionId: int): Promise<ConnectResult>--><!--Device-abilityConnectionManager-function connect(sessionId: int): Promise<ConnectResult>-End-->

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | int | 是 | 已创建的协同会话ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ConnectResult&gt; | 以Promise形式返回[连接结果]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let sessionId = 100;
abilityConnectionManager.connect(sessionId).then((ConnectResult) => {
  if (!ConnectResult.isConnected) {
    hilog.info(0x0000, 'testTag', 'connect failed');
    return;
  }
}).catch(() => {
  hilog.error(0x0000, 'testTag', "connect failed");
})
```

ArkTS-Sta示例：

```TypeScript
import abilityConnectionManager from '@ohos.distributedsched.abilityConnectionManager';
import hilog from '@ohos.hilog';

let sessionId = 100;
abilityConnectionManager.connect(sessionId).then((ConnectResult) => {
  if (!ConnectResult.isConnected) {
    hilog.info(0x0000, 'testTag', 'connect failed');
    return ConnectResult;
  }
}).catch(() => {
  hilog.error(0x0000, 'testTag', "connect failed");
})
```

