# getAllRegisteredInformation（系统接口）

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## getAllRegisteredInformation

```TypeScript
function getAllRegisteredInformation(userId?: number): Promise<Array<LaunchServiceInformation>>
```

获取所有已注册的LaunchService信息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.MANAGE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function getAllRegisteredInformation(userId?: int): Promise<Array<LaunchServiceInformation>>--><!--Device-launchServiceManager-function getAllRegisteredInformation(userId?: int): Promise<Array<LaunchServiceInformation>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 否 | 指定userId时，查询该userId下已注册的LaunchService；未指定userId时，查询所有用户下已注册的LaunchService。<br>取值限定为整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md)&gt;&gt; | Promise对象，返回一个LaunchService的数组信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-非系统应用调用系统-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
