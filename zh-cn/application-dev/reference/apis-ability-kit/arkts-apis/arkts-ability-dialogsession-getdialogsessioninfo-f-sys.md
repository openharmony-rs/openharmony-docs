# getDialogSessionInfo（系统接口）

## getDialogSessionInfo

```TypeScript
function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo
```

通过dialogSessionId获取会话信息。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dialogSession-function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo--><!--Device-dialogSession-function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogSessionId | string | 是 | 用户请求会话ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DialogSessionInfo](arkts-ability-dialogsession-dialogsessioninfo-i-sys.md) | 同步返回会话信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |


## getDialogSessionInfo

```TypeScript
function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo | null
```

根据dialogSessionId获取会话信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dialogSession-function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo | null--><!--Device-dialogSession-function getDialogSessionInfo(dialogSessionId: string): DialogSessionInfo | null-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dialogSessionId | string | 是 | 用户请求会话ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DialogSessionInfo](arkts-ability-dialogsession-dialogsessioninfo-i-sys.md) | Returns the session info when the target DialogSessionInfo of dialogSessionId exists. Returns null if the target DialogSessionInfo of dialogSessionId not exist. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000005](../errorcode-ability.md#16000005-指定的进程权限校验失败) | The specified process does not have the permission. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | The application is not system-app, can not use system-api. |

