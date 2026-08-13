# getArguments

## getArguments

```TypeScript
function getArguments(): AbilityDelegatorArgs
```

获取单元测试参数[AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md#AbilityDelegatorArgs)对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-abilityDelegatorRegistry-function getArguments(): AbilityDelegatorArgs--><!--Device-abilityDelegatorRegistry-function getArguments(): AbilityDelegatorArgs-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AbilityDelegatorArgs | [AbilityDelegatorArgs]{ |

## 示例

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

