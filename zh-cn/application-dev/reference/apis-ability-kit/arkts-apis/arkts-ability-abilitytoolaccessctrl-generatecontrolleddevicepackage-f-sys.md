# generateControlledDevicePackage（系统接口）

## 导入模块

```TypeScript
```

## generateControlledDevicePackage

```TypeScript
export function generateControlledDevicePackage(permissionQuery: PermissionQuery[]): Promise<RemoteAuthPackage[]>
```

生成受控设备的授权包。 根据权限查询列表生成远程授权包。 生成的包可以发送到控制器设备进行权限验证。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| permissionQuery | [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md)[] | 是 | 权限查询列表。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md)[]&gt; | Promise用于返回\\${RemoteAuthPackage[]}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. Permission exceeds 256 characters, specified tokenId is invalid, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-环境错误) | The account is not logged in, network is unavailable, timeout, etc. |

**示例**

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let permissionQuery: Array<abilityToolAccessCtrl.PermissionQuery> = [{
  operationInfo: [{
    operationType: abilityToolAccessCtrl.OperationType.CLI,
    info: {
      cliCmdName: 'ohos-displayManager',
      subCliCmdName: 'set-brightness'
    }
  }],
  needTicket: true,
  remoteInfo: {
    role: abilityToolAccessCtrl.Role.CONTROLLER,
    remoteId: 'device123',
    domainId: 'domain456'
  }
}];
abilityToolAccessCtrl.generateControlledDevicePackage(permissionQuery).then((data: Array<abilityToolAccessCtrl.RemoteAuthPackage>) => {
  console.info('generateControlledDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`generateControlledDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```
