# connect

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## connect

```TypeScript
function connect(sessionId: number): Promise<ConnectResult>
```

创建协同会话成功并获得会话ID后，设备A上可进行UIAbility的连接。调用此接口前， 需先在两端设备分别创建协同会话。connect接口通过底层分布式通信服务建立连接， 必须与设备B的acceptConnect配合使用才能建立成功连接，调用connect会拉起设备B应用。 连接过程会触发'connect'事件通知状态变化。使用Promise异步回调。 连接失败时，返回的ConnectResult对象中的errorCode字段包含具体的错误信息， 可参考ConnectErrorCode枚举了解错误原因。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 已创建的协同会话ID，由createAbilityConnectionSession接口返回。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;ConnectResult&gt; | Promise对象，成功时resolve返回ConnectResult（包含isConnected和errorCode字段）， 失败时reject返回错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

设备A上创建协同会话成功并获得会话ID后，调用connect()方法启动UIAbility连接，并拉起设备B应用。

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
