# customComponent

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [BaseCustomComponent](arkts-na-customcomponent-basecustomcomponent-c.md) | 基础自定义组件的定义，它是所有自定义组件的基类。 |
| [BaseCustomDialog](arkts-na-customcomponent-basecustomdialog-c.md) | Definition of base custom dialog class. |
| [CustomComponent](arkts-na-customcomponent-customcomponent-c.md) | 定义自定义组件类 |
| [CustomComponentV2](arkts-na-customcomponent-customcomponentv2-c.md) | V2自定义组件类的定义。 |
| [EntryPoint](arkts-na-customcomponent-entrypoint-c.md) | Defining of entry of page |
| [ReuseObject](arkts-na-customcomponent-reuseobject-c.md) | Define ReuseObject for aboutToReuse method. |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomComponentInvokeOptions](arkts-na-customcomponent-customcomponentinvokeoptions-i.md) | Defining interface for _invokeImpl options. |
| [CustomComponentLifecycle](arkts-na-customcomponent-customcomponentlifecycle-i.md) | CustomComponentLifecycle用于监控自定义组件生命周期的变化，开发者可以通过 [UIUtils.getLifecycle](../../apis-arkui/arkts-apis/arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。 |
| [CustomComponentLifecycleObserver](arkts-na-customcomponent-customcomponentlifecycleobserver-i.md) | 用户注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。 |
| [LayoutCallbacks](arkts-na-customcomponent-layoutcallbacks-i.md) | Defining interface of LayoutCallbacks for custom component, when decorate with @Layoutable. |
| [PageLifeCycle](arkts-na-customcomponent-pagelifecycle-i.md) | Defining interface of PageLifeCycle for custom component, when decorate with @Entry. |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomComponentLifecycleState](arkts-na-customcomponent-customcomponentlifecyclestate-e.md) | 自定义组件当前的生命周期状态。 |
| [ReusePoolOwnership](arkts-na-customcomponent-reusepoolownership-e.md) | 重用池所有权的枚举 |

