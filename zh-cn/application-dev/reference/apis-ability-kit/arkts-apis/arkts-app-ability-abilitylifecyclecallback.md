# @ohos.app.ability.AbilityLifecycleCallback

[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)从创建到销毁过程其生命周期是动态变化的。AbilityLifecycleCallback模块提供监听
 [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)生命周期变化的能力，可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。
 > **说明**
 >
 > 本模块接口只能监听进程内UIAbility生命周期变化。
 ## 使用说明
 1. 应用创建AbilityLifecycleCallback对象，并调用ApplicationContext.on('abilityLifecycle')接口注册UIAbility生命周期变化监听。
 2. 当UIAbility生命周期变化时，应用可以通过已注册的AbilityLifecycleCallback对象接收到UIAbility生命周期的变化通知。
 3. 当应用不需要监听UIAbility生命周期变化时，需要通过ApplicationContext.off('abilityLifecycle')接口取消监听。


## 导入模块

```TypeScript
import { AbilityLifecycleCallback } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)从创建到销毁过程其生命周期是动态变化的。 AbilityLifecycleCallback模块提供监听[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md)生命周期变化的能力， 可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。 |
