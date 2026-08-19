# activateSceneAnimation（系统接口）

## 导入模块

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## activateSceneAnimation

```TypeScript
function activateSceneAnimation(formId: string): Promise<void>
```

互动卡片请求状态切换到激活态，只针对[场景动效类型互动卡片](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams标签)生效，使用Promise异 步回调。互动卡片状态分为激活态和非激活态，非激活态下，互动卡片同普通卡片一致；激活态下，互动卡片支持拉起卡片提供方所开发的LiveFormExtensionAbility进程，实现互动卡片动效。

**起始版本：** 23

<!--Device-formProvider-function activateSceneAnimation(formId: string): Promise<void>--><!--Device-formProvider-function activateSceneAnimation(formId: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.Form

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| formId | string | 是 | 卡片标识。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16501003](../errorcode-form.md#16501003-无法操作指定卡片) | The form cannot be operated by the current application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported.function activateSceneAnimation cannot work correctly due to limited device capabilities. |
| [16501001](../errorcode-form.md#16501001-卡片id不存在) | The ID of the form to be operated does not exist. |
| [16501000](../errorcode-form.md#16501000-内部功能错误) | An internal functional error occurred. |
| [16500060](../errorcode-form.md#16500060-连接服务失败) | Service connection error. |
| [16501011](../errorcode-form.md#16501011-卡片不支持调用当前接口) | The form cannot support this operation. |
| [16500050](../errorcode-form.md#16500050-进程间通信失败) | IPC connection error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not a system application. |
| [16500100](../errorcode-form.md#16500100-获取卡片配置信息失败) | Failed to obtain the configuration information. |

