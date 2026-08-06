# @ohos.app.ability.AbilityLifecycleCallback

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AbilityLifecycleCallback](arkts-ability-app-ability-abilitylifecyclecallback-abilitylifecyclecallback-c.md) | [UIAbility]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_从创建到销毁过程其生命周期是动态变化的。 AbilityLifecycleCallback模块提供监听[UIAbility]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_生命周期变化的能力， 可用于统计每个UIAbility的运行时长、执行与UIAbility业务逻辑解耦的数据加载等场景。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnAbilitySaveStateFn](arkts-ability-onabilitysavestatefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onSaveState触发后回调。 |
| [OnAbilityWillBackgroundFn](arkts-ability-onabilitywillbackgroundfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onBackground触发前回调。 |
| [OnAbilityWillContinueFn](arkts-ability-onabilitywillcontinuefn-t.md) | 注册监听应用上下文的生命周期后，在Ability迁移前触发回调。 |
| [OnAbilityWillCreateFn](arkts-ability-onabilitywillcreatefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onCreate触发前回调。 |
| [OnAbilityWillDestroyFn](arkts-ability-onabilitywilldestroyfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onDestroy触发前回调。 |
| [OnAbilityWillForegroundFn](arkts-ability-onabilitywillforegroundfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onForeground触发前回调。 |
| [OnAbilityWillSaveStateFn](arkts-ability-onabilitywillsavestatefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onSaveState触发前回调。 |
| [OnNewWantFn](arkts-ability-onnewwantfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onNewWant触发后回调。 |
| [OnWillNewWantFn](arkts-ability-onwillnewwantfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onNewWant触发前回调。 |
| [OnWindowStageRestoreFn](arkts-ability-onwindowstagerestorefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onWindowStageRestore触发后回调。 |
| [OnWindowStageWillCreateFn](arkts-ability-onwindowstagewillcreatefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onWindowStageCreate触发前回调。 |
| [OnWindowStageWillDestroyFn](arkts-ability-onwindowstagewilldestroyfn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onWindowStageDestroy触发前回调。 |
| [OnWindowStageWillRestoreFn](arkts-ability-onwindowstagewillrestorefn-t.md) | 注册监听应用上下文的生命周期后，在UIAbility的onWindowStageRestore触发前回调。 |

