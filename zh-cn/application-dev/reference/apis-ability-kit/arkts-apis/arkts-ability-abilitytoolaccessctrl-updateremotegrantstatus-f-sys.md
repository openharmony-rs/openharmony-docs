# updateRemoteGrantStatus（系统接口）

## updateRemoteGrantStatus

```TypeScript
export function updateRemoteGrantStatus(remoteGrantStatus: RemoteGrantStatus): Promise<void>
```

更新远程授权状态。 该功能用于开启或关闭远程授权特性。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**需要权限：** ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS

<!--Device-abilityToolAccessCtrl-export function updateRemoteGrantStatus(remoteGrantStatus: RemoteGrantStatus): Promise<void>--><!--Device-abilityToolAccessCtrl-export function updateRemoteGrantStatus(remoteGrantStatus: RemoteGrantStatus): Promise<void>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| remoteGrantStatus | [RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | 是 | 要设置的远程授权状态 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不会返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial. The interface caller does not have permission "ohos.permission.MANAGE_TOOL_RUNTIME_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. possible cause: dependent service unavailable, resource access failure, etc. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. RemoteGrantStatus is invalid. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. possible cause: IPC failed. |

