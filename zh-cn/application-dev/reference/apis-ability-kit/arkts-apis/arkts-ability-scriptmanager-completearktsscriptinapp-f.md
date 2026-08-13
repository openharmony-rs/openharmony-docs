# completeArkTSScriptInApp

## completeArkTSScriptInApp

```TypeScript
function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>
```

完成应用的ArkTS脚本执行，上报执行结果。使用Promise异步回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-scriptManager-function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>--><!--Device-scriptManager-function completeArkTSScriptInApp(context: Context, requestCode: string, result: ExecuteResult): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](arkts-ability-context-c.md) | 是 | Ability上下文，用于临时文件授权。 |
| requestCode | string | 是 | 用于标识当前操作的请求码。 |
| result | ExecuteResult | 是 | ArkTS脚本的执行结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000020](../errorcode-ability.md#16000020-传入的context对象不是ability级别context) | The context is not ability context. |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. Possible causes: 1. Connect to system service failed; 2.Send restart message to system service failed; 3.System service failed to communicate with dependency module. |
| [16000003](../errorcode-ability.md#16000003-指定的id不存在) | The specified ID does not exist. |

