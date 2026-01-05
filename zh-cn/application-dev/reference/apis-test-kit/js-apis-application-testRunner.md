# @ohos.application.testRunner (TestRunner)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @li-weifeng2024; @xuzhihao666-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

TestRunner模块提供了框架测试的能力。包括准备单元测试环境、运行测试用例。

如果您想实现自己的单元测试框架，您必须继承这个类并覆盖它的所有方法。

> **说明：**
> 
> 本模块首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 
> 本模块接口仅可在<!--RP1-->[单元测试框架](../../application-test/unittest-guidelines.md)<!--RP1End-->中使用。 

## 导入模块

```ts
import { TestRunner } from '@kit.TestKit';
```

## TestRunner

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| onPrepare | [OnPrepareFn](#onpreparefn23) | 否    | 否    | 为运行测试用例准备单元测试环境。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**说明**：<br/>从API version 23开始，原来的onPrepare()方法变更为当前属性，调用方式不变。 |
| onRun | [OnRunFn](#onrunfn23) | 否    | 否    | 运行全部测试用例。<br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。<br/>**说明**：<br/>从API version 23开始，原来的onRun()方法变更为当前属性，调用方式不变。 |

## OnPrepareFn<sup>23+</sup>

type OnPrepareFn = () => void

当单元测试环境准备完成时，会触发该回调。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

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

## OnRunFn<sup>23+</sup>

type OnRunFn = () => void

当运行测试用例时，会触发该回调。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**原子化服务API：** 从API version 23开始，该接口支持在原子化服务中使用。

**示例：**

```ts
import { TestRunner } from '@kit.TestKit';

export default class UserTestRunner implements TestRunner {
  onPrepare() {
  }

  onRun() {
    console.info('Trigger onRun');
  }
}
```
