# @ohos.arkui.StateManagement(状态管理)

状态管理模块具备应用数据存储、持久化管理以及UIAbility（包含用户界面的应用组件）数据存储能力，同时覆盖环境状态、工具和UI状态同步等场景，从而帮助开发者简化状态管理逻辑，提升应用的响应能力和数据一致性。

本文中T和S的含义如下：

| 类型   | 说明                                     |
 | ---- | -------------------------------------- |
| T    | Class、number、boolean、string和这些类型的数组形式。 |
| S    | number、boolean、string。                 |



## 导入模块

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## 汇总

### 装饰器

| 名称 | 说明 |
| --- | --- |
| [@ComponentActive](arkts-arkui-arkui-statemanagement-componentactive-d.md#componentactive) | 自定义组件由非激活状态转变为激活状态后，调用@ComponentActive装饰的函数。在组件回收复用场景下，当缓存的组件被重新复用（即从复用池重新添加到节点树）时，组件由非激活状态转为激活状态，触发此回调。 |
| [@ComponentAppear](arkts-arkui-arkui-statemanagement-componentappear-d.md#componentappear) | 与aboutToAppear相似，\@ComponentAppear装饰的函数在创建自定义组件的新实例后，在其build()函数执行前调用，不同的是，\@ComponentAppear装饰的函数仅在自定义组件处于[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).INIT状态才会触发。允许在\@ComponentAppear装饰的函数中改变状态变量，更改将在后续执行build()函数中生效。 |
| [@ComponentBuilt](arkts-arkui-arkui-statemanagement-componentbuilt-d.md#componentbuilt) | \@ComponentBuilt装饰的函数在自定义组件的build()函数首次执行后调用，即从CustomComponentLifecycleState.APPEARED到CustomComponentLifecycleState.BUILT的阶段触发。开发者可以在此阶段实现埋点数据上报等不影响实际UI的功能。 |
| [@ComponentDisappear](arkts-arkui-arkui-statemanagement-componentdisappear-d.md#componentdisappear) | @ComponentDisappear装饰的函数在自定义组件销毁前执行，即向CustomComponentLifecycleState.DISAPPEARED状态转变时触发。不建议在此函数中改变状态变量，特别是\@Link变量的修改可能会导致应用程序行为不稳定。 |
| [@ComponentInactive](arkts-arkui-arkui-statemanagement-componentinactive-d.md#componentinactive) | 自定义组件由激活状态转变为非激活状态后，调用@ComponentInactive装饰的函数。在组件回收复用场景下，当组件被回收到复用池时，组件由激活状态转为非激活状态，触发此回调。 |
| [@ComponentInit](arkts-arkui-arkui-statemanagement-componentinit-d.md#componentinit) | \@ComponentInit装饰的函数在自定义组件初始化即将完成时执行，先于\@ComponentAppear触发。开发者可以在此时注册生命周期监听器和修改状态变量。与\@ComponentAppear的区别在于：\@ComponentInit侧重于初始化阶段的准备操作（如注册监听），\@ComponentAppear侧重于组件即将展现前的状态变更，两者配合使用可分别承担初始化与显现前的职责。 |
| [@ComponentRecycle](arkts-arkui-arkui-statemanagement-componentrecycle-d.md#componentrecycle) | 当组件被回收后，先执行应用程序中定义的资源释放等回收操作，完成回收后调用\@ComponentRecycle装饰的函数，即从CustomComponentLifecycleState.BUILT到CustomComponentLifecycleState.RECYCLED阶段触发。随后该组件被冻结，以避免该组件处于复用池时进行UI更新。最后，回收会递归遍历所有子组件，对每个完成回收的子组件调用子组件中\@ComponentRecycle装饰的函数。 |
| [@ComponentReuse](arkts-arkui-arkui-statemanagement-componentreuse-d.md#componentreuse) | 当可复用的自定义组件从缓存中重新添加到节点树时调用\@ComponentReuse装饰的函数，即从CustomComponentLifecycleState.RECYCLED到CustomComponentLifecycleState.BUILT阶段触发，以接收组件的构造参数。最后，复用会递归遍历所有子组件，对每个完成复用的子组件，会调用子组件中\@ComponentReuse装饰的函数。 |
| [@Type](arkts-arkui-arkui-statemanagement-type-d.md#type) | @Type标记属性的原始类型，可确保在序列化过程中正确保留和还原属性的复杂类型信息。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md) | AppStorageV2提供应用级全局共享状态变量的能力，开发者可以通过connect绑定同一个key，进行跨Ability的数据共享。具体UI使用说明，详见[AppStorageV2(应用全局的UI状态存储)](../../../ui/state-management/arkts-new-appstoragev2.md)。 |
| [Binding](arkts-arkui-arkui-statemanagement-binding-c.md) | 只读数据绑定的泛型类，可以绑定任意类型的数据。 |
| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md) | globalConnect参数类型。 |
| [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md) | globalConnect接口参数类型，ConnectOptionsCollections继承自[ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md)。当开发者需要持久化容器类型数据（如`Array&lt;S&gt;`）时，需要使用`ConnectOptionsCollections`入参。 |
| [MutableBinding](arkts-arkui-arkui-statemanagement-mutablebinding-c.md) | 可变数据绑定的泛型类，允许对绑定值进行读写操作，提供完整的get和set访问器。 |
| [PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md) | 继承自[AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md)，PersistenceV2提供UI状态的持久化存储能力，支持将应用状态数据持久化到磁盘，在应用重启后恢复数据，适用于需要保留UI状态数据的场景。具体UI使用说明，详见[PersistenceV2(持久化存储UI状态)](../../../ui/state-management/arkts-new-persistencev2.md)。 |
| [UIUtils](arkts-arkui-arkui-statemanagement-uiutils-c.md) | UIUtils状态管理相关的工具方法，包括获取代理对象的原始对象、将非观察数据变为可观察数据、动态添加和删除状态变量监听、同步刷新状态变量修改、创建数据绑定等，适用于需要手动管理状态观察、监听和同步刷新的场景。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [CustomComponentContext](arkts-arkui-arkui-statemanagement-customcomponentcontext-i.md) | `CustomComponentContext`类提供对组件级服务的访问，包括复用池。通过[UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext)获取实例。 |
| [CustomComponentLifecycle](arkts-arkui-arkui-statemanagement-customcomponentlifecycle-i.md) | CustomComponentLifecycle用于监控自定义组件生命周期的变化，开发者可以通过[UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle)获取CustomComponentLifecycle实例。 |
| [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | 开发者注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。与生命周期装饰器的区别在于：生命周期装饰器由组件自身响应生命周期事件，CustomComponentLifecycleObserver从外部观察组件生命周期事件；若仅需组件自身响应生命周期变化，使用生命周期装饰器即可，若需集中监控多个组件的生命周期，则使用CustomComponentLifecycleObserver。 |
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
| [MonitorCallback](arkts-arkui-monitorcallback-t.md) | 参数为[IMonitor](../arkts-components/arkts-arkui-imonitor-i.md)类型的监听回调函数。 |
| [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) | 持久化失败时返回错误原因的回调。 |
| [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | 复用自定义组件初始化函数。 |
| [SetterCallback](arkts-arkui-settercallback-t.md) | 设置值的回调方法。 |
| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md) | 返回默认构造器的函数。 |
| [TaskCallback](arkts-arkui-taskcallback-t.md) | 同步执行的回调方法。 |
| [TypeDecorator](arkts-arkui-typedecorator-t.md) | 属性装饰器，用于装饰嵌套类中属于自定义class类的属性。 |
