# getArguments

## getArguments

```TypeScript
function getArguments(): AbilityDelegatorArgs
```

获取单元测试参数[AbilityDelegatorArgs]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对象。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-abilityDelegatorRegistry-function getArguments(): AbilityDelegatorArgs--><!--Device-abilityDelegatorRegistry-function getArguments(): AbilityDelegatorArgs-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | [AbilityDelegatorArgs]{ |

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

