# queryEntityInfo（系统接口）

## queryEntityInfo

```TypeScript
function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>
```

查询意图实体信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.EXECUTE_INSIGHT_INTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>--><!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, Object>>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 查询参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Record&lt;string, Object&gt;&gt;&gt; | - Returns the insight intent entity information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |


## queryEntityInfo

```TypeScript
function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, RecordData>>>
```

查询意图实体信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**需要权限：** ohos.permission.EXECUTE_INSIGHT_INTENT

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, RecordData>>>--><!--Device-insightIntentDriver-function queryEntityInfo(param: QueryParam): Promise<Array<Record<string, RecordData>>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| param | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 查询参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Record&lt;string, RecordData&gt;&gt;&gt; | - Returns the insight intent entity information. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [16000006](../errorcode-ability.md#16000006-不允许跨用户操作) | Cross-user operations are not allowed. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed;2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |

