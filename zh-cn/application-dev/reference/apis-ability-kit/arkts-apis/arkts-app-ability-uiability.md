# @ohos.app.ability.UIAbility

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [UIAbility](arkts-ability-uiability-c.md) | 表示包含UI界面的应用组件，提供组件创建、销毁、前后台切换等生命周期回调，同时也具备后台通信能力。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Callee](arkts-ability-callee-i.md) | 系统为UIAbility创建的后台通信对象，Callee UIAbility（被调用方）可以通过Callee对象接收Caller对象发送的数据。 |
| [CalleeCallback](arkts-ability-calleecallback-i.md) | 通用组件服务端注册消息通知的回调函数类型。 |
| [Caller](arkts-ability-caller-i.md) | 调用方Caller UIAbility通过[startAbilityByCall](arkts-ability-uiabilitycontext-c.md#startabilitybycall-1)接口拉起目标Callee UIAbility，目标UIAbility启动成功后，返回一个Caller对象给调用方进行通信。 |
| [OnReleaseCallback](arkts-ability-onreleasecallback-i.md) | 注册通用组件服务端Stub（桩）断开监听通知的回调函数类型。 |
| [OnRemoteStateChangeCallback](arkts-ability-onremotestatechangecallback-i.md) | 注册协同场景下跨设备组件状态变化监听通知的回调函数类型。 |

