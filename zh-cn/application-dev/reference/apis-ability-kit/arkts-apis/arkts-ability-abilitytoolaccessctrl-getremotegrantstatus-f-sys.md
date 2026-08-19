# getRemoteGrantStatus（系统接口）

## 导入模块

```TypeScript
```

## getRemoteGrantStatus

```TypeScript
export function getRemoteGrantStatus(): Promise<RemoteGrantStatus>
```

获取远程授权状态。 该功能用于查询远程授权特性的使能状态。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

<!--Device-abilityToolAccessCtrl-export function getRemoteGrantStatus(): Promise<RemoteGrantStatus>--><!--Device-abilityToolAccessCtrl-export function getRemoteGrantStatus(): Promise<RemoteGrantStatus>-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md)&gt; | Promise用于返回\\${RemoteGrantStatus}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. Possible cause: IPC failed. |

**示例**

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

abilityToolAccessCtrl.getRemoteGrantStatus().then((data: abilityToolAccessCtrl.RemoteGrantStatus) => {
  console.info('getRemoteGrantStatus success, data: ' + data);
}).catch((err: BusinessError): void => {
  console.error(`getRemoteGrantStatus fail, code: ${err.code}, message: ${err.message}`);
});
```

