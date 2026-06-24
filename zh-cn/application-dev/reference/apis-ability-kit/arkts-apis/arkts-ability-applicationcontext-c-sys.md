# ApplicationContext

ApplicationContext作为应用上下文，继承自[Context](arkts-ability-context-depr-i.md#Context)，提供了应用生命周期监听、进程管理、应用环境设置等应用级别的管控能力。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。

**继承/实现关系：** ApplicationContext extends [Context](../../apis-arkui/arkts-apis/arkts-arkui-context-t.md#Context)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## preloadUIExtensionAbility

```TypeScript
preloadUIExtensionAbility(want: Want): Promise<void>
```

Preload UIExtensionAbility.

**起始版本：** 12

**需要权限：** ohos.permission.PRELOAD_UI_EXTENSION_ABILITY

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | Want | 是 | Indicates the want of target UIExtensionAbility. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-The) | The application does not have permission to call the interface. |
| [202](../../errorcode-universal.md#202-The) | The application is not system-app, can not use system-api. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified.<br/>2.Incorrect parameter types. |
| [16000001](../../errorcode-universal.md#16000001-The) | The specified ability does not exist. |
| [16000002](../../errorcode-universal.md#16000002-Incorrect) | Incorrect ability type. |
| [16000004](../../errorcode-universal.md#16000004-Cannot) | Cannot start an invisible component. |
| [16000011](../../errorcode-universal.md#16000011-The) | The context does not exist. |
| [16000050](../../errorcode-universal.md#16000050-Internal) | Internal error. |

