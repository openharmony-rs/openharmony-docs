# verifyControllerDevicePackage（系统接口）

## verifyControllerDevicePackage

```TypeScript
export function verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo):
    Promise<boolean[]>
```

验证来自控制器设备的授权包。 验证控制器设备发送的远程授权包。 它验证票证和远程设备信息，以确保授权是合法的。

**起始版本：** 26.1.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.1.0。

**废弃版本：** -1

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

<!--Device-abilityToolAccessCtrl-export function verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo):    Promise<boolean[]>--><!--Device-abilityToolAccessCtrl-export function verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo):    Promise<boolean[]>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ticketInfo | [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[] | 是 | 远程授权包列表 |
| remoteInfo | [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | 是 | 远端设备信息 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean[]&gt; | Promise用于返回\\${boolean[]}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-环境错误) | The account is not logged in, network is unavailable, timeout, etc. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. Format of ticketInfo or remoteInfo is invalid. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. possible cause: IPC failed. |

