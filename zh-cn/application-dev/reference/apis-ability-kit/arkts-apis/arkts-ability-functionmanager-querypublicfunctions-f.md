# queryPublicFunctions

## 导入模块

```TypeScript
import { functionManager, FunctionHook, InvokeFunctionParam, FunctionResultWrap } from '@kit.AbilityKit';
```

## queryPublicFunctions

```TypeScript
function queryPublicFunctions(): Promise<Array<FunctionInfo>>
```

查询公开函数（Function），使用Promise异步回调。三方应用通过ACL授权获取权限后可调用此接口查询公开函数（Function）。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ACCESS_PUBLIC_FUNCTION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-functionManager-function queryPublicFunctions(): Promise<Array<FunctionInfo>>--><!--Device-functionManager-function queryPublicFunctions(): Promise<Array<FunctionInfo>>-End-->

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[FunctionInfo](arkts-ability-functioninfo-i.md)&gt;&gt; | Promise对象，返回公开函数信息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
