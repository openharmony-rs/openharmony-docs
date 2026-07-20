# cancelApplicationAutoStartup（系统接口）

## 导入模块

```TypeScript
import { autoStartupManager } from '@kit.AbilityKit';
```

<a id="cancelapplicationautostartup"></a>
## cancelApplicationAutoStartup

```TypeScript
function cancelApplicationAutoStartup(info: AutoStartupInfo, callback: AsyncCallback<void>): void
```

取消应用组件开机自启动。使用callback异步回调。从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_APP_BOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function cancelApplicationAutoStartup(info: AutoStartupInfo, callback: AsyncCallback<void>): void--><!--Device-autoStartupManager-function cancelApplicationAutoStartup(info: AutoStartupInfo, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | 是 | 要取消的开机自启动应用组件信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当取消应用组件开机自启动成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service. |


<a id="cancelapplicationautostartup-1"></a>
## cancelApplicationAutoStartup

```TypeScript
function cancelApplicationAutoStartup(info: AutoStartupInfo): Promise<void>
```

取消应用组件开机自启动。使用Promise异步回调。从API version 21开始，该接口仅在Phone、2in1、Tablet和Wearable设备中正常调用，在其他设备上返回16000050错误码。从API version 18开始，该接口仅在2in1和Wearable设备中可正常调用，在其他设备上返回16000050错误码。对于API version 18之前版本，该接口仅在2in1设备中可正常调用，在其他设备上返回16000050错误码。

**起始版本：** 11

**需要权限：** ohos.permission.MANAGE_APP_BOOT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-autoStartupManager-function cancelApplicationAutoStartup(info: AutoStartupInfo): Promise<void>--><!--Device-autoStartupManager-function cancelApplicationAutoStartup(info: AutoStartupInfo): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| info | [AutoStartupInfo](arkts-ability-common-autostartupinfo-t-sys.md) | 是 | 要取消的开机自启动应用组件信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied, interface caller does not have permission"ohos.permission.MANAGE_APP_BOOT". |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission denied, non-system app called system api. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | The parameter check failed. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| [16000004](../errorcode-ability.md#16000004-可见性校验失败) | Cannot start an invisible component. |
| [16000013](../errorcode-ability.md#16000013-应用被edm管控) | The application is controlled by EDM. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Failed to connect to the system service. |

