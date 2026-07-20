# updateConfiguration（系统接口）

## 导入模块

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

<a id="updateconfiguration"></a>
## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void
```

通过传入修改的配置项来更新配置。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-abilityManager-function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void--><!--Device-abilityManager-function updateConfiguration(config: Configuration, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-configuration-i.md) | 是 | 新的配置项，仅需配置需要更新的项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当更新配置成功，err为undefined；否则为错误对象。可进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |


<a id="updateconfiguration-1"></a>
## updateConfiguration

```TypeScript
function updateConfiguration(config: Configuration): Promise<void>
```

通过修改配置来更新配置。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.UPDATE_CONFIGURATION

<!--Device-abilityManager-function updateConfiguration(config: Configuration): Promise<void>--><!--Device-abilityManager-function updateConfiguration(config: Configuration): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [Configuration](../../apis-arkui/arkts-components/arkts-arkui-configuration-i.md) | 是 | 新的配置项，仅需配置需要更新的项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。开发者可在此进行错误处理或其他自定义处理。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

