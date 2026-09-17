# acceptConnect

## 导入模块

```TypeScript
import { abilityConnectionManager } from '@kit.DistributedServiceKit';
```

## acceptConnect

```TypeScript
function acceptConnect(sessionId: number, token: string): Promise<void>
```

设备B上的应用，在创建协同会话成功并获得会话ID后，调用acceptConnect()方法接受连接。调用此接口前，需先在两端设备分别创建协同会话。必须与设备A的connect方法配合使用：设备A调用connect会拉起设备B应用，设备B在onCollaborate生命周期中创建会话后调用acceptConnect。使用Promise异步回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedSched.AppCollaboration

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sessionId | number | 是 | 已创建的协同会话ID。 |
| token | string | 是 | 设备A应用传入的token值，该值通过wantParam参数中'ohos.dms.collabToken'键获取（在应用被拉起后的onCollaborate生命周期方法的wantParam参数中获取）。当设备A调用connect方法时，系统会自动生成collabToken并通过want参数传递给设备B，设备B在onCollaborate生命周期回调中可以从wantParam参数获取此token。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |

**示例**

```TypeScript
在设备B上，createAbilityConnectionSession接口调用并获取sessionId成功后，调用acceptConnect接口选择接受连接。
```
