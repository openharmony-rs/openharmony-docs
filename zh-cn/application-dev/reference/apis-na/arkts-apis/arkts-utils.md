# utils

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [Binding](arkts-na-utils-binding-c.md) | 只读数据绑定的泛型类可以绑定任意类型的数据（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。 |
| [MutableBinding](arkts-na-utils-mutablebinding-c.md) | 可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器（需要与@builder参数列表同时使用）。当调用函数时，需要使用makeBinding来进行值的传递。 |
| [ObservedArray](arkts-na-utils-observedarray-c.md) | 继承自Array&lt;T&gt;，为可观察API操作的Array对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。 |
| [ObservedDate](arkts-na-utils-observeddate-c.md) | 继承自Date，为可观察API操作的Date对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。 |
| [ObservedMap](arkts-na-utils-observedmap-c.md) | 继承自Map&lt;K, V&gt;，为可观察API操作的Map对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。 |
| [ObservedSet](arkts-na-utils-observedset-c.md) | 继承自Set&lt;K&gt;，为可观察API操作的Set对象。详见 ObservedArray/ObservedMap/ObservedSet/ObservedDate：具有观察能力的Built-in类型。 |
| [UIUtils](arkts-na-utils-uiutils-c.md) | UIUtils是状态管理提供的工具，用于处理可观察数据。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomComponentContext](arkts-na-utils-customcomponentcontext-i.md) | 自定义组件的上下文信息。 |
| [DecoratorInfo](arkts-na-utils-decoratorinfo-i.md) | 可被观察对象关联的装饰器和组件信息。 |
| [ElementInfo](arkts-na-utils-elementinfo-i.md) | 可被观察对象关联的组件信息，包含系统组件和自定义组件。 |
| [IReusableInfo](arkts-na-utils-ireusableinfo-i.md) | `IReusableInfo`接口提供有关复用池管理的可复用组件的当前数量和数量上限的信息。 |
| [IReusePool](arkts-na-utils-ireusepool-i.md) | `IReusePool` 接口提供自定义组件上的全局复用池的相关功能。 |
| [MonitorBaseOptions](arkts-na-utils-monitorbaseoptions-i.md) | 监听基础选项。 |
| [MonitorOptions](arkts-na-utils-monitoroptions-i.md) | 设置监听的行为。 |
| [MonitorValueInfo](arkts-na-utils-monitorvalueinfo-i.md) | 监听变量信息。 |
| [ObservedResult](arkts-na-utils-observedresult-i.md) | 对象是否可被观察的结果。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ActiveAndInactiveCallbackType](arkts-na-activeandinactivecallbacktype-t.md) | 定义激活和非激活函数回调 |
| [GetterCallback](arkts-na-gettercallback-t.md) | 获取绑定值的回调方法。 |
| [ObservedArrayInitializer](arkts-na-observedarrayinitializer-t.md) | ObservedArray的元素初始化函数类型。 |
| [SetterCallback](arkts-na-settercallback-t.md) | 设置绑定值的回调方法。 |

