# requestToolPermissions（系统接口）

## requestToolPermissions

```TypeScript
export function requestToolPermissions(permissionQuery: PermissionQuery): Promise<PermissionQueryResult>
```

根据指定的操作查询工具权限。该函数用于检查权限查询中指定的CLI命令或API的权限状态。对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。当needTicket设置为true时，远程授权会生成一个票据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

<!--Device-abilityToolAccessCtrl-export function requestToolPermissions(permissionQuery: PermissionQuery): Promise<PermissionQueryResult>--><!--Device-abilityToolAccessCtrl-export function requestToolPermissions(permissionQuery: PermissionQuery): Promise<PermissionQueryResult>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionQuery | [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | 是 | 权限查询信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PermissionQueryResult&gt; | Promise用于返回${PermissionQueryResult}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial.The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. OperationType and operationInfo do not match,specified callerTokenId does not exist, ticketExpireTime exceeds 24h, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. possible cause: dependent service unavailable,resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-环境错误) | The account is not logged in, network is unavailable, timeout, etc. |
| [24010006](../errorcode-abilityToolAccessCtrl-sys.md#24010006-设备处于锁屏状态时不允许执行操作) | The requested operation is not allowed to be executed while the device is locked. |

