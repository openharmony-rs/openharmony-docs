# @ohos.arkui.StateManagement

## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md) | AppStorageV2提供应用级全局共享状态变量的能力，开发者可以通过connect绑定同一个key，进行跨Ability的数据共享。具体UI使用说明，详见 [AppStorageV2(应用全局的UI状态存储)](../../../ui/state-management/arkts-new-appstoragev2.md)。 |
| [Binding](arkts-arkui-arkui-statemanagement-binding-c.md) | 只读数据绑定的泛型类，可以绑定任意类型的数据。 |
| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md) | globalConnect参数类型。 |
| [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md) | globalConnect 接口参数类型，ConnectOptionsCollections继承自[ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md)。当开发者需要持久化容器类型数据（如`Array&lt;S&gt;`）时，需要使用 `ConnectOptionsCollections`入参。 如下展示`StorageDefaultCreator&lt;T&gt;`和`StorageDefaultCreator&lt;S&gt;`示例： |
| [MutableBinding](arkts-arkui-arkui-statemanagement-mutablebinding-c.md) | 可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器。 |
| [PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md) | 继承自[AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)，PersistenceV2提供UI状态的持久化存储能力，支持将应用状态数据持久化到磁盘，在应用重启后恢复数据，适用于需要保留UI状态数据的场景。具体UI使用说 明，详见[PersistenceV2(持久化存储UI状态)](../../../ui/state-management/arkts-new-persistencev2.md)。 |
| [UIUtils](arkts-arkui-arkui-statemanagement-uiutils-c.md) | UIUtils状态管理相关的工具方法，包括获取代理对象的原始对象、将非观察数据变为可观察数据、动态添加和删除状态变量监听、同步刷新状态变量修改、创建数据绑定等，适用于需要手动管理状态观察、监听和同步刷新的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomComponentContext](arkts-arkui-arkui-statemanagement-customcomponentcontext-i.md) | `CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过 [UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext)获取实例。 |
| [CustomComponentLifecycle](arkts-arkui-arkui-statemanagement-customcomponentlifecycle-i.md) | CustomComponentLifecycle用于监控自定义组件生命周期的变化， 开发者可以通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。 |
| [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | 开发者注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。与生命周期装饰器的区别在于：生命周期装饰器由组件自身响应生命周期事件， CustomComponentLifecycleObserver从外部观察组件生命周期事件；若仅需组件自身响应生命周期变化，使用生命周期装饰器即可，若需集中监控多个组件的生命周期， 则使用CustomComponentLifecycleObserver。 |
| [DecoratorInfo](arkts-arkui-arkui-statemanagement-decoratorinfo-i.md) | 可被观察对象关联的装饰器和组件信息。 |
| [ElementInfo](arkts-arkui-arkui-statemanagement-elementinfo-i.md) | 可被观察对象关联的组件信息，包含系统组件和自定义组件。 |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) | `IReusableInfo`接口提供有关复用池管理的可复用组件的当前数量和数量上限的信息。 |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) | `IReusePool`接口提供自定义组件上的全局复用池的相关功能，包括查询回收组件的当前数量和上限信息、预渲染可复用组件到复用池中等，适用于开发者需要手动管理和优化组件复用效率的场景。 |
| [MonitorOptions](arkts-arkui-arkui-statemanagement-monitoroptions-i.md) | [addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor)的可选参数，用于配置回调类型以及是否使能通配符能力。 |
| [ObservedResult](arkts-arkui-arkui-statemanagement-observedresult-i.md) | 对象是否可被观察的结果。 |
| [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md) | 类构造函数。 |
| [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md) | 含有任意入参的类构造器。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md) | 自定义组件当前的生命周期状态。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CollectionType](arkts-arkui-collectiontype-t.md) | globalConnect的入参泛型，用于定义globalConnect支持的持久化集合数据类型。 |
| [GetterCallback](arkts-arkui-gettercallback-t.md) | 获取值的回调方法。 |
| [MonitorCallback](arkts-arkui-monitorcallback-t.md) | 参数为IMonitor类型的监听回调函数。 |
| [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) | 持久化失败时返回错误原因的回调。 |
| [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | 复用自定义组件初始化函数。 |
| [SetterCallback](arkts-arkui-settercallback-t.md) | 设置值的回调方法。 |
| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md) | 返回默认构造器的函数。 |
| [TaskCallback](arkts-arkui-taskcallback-t.md) | 同步执行的回调方法。 |
| [TypeDecorator](arkts-arkui-typedecorator-t.md) | 属性装饰器，用于装饰嵌套类中属于自定义class类的属性。 |

