# TestRunner

TestRunner模块提供了框架测试的能力。包括准备单元测试环境、运行测试用例。 如果您想实现自己的单元测试框架，您必须继承这个类并覆盖它的所有方法。

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-unnamed-interface TestRunner--><!--Device-unnamed-interface TestRunner-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onPrepare

```TypeScript
onPrepare(): void
```

为运行测试用例准备单元测试环境。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TestRunner-onPrepare(): void--><!--Device-TestRunner-onPrepare(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { TestRunner } from '@kit.TestKit';

// 实现自定义测试运行器
export default class UserTestRunner implements TestRunner {
  // 准备单元测试环境
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  onRun() {
  }
}
```

## onRun

```TypeScript
onRun(): void
```

运行测试用例。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TestRunner-onRun(): void--><!--Device-TestRunner-onRun(): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**示例：**

```TypeScript
import { TestRunner } from '@kit.TestKit';

// 实现自定义测试运行器
export default class UserTestRunner implements TestRunner {
  // 准备单元测试环境
  onPrepare() {
    console.info('Trigger onPrepare');
  }

  // 运行测试用例
  onRun() {
    console.info('Trigger onRun');
  }

  // 测试完成时的回调处理
  onStop() {
    console.info('Trigger onStop');
  }
}
```

## onPrepare

```TypeScript
onPrepare: OnPrepareFn
```

为运行测试用例准备单元测试环境。

**类型：** OnPrepareFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TestRunner-onPrepare: OnPrepareFn--><!--Device-TestRunner-onPrepare: OnPrepareFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onRun

```TypeScript
onRun: OnRunFn
```

运行测试用例。

**类型：** OnRunFn

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TestRunner-onRun: OnRunFn--><!--Device-TestRunner-onRun: OnRunFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## onStop

```TypeScript
onStop?: OnStopFn
```

当测试完成时，系统会在测试环境退出前触发该回调。

**类型：** OnStopFn

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TestRunner-onStop?: OnStopFn--><!--Device-TestRunner-onStop?: OnStopFn-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

