# ShellCmdResult

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

ShellCmdResult是测试框架中用于封装Shell命令执行结果的数据对象，它包含stdResult（标准输出内容）和exitCode（退出码）两个关键属性，为测试脚本提供了结构化的命令执行结果访问方式。

该模块适用于需要验证Shell命令执行结果或处理命令返回数据的测试场景，通过abilityDelegator的[executeShellCommand](js-apis-inner-application-abilityDelegator.md#executeshellcommand)方法获取。需要注意的是，其接口仅限测试框架中使用，不应在正式业务代码中调用。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块接口仅可在<!--RP1-->[单元测试框架](../../application-test/unittest-guidelines.md)<!--RP1End-->中使用。

## 导入模块

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## 使用说明

调用abilityDelegator中的[executeShellCommand](js-apis-inner-application-abilityDelegator.md#executeshellcommand)方法获取ShellCmdResult实例。调用成功后，返回ShellCmdResult对象，包含Shell命令的标准输出内容（stdResult）和退出码（exitCode）。

**示例：**

```ts
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityDelegator: abilityDelegatorRegistry.AbilityDelegator;
let shellCommand = 'cmd';
// 获取AbilityDelegator实例
abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// 执行Shell命令，通过回调获取执行结果
abilityDelegator.executeShellCommand(shellCommand, (error: BusinessError<void> | null, data) => {
  if (error) {
    console.error(`executeShellCommand fail, error: ${JSON.stringify(error)}`);
  } else {
    console.info(`executeShellCommand success, data: ${JSON.stringify(data)}`);
  }
});
```

## ShellCmdResult

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 8

**ArkTS-Sta起始版本：** 23

| 名称      | 类型   | 只读 | 可选 | 说明                                                         |
| --------- | ------ | ---- | ---- | ------------------------------------------------------------ |
| stdResult | string | 否   | 否   | Shell命令的标准输出内容。 |
| exitCode  | number | 否   | 否   | Shell命令的退出码。返回值为0表示命令执行成功，非0表示命令执行失败。 |
