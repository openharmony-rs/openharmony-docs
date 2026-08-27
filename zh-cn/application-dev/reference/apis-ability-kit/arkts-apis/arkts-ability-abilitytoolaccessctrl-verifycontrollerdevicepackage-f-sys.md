# verifyControllerDevicePackage（系统接口）

## 导入模块

```TypeScript
```

## verifyControllerDevicePackage

```TypeScript
export function verifyControllerDevicePackage(ticketInfo: RemoteAuthPackage[], remoteInfo: RemoteInfo):
    Promise<boolean[]>
```

验证来自控制器设备的授权包。 验证控制器设备发送的远程授权包。 它验证票证和远程设备信息，以确保授权是合法的。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.QUERY_TOOL_PERMISSIONS

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
| Promise & lt;boolean[] & gt; | Promise用于返回\\${boolean[]}。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denial. The interface caller does not have permission "ohos.permission.QUERY_TOOL_PERMISSIONS". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The caller is not a system application. |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-入参错误) | Invalid parameter. Format of ticketInfo or remoteInfo is invalid. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-系统服务工作异常) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-服务内部错误) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010003](../errorcode-abilityToolAccessCtrl-sys.md#24010003-环境错误) | The account is not logged in, network is unavailable, timeout, etc. |

**示例**

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ticketInfo: Array<abilityToolAccessCtrl.RemoteAuthPackage> = [{
  remoteMessage: 'test_message',
  challenge: 'test_challenge',
  ticket: 'test_ticket'
}];
let remoteInfo: abilityToolAccessCtrl.RemoteInfo = {
  role: abilityToolAccessCtrl.Role.CONTROLLER,
  remoteId: 'device123',
  domainId: 'domain456'
};
abilityToolAccessCtrl.verifyControllerDevicePackage(ticketInfo, remoteInfo).then((data: Array<boolean>) => {
  console.info('verifyControllerDevicePackage success, data: ' + JSON.stringify(data));
}).catch((err: BusinessError): void => {
  console.error(`verifyControllerDevicePackage fail, code: ${err.code}, message: ${err.message}`);
});
```
