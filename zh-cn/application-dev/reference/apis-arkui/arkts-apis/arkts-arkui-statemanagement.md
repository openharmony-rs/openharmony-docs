# @ohos.arkui.StateManagement

## 导入模块

```TypeScript
import { Binding, ComponentReuse, CustomComponentLifecycleState, ComponentInactive, PersistenceV2, ComponentDisappear, MutableBinding, CustomComponentLifecycleObserver, AppStorageV2, Type, ConnectOptionsCollections, CollectionType, CustomComponentContext, IReusePool, ConnectOptions, UIUtils, ComponentActive, CustomComponentLifecycle, ComponentInit, ComponentAppear, ComponentBuilt, ComponentRecycle, IReusableInfo } from '@kit.ArkUI';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md) | AppStorageV2具体UI使用说明，详见[AppStorageV2(应用全局的UI状态存储)](../../../../ui/state-management/arkts-new-appstoragev2.md)。 |
| [Binding](arkts-arkui-arkui-statemanagement-binding-c.md) | 只读数据绑定的泛型类，可以绑定任意类型的数据。 |
| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md) | globalConnect参数类型。 |
| [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md) | [globalConnect](PersistenceV2.globalConnect&lt;T extends CollectionType&lt;S&gt;, S extends object&gt;( type: ConnectOptionsCollections&lt;T, S&gt; \| ConnectOptions&lt;T&gt; ))接口参数类型，ConnectOptionsCollections继承自[ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md)。当开发者需要持久化容器类型数据（如`Array&lt;S&gt;`）时，需要使用`ConnectOptionsCollections`入参。如下展示`StorageDefaultCreator&lt;T&gt;`和`StorageDefaultCreator&lt;S&gt;`示例： |
| [MutableBinding](arkts-arkui-arkui-statemanagement-mutablebinding-c.md) | 可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器。 |
| [PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md) | 继承自[AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)，PersistenceV2具体UI使用说明，详见[PersistenceV2(持久化存储UI状态)](../../../../ui/state-management/arkts-new-persistencev2.md)。 |
| [UIUtils](arkts-arkui-arkui-statemanagement-uiutils-c.md) | UIUtils提供一些方法，用于处理状态管理相关的数据转换。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomComponentContext](arkts-arkui-arkui-statemanagement-customcomponentcontext-i.md) | `CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过[UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext-1)获取实例。 |
| [CustomComponentLifecycle](arkts-arkui-arkui-statemanagement-customcomponentlifecycle-i.md) | CustomComponentLifecycle用于监控自定义组件生命周期的变化。 |
| [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | 用户注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。 |
| [DecoratorInfo](arkts-arkui-arkui-statemanagement-decoratorinfo-i.md) | 可被观察对象关联的装饰器和组件信息。 |
| [ElementInfo](arkts-arkui-arkui-statemanagement-elementinfo-i.md) | 可被观察对象关联的组件信息，包含系统组件和自定义组件。 |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) | `IReusableInfo`接口提供有关复用池管理的可复用组件的当前数量和数量上限的信息。 |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) | `IReusePool` 接口提供自定义组件上的全局复用池的相关功能。 |
| [MonitorOptions](arkts-arkui-arkui-statemanagement-monitoroptions-i.md) | [addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor-1)的可选参数，用于配置回调类型以及是否使能通配符能力。 |
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
| [MonitorCallback](arkts-arkui-monitorcallback-t.md) | 参数为[IMonitor](../arkts-components/arkts-arkui-common-imonitor-i.md)类型的监听回调函数。 |
| [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) | 持久化失败时返回错误原因的回调。 |
| [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | 复用自定义组件初始化函数。 |
| [SetterCallback](arkts-arkui-settercallback-t.md) | 设置值的回调方法。 |
| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md) | 返回默认构造器的函数。 |
| [TaskCallback](arkts-arkui-taskcallback-t.md) | 同步执行的回调方法。 |
| [TypeDecorator](arkts-arkui-typedecorator-t.md) | 属性装饰器，用于装饰嵌套类中属于自定义class类的属性。 |

