# requestAutoFill

## 导入模块

```TypeScript
import { autoFillManager } from '@kit.AbilityKit';
```

## requestAutoFill

```TypeScript
export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void
```

触发自动填充请求。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

<!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void--><!--Device-autoFillManager-export function requestAutoFill(context: UIContext, request: FillRequest, callback?: AutoFillCallback): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [UIContext](../../apis-arkui/arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md) | 是 | Indicates the ui context where the filling operation will be performed. |
| request | [FillRequest](arkts-ability-autofillmanager-fillrequest-t.md) | 是 | Indicates the struct of automatic filling request. |
| callback | [AutoFillCallback](arkts-ability-autofillmanager-autofillcallback-i.md) | 否 | Indicates the callback that used to receive the result. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [16000050](../errorcode-ability.md#16000050-内部错误) | Internal error. |

**示例**
