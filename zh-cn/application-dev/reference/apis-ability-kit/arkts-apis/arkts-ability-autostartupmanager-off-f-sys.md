# off（系统接口）

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

<a id="off"></a>
## off('systemAutoStartup')

```TypeScript
function off(type: 'systemAutoStartup', callback?: AutoStartupCallback): void
```

注销监听应用组件开机自启动状态变化的回调函数。从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_APP_BOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function off(type: 'systemAutoStartup', callback?: AutoStartupCallback): void--><!--Device-autoStartupManager-function off(type: 'systemAutoStartup', callback?: AutoStartupCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'systemAutoStartup' | 是 | 固定取值“systemAutoStartup”，表示为系统应用所调用。 |
| callback | [AutoStartupCallback](arkts-ability-autostartupcallback-i-sys.md) | 否 | 监听应用组件开机自启动状态变化的回调对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service. |

