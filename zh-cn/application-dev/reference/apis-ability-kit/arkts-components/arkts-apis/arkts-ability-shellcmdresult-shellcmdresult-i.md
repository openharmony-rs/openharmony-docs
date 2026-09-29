# ShellCmdResult

```TypeScript
export interface ShellCmdResult
```

本模块提供Shell命令执行结果的能力。

> **说明：** 
> 
> 本模块接口仅可在[单元测试框架](../../../application-test/unittest-guidelines.md)中使用。

**起始版本：** 8

<!--Device-unnamed-export interface ShellCmdResult--><!--Device-unnamed-export interface ShellCmdResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**测试接口：** 此接口仅在自动化测试脚本中使用。

## exitCode

```TypeScript
exitCode: number
```

Shell命令的结果码。

**类型：** number

**起始版本：** 8

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-ShellCmdResult-exitCode: int--><!--Device-ShellCmdResult-exitCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## stdResult

```TypeScript
stdResult: string
```

Shell命令的标准输出内容。

**类型：** string

**起始版本：** 8

**原子化服务API（仅ArkTS-Dyn）：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-ShellCmdResult-stdResult: string--><!--Device-ShellCmdResult-stdResult: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
