# requestToolTicket

## 导入模块

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## requestToolTicket

```TypeScript
export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketParams: TicketParams): Promise<TicketQueryResult>
```

获取CLI工具的执行认证票据。该函数用于获取CLI工具及子命令的执行认证票据。如果CLI工具所需权限用户尚未授权，会返回需要授权的权限列表及权限状态。如果CLI工具所需权限用户均授权，会返回授权的票据。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.EXEC_PUBLIC_CLI_TOOL

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-abilityToolAccessCtrl-export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketParams: TicketParams): Promise<TicketQueryResult>--><!--Device-abilityToolAccessCtrl-export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketParams: TicketParams): Promise<TicketQueryResult>-End-->

**系统能力：** SystemCapability.Security.Asset

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| cliCmdInfos | [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i.md)[] | 是 | CLI命令列表。 |
| ticketParams | [TicketParams](arkts-ability-abilitytoolaccessctrl-ticketparams-i.md) | 是 | 生成授权凭据选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TicketQueryResult](arkts-ability-abilitytoolaccessctrl-ticketqueryresult-i.md)&gt; | Promise用于返回${TicketQueryResult} |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. TicketExpireTime exceeds 60s, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010006](../errorcode-abilityToolAccessCtrl-sys.md#24010006-设备处于锁屏状态时不允许执行操作) | The requested operation is not allowed to be executed while the device is locked. |
