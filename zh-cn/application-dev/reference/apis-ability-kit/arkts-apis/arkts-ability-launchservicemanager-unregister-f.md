# unregister

## 导入模块

```TypeScript
import { launchServiceManager } from '@kit.AbilityKit';
```

## unregister

```TypeScript
function unregister(descriptor: LaunchServiceDescriptor): Promise<void>
```

注销LaunchService。若LaunchService进程正在运行，注销时系统将停止该进程。

仅允许包含该LaunchService的应用自身进行注册注销，且需根据应用类型申请对应权限：  
- 普通应用（非MDM应用）：需申请ohos.permission.REGISTER_DAEMON_SERVICE权限。  
- MDM应用：需申请ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE权限。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.REGISTER_DAEMON_SERVICE or ohos.permission.ENTERPRISE_REGISTER_DAEMON_SERVICE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-launchServiceManager-function unregister(descriptor: LaunchServiceDescriptor): Promise<void>--><!--Device-launchServiceManager-function unregister(descriptor: LaunchServiceDescriptor): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| descriptor | [LaunchServiceDescriptor](arkts-ability-launchservicemanager-launchservicedescriptor-t.md) | 是 | 要注销的LaunchService的描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 不返回任何值的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | System service connection failed. |
| 16000211 | The specified service is not found. |
