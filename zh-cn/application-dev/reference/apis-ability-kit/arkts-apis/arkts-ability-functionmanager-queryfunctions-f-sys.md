# queryFunctions（系统接口）

## 导入模块

```TypeScript
import { functionManager } from '@kit.AbilityKit';
```

## queryFunctions

```TypeScript
function queryFunctions(): Promise<Array<FunctionInfo>>
```

查询所有可用的Function信息，使用Promise异步回调。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_FUNCTION

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Ability.AgentRuntime.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[FunctionInfo](arkts-ability-functioninfo-i-sys.md)&gt;&gt; | Promise对象，返回可用Function的信息列表，包含命名空间、名称、版本、描述、输入输出模式等。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Not system application. |
| [35600050](../errorcode-ability.md#35600050-偶发性报错) | System Error. 1. Connect to system service failed; 2.System service failed to communicate with dependency module. |
