# setWantAgentMultithreading（系统接口）

## setWantAgentMultithreading

```TypeScript
function setWantAgentMultithreading(isMultithreadingSupported: boolean) : void
```

开启或者关闭WantAgent多线程传递功能。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isMultithreadingSupported | boolean | 是 | 表示是否开启多线程传递功能。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-Not) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types. |

