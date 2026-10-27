# generateTaskIdentity（系统接口）

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## generateTaskIdentity

```TypeScript
export function generateTaskIdentity(taskIdentityInfo: TaskIdentityInfo): Promise<TaskIdentity>
```

为代理命令生成基于任务的身份验证身份。该函数根据调用者身份和基本任务属性（例如任务 ID 和任务过期时间）生成认证标识。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-abilityToolAccessCtrl-export function generateTaskIdentity(taskIdentityInfo: TaskIdentityInfo): Promise<TaskIdentity>--><!--Device-abilityToolAccessCtrl-export function generateTaskIdentity(taskIdentityInfo: TaskIdentityInfo): Promise<TaskIdentity>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| taskIdentityInfo | [TaskIdentityInfo](arkts-ability-abilitytoolaccessctrl-taskidentityinfo-i-sys.md) | 是 | 要生成认证标识的任务信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TaskIdentity](arkts-ability-abilitytoolaccessctrl-taskidentity-i-sys.md)&gt; | Promise用于返回${TaskIdentity}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. TicketExpireTime exceeds 24h, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
