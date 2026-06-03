# @ohos.application.testRunner (TestRunner)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

TestRunner模块提供了框架测试的能力。包括准备单元测试环境、运行测试用例。

如果您想实现自己的单元测试框架，您必须继承这个类并覆盖它的所有方法。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
> - 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块接口仅可在<!--RP1-->[单元测试框架](../../application-test/unittest-guidelines.md)<!--RP1End-->中使用。 

## 导入模块

```ts
import { TestRunner } from '@kit.TestKit';
```

## TestRunner

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| onPrepare | [OnPrepareFn](#onpreparefn) | 否    | 否    | 为运行测试用例准备单元测试环境。<br/>**ArkTS模式：** 该接口仅适用于ArkTS-Sta<br/>**ArkTS-Sta起始版本：** 23 |
| onRun | [OnRunFn](#onrunfn) | 否    | 否    | 运行全部测试用例。<br/>**ArkTS模式：** 该接口仅适用于ArkTS-Sta<br/>**ArkTS-Sta起始版本：** 23 |
| onStop | [OnStopFn](#onstopfn) | 否 | 是 | 当测试完成时，系统会在测试环境退出前触发该回调。<br/>**原子化服务API（仅ArkTS-Dyn）：** 从API version 26.0.0开始，该接口支持在原子化服务中使用。<br/>**ArkTS-Dyn起始版本：** 26.0.0 <br/>**ArkTS-Sta起始版本：** 26.0.0 <br/>**模型约束：** 此接口仅可在Stage模型下使用。|

**示例：**

ArkTS-Sta示例：
```ts
'use static'
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  public onPrepare: () => void = () => {
    console.info('Trigger onPrepare');
  }

  public onRun: () => void = () => {
    console.info('Trigger onRun');
  }

  public onStop?: () => void = () => {
    console.info('Trigger onStop');
  }
}
```

### onPrepare

onPrepare(): void

为运行测试用例准备单元测试环境。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn

**ArkTS-Dyn起始版本：** 8

**示例：**

```ts 
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
  }
}
```

### onRun

onRun(): void

运行测试用例。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core


**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn

**ArkTS-Dyn起始版本：** 8

**示例：**

```ts
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
    console.info('Trigger onRun');
  }

  onStop() {
    console.info('Trigger onStop');
  }
}
```

## OnPrepareFn

type OnPrepareFn = () => void

当单元测试环境准备完成时，会触发该回调。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

## OnRunFn

type OnRunFn = () => void

当运行测试用例时，会触发该回调。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**ArkTS模式：** 此接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

## OnStopFn

type OnStopFn = () => void

当测试完成时，系统会在测试环境退出前触发该回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**原子化服务API（仅ArkTS-Dyn）：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core