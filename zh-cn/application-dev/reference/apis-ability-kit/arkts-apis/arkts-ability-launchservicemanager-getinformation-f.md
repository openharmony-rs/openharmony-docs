# getInformation

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## getInformation

```TypeScript
function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>
```

获取指定LaunchService的信息。如果应用程序已安装，但LaunchService未注册，返回的状态为NOT_REGISTERED，pid为0。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.USE_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>--><!--Device-launchServiceManager-function getInformation(descriptor: LaunchServiceDescriptor): Promise<LaunchServiceInformation>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | 是 | 要查询的LaunchService的描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[LaunchServiceInformation](arkts-ability-launchservicemanager-launchserviceinformation-t.md)&gt; | Promise用于返回LaunchService信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
| 16000211 | The specified service is not found. |
