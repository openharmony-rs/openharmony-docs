# @ohos.arkui.StateManagement(State Management)

The state management module provides data storage, persistent data management, UIAbility data storage, and
 environment state and tools required by applications.

T and S in this topic represent the types as described below.

| Type  | Description                                    |
 | ---- | -------------------------------------- |
| T    | Class, number, boolean, string, and arrays of these types.|
| S    | number, boolean, string.                |



## Modules to Import

```TypeScript
import { AppStorageV2, PersistenceV2, Type, UIUtils, ConnectOptions, Binding, MutableBinding, CustomComponentLifecycle, CustomComponentLifecycleObserver, CustomComponentLifecycleState, ComponentInit, ComponentAppear, ComponentBuilt, ComponentReuse, ComponentActive, ComponentInactive, ComponentRecycle, ComponentDisappear, CollectionType, ConnectOptionsCollections, CustomComponentContext, IReusePool, IReusableInfo, StorageDefaultCreator, TypeConstructorWithArgs, PersistenceErrorCallback, TypeConstructor, TypeDecorator, MonitorCallback, MonitorOptions, GetterCallback, SetterCallback, ObservedResult, DecoratorInfo, ElementInfo } from '@kit.ArkUI';
```

## Summary

### Decorators

| Name | Description |
| --- | --- |
| [@ComponentActive](arkts-arkui-arkui-statemanagement-componentactive-d.md#componentactive) | The function decorated is invoked before a custom component becomes active. |
| [@ComponentAppear](arkts-arkui-arkui-statemanagement-componentappear-d.md#componentappear) | Decorates a function that is called after a new instance of the custom component is created and before the **build()** function is executed. This callback is similar to **aboutToAppear**. The difference is that the **@ComponentAppear** callback is triggered only when the custom component is in the **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).INIT** state. The state variable can be changed in **@ComponentAppear**. The change will take effect in the subsequent **build()** function execution. |
| [@ComponentBuilt](arkts-arkui-arkui-statemanagement-componentbuilt-d.md#componentbuilt) | Decorates a function that is called after the **build()** function of the custom component is executed for the first time, that is, when the component status changes from **CustomComponentLifecycleState.APPEARED** to **CustomComponentLifecycleState.BUILT**. You can use this callback for actions that do not affect the UI, such as tracking data reporting. |
| [@ComponentDisappear](arkts-arkui-arkui-statemanagement-componentdisappear-d.md#componentdisappear) | Decorates a function that is called when the custom component is destructed. You are advised not to change state variables in this function. Modifying the **@Link** decorated variable may lead to unstable application behavior. |
| [@ComponentInactive](arkts-arkui-arkui-statemanagement-componentinactive-d.md#componentinactive) | The function decorated is invoked before a custom component becomes inactive. |
| [@ComponentInit](arkts-arkui-arkui-statemanagement-componentinit-d.md#componentinit) | Decorates a function that is called when the initialization of a custom component is about to complete. You can register a listener at this time. |
| [@ComponentRecycle](arkts-arkui-arkui-statemanagement-componentrecycle-d.md#componentrecycle) | Decorates a function that is called when the necessary recycling operations defined in the application are performed. That is, this function is triggered when the component status changes from **CustomComponentLifecycleState.BUILT** to **CustomComponentLifecycleState.RECYCLED**. At last, the function decorated by **@ComponentRecycle** recursively traverses all child components, and the **@ComponentRecycle** decorated function in each recycled child component will be called. |
| [@ComponentReuse](arkts-arkui-arkui-statemanagement-componentreuse-d.md#componentreuse) | Decorates a function that is called when a reusable custom component is re-added to the node tree from the cache, that is, when the component status changes from the **CustomComponentLifecycleState.RECYCLED** to **CustomComponentLifecycleState.BUILT** phase, to receive the constructor parameters. At last, the function decorated by **@ComponentReuse** recursively traverses all child components, and the **@ComponentReuse** decorated function in each reused child component will be called. |
| [@Type](arkts-arkui-arkui-statemanagement-type-d.md#type) | Define Type PropertyDecorator, adds type information to an object. |

### Classes

| Name | Description |
| --- | --- |
| [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md) | For details about how to use AppStorageV2, see [AppStorageV2: Storing Application-wide UI State](../../../ui/state-management/arkts-new-appstoragev2.md). |
| [Binding](arkts-arkui-arkui-statemanagement-binding-c.md) | Represents the generic class for read-only data binding, which can bind data of any type. |
| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md) | Defines the parameter type for **globalConnect**. |
| [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md) | Defines the parameter type for the globalConnect API. **ConnectOptionsCollections** is inherited from [ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md). You can use the **ConnectOptionsCollections** input parameter to persist container data (such as **Array\&lt;S&gt;**). |
| [MutableBinding](arkts-arkui-arkui-statemanagement-mutablebinding-c.md) | Represents a generic class for mutable data binding, which allows the read and write operations on the bound value and provides complete **get** and **set** accessors. |
| [PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md) | Inherits from [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md). For details, see [PersistenceV2: Persisting Application State](../../../ui/state-management/arkts-new-persistencev2.md). |
| [UIUtils](arkts-arkui-arkui-statemanagement-uiutils-c.md) | Provides APIs for handling data transformations related to state management. |

### Interfaces

| Name | Description |
| --- | --- |
| [CustomComponentContext](arkts-arkui-arkui-statemanagement-customcomponentcontext-i.md) | The **CustomComponentContext** class provides access to component-level services, including the reuse pool. You can obtain an instance through [UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext). |
| [CustomComponentLifecycle](arkts-arkui-arkui-statemanagement-customcomponentlifecycle-i.md) | **CustomComponentLifecycle** monitors the lifecycle changes of a custom component. |
| [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | Observes lifecycle status changes of a custom component, and triggers the lifecycle callback in the listener when detecting lifecycle status changes. |
| [DecoratorInfo](arkts-arkui-arkui-statemanagement-decoratorinfo-i.md) | Defines the decorator and component information associated with the observable object. |
| [ElementInfo](arkts-arkui-arkui-statemanagement-elementinfo-i.md) | Defines information about the components associated with the observable object, including system components and custom components. |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) | The **IReusableInfo** API provides information about the current number and maximum number of reusable components managed by the reuse pool. |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) | The **IReusePool** API provides the features related to the global reuse pool of a custom component. |
| [MonitorOptions](arkts-arkui-arkui-statemanagement-monitoroptions-i.md) | Defines the optional parameters for [addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor), which are used to configure the callback type and whether to enable the wildcard capability. |
| [ObservedResult](arkts-arkui-arkui-statemanagement-observedresult-i.md) | Provides the result of whether the object can be observed. |
| [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md) | Represents a class constructor. |
| [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md) | Represents a class constructor that accepts arbitrary arguments. |

### Enums

| Name | Description |
| --- | --- |
| [CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md) | Current lifecycle status of a custom component. |

### Types

| Name | Description |
| --- | --- |
| [CollectionType](arkts-arkui-collectiontype-t.md) | Defines the types of persistent collection data supported by **globalConnect** using the generic type of the input parameter of **globalConnect**. |
| [GetterCallback](arkts-arkui-gettercallback-t.md) | Defines a callback used to obtain a value. |
| [MonitorCallback](arkts-arkui-monitorcallback-t.md) | Listener callback function of the [IMonitor](../arkts-components/arkts-arkui-imonitor-i.md) type. |
| [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) | Defines a callback used to return the cause of the persistence failure. |
| [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | Function for initializing the reusable custom component. |
| [SetterCallback](arkts-arkui-settercallback-t.md) | Defines a callback used to set a value. |
| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md) | Obtains the default constructor. |
| [TaskCallback](arkts-arkui-taskcallback-t.md) | Defines a synchronous callback. |
| [TypeDecorator](arkts-arkui-typedecorator-t.md) | Defines the attribute decorator, which is used to decorate attributes of the custom class in a nested class. |
