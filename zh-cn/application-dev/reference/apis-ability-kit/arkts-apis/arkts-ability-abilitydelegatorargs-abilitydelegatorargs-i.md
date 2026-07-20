# AbilityDelegatorArgs

AbilityDelegatorArgs模块提供在应用程序执行测试用例期间，获取测试用例参数AbilityDelegatorArgs对象的能力。

> **说明：**  
>  
> 本模块接口仅可在[单元测试框架](docroot://application-test/unittest-guidelines.md)中使用。

**起始版本：** 8

<!--Device-unnamed-export interface AbilityDelegatorArgs--><!--Device-unnamed-export interface AbilityDelegatorArgs-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

当前被测试应用的包名。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityDelegatorArgs-bundleName: string--><!--Device-AbilityDelegatorArgs-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## parameters

```TypeScript
parameters: Record<string, string>
```

当前启动单元测试的参数。

**类型：** Record&lt;string, string&gt;

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityDelegatorArgs-parameters: Record<string, string>--><!--Device-AbilityDelegatorArgs-parameters: Record<string, string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## testCaseNames

```TypeScript
testCaseNames: string
```

测试用例名称。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityDelegatorArgs-testCaseNames: string--><!--Device-AbilityDelegatorArgs-testCaseNames: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## testRunnerClassName

```TypeScript
testRunnerClassName: string
```

执行测试用例的测试执行器名称。

**类型：** string

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityDelegatorArgs-testRunnerClassName: string--><!--Device-AbilityDelegatorArgs-testRunnerClassName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

