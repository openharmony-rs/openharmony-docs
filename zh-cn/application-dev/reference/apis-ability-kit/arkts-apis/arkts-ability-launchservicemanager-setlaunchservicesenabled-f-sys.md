# setLaunchServicesEnabled（系统接口）

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## setLaunchServicesEnabled

```TypeScript
function setLaunchServicesEnabled(bundleName: string, userId: number, appIndex: number,
    enabled: boolean, token?: Uint8Array): Promise<void>
```

设置应用LaunchService的启用状态。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function setLaunchServicesEnabled(bundleName: string, userId: int, appIndex: int,    enabled: boolean, token?: Uint8Array): Promise<void>--><!--Device-launchServiceManager-function setLaunchServicesEnabled(bundleName: string, userId: int, appIndex: int,    enabled: boolean, token?: Uint8Array): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 目标应用包名。 |
| userId | number | 是 | 目标应用用户ID。<br>取值限定为整数。 |
| appIndex | number | 是 | 目标应用分身索引。<br>取值限定为整数。 |
| enabled | boolean | 是 | 设置的使能状态。true表示使能，false表示禁用。 |
| token | Uint8Array | 否 | 用于批准该操作的身份验证令牌。若传递了该令牌，直接使用该令牌进行鉴权；未传递时将拉起用户授权界面。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
| 16000215 | The approval request was rejected. |
| [16300005](../errorcode-ability.md#16300005-指定的包信息不存在) | The target bundle does not exist. |
