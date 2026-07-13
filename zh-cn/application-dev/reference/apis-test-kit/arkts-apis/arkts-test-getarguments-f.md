# getArguments

## getArguments

```TypeScript
function getArguments(): AbilityDelegatorArgs
```

获取单元测试参数[AbilityDelegatorArgs](application/abilityDelegatorArgs:AbilityDelegatorArgs)对象。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityDelegatorArgs | [AbilityDelegatorArgs](application/abilityDelegatorArgs:AbilityDelegatorArgs)对象。可以用来获取测试参数。 |

**示例：**

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';

// 获取单元测试参数AbilityDelegatorArgs对象
let args = abilityDelegatorRegistry.getArguments();
// 打印测试参数信息
console.info(`getArguments bundleName: ${args.bundleName}`);
console.info(`getArguments parameters: ${JSON.stringify(args.parameters)}`);
console.info(`getArguments testCaseNames: ${args.testCaseNames}`);
console.info(`getArguments testRunnerClassName: ${args.testRunnerClassName}`);

```

