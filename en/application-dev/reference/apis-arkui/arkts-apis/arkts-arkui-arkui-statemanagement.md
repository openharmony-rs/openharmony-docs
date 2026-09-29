# @ohos.arkui.StateManagement(State Management)

This module provides capabilities for application data storage, data persistence management, and UIAbility
 (application component that contains a UI) data storage. It also covers scenarios such as environment state, tool,
 and UI state synchronization, helping you simplify state management logic and improve application responsiveness and
 data consistency.

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
| [@ComponentActive](arkts-arkui-arkui-statemanagement-componentactive-d.md#componentactive) | After a custom component transitions from the inactive state to the active state, the function decorated by **\@ComponentActive** is called. In the component reuse and recycling scenario, when a cached component is reused (that is, re-added to the node tree from the reuse pool), the component transitions from the inactive state to the active state, triggering this callback. |
| [@ComponentAppear](arkts-arkui-arkui-statemanagement-componentappear-d.md#componentappear) | Decorates a function that is called after a new instance of the custom component is created and before the **build()** function is executed. This callback is similar to **aboutToAppear**. The difference is that the **@ComponentAppear** callback is triggered only when the custom component is in the **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).INIT** state. The state variable can be changed in **@ComponentAppear**. The change will take effect in the subsequent **build()** function execution. |
| [@ComponentBuilt](arkts-arkui-arkui-statemanagement-componentbuilt-d.md#componentbuilt) | The function decorated by **\@ComponentBuilt** is called after the **build()** function of a custom component is executed for the first time, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).APPEARED** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**. You can implement functions that do not affect the actual UI, such as event data reporting, in this phase. |
| [@ComponentDisappear](arkts-arkui-arkui-statemanagement-componentdisappear-d.md#componentdisappear) | The function decorated by **\@ComponentDisappear** is executed before a custom component is destroyed, that is, it is triggered when the component transitions to the **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).DISAPPEARED** state. It is not recommended to change state variables in this function. In particular, modifying **\@Link** variables may cause unstable app behavior. |
| [@ComponentInactive](arkts-arkui-arkui-statemanagement-componentinactive-d.md#componentinactive) | After a custom component transitions from the active state to the inactive state, the function decorated by **\@ComponentInactive** is called. In the component reuse and recycling scenario, when a component is recycled to the reuse pool, the component transitions from the active state to the inactive state, triggering this callback. |
| [@ComponentInit](arkts-arkui-arkui-statemanagement-componentinit-d.md#componentinit) | The function decorated by **\@ComponentInit** is executed when the initialization of a custom component is about to complete, and is triggered before **\@ComponentAppear**. You can register lifecycle listeners and modify state variables at this time. The difference from **\@ComponentAppear** is that **\@ComponentInit** focuses on preparation operations in the initialization phase (such as listener registration), while **\@ComponentAppear** focuses on state changes before the component is about to be displayed. The two can be used together to respectively assume the responsibilities of initialization and pre-display. |
| [@ComponentRecycle](arkts-arkui-arkui-statemanagement-componentrecycle-d.md#componentrecycle) | After a component is recycled, the recycling operations such as resource release defined in the app are performed first. After the recycling is complete, the function decorated by **\@ComponentRecycle** is called, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED**. Then the component is frozen to avoid UI updates while the component is in the reuse pool. Finally, recycling recursively traverses all child components, and for each child component that completes recycling, the function decorated by **\@ComponentRecycle** in the child component is called. |
| [@ComponentReuse](arkts-arkui-arkui-statemanagement-componentreuse-d.md#componentreuse) | The function decorated by **\@ComponentReuse** is called when a reusable custom component is re-added to the node tree from the cache, that is, it is triggered in the stage from **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).RECYCLED** to **[CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md).BUILT**, to receive the construction parameters of the component. Finally, reuse recursively traverses all child components, and for each child component that completes reuse, the function decorated by **\@ComponentReuse** in the child component is called. |
| [@Type](arkts-arkui-arkui-statemanagement-type-d.md#type) | **\ |

### Classes

| Name | Description |
| --- | --- |
| [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md) | AppStorageV2 provides the capability of globally sharing state variables within an application. You can bind the same key through **connect** to share data across abilities. For details about the UI usage, see [AppStorageV2: Storing Application-wide UI State](../../../ui/state-management/arkts-new-appstoragev2.md). |
| [Binding](arkts-arkui-arkui-statemanagement-binding-c.md) | Represents the generic class for read-only data binding, which can bind data of any type. |
| [ConnectOptions](arkts-arkui-arkui-statemanagement-connectoptions-c.md) | Defines the parameter type for **globalConnect**. |
| [ConnectOptionsCollections](arkts-arkui-arkui-statemanagement-connectoptionscollections-c.md) | Defines the parameter type for the globalConnect API. **ConnectOptionsCollections** is inherited from [ConnectOptions\&lt;T\&gt;](arkts-arkui-arkui-statemanagement-connectoptions-c.md). You can use the **ConnectOptionsCollections** input parameter to persist container data (such as **Array\&lt;S&gt;**). |
| [MutableBinding](arkts-arkui-arkui-statemanagement-mutablebinding-c.md) | Represents a generic class for mutable data binding, which allows the read and write operations on the bound value and provides complete **get** and **set** accessors. |
| [PersistenceV2](arkts-arkui-arkui-statemanagement-persistencev2-c.md) | Provides persistent storage for UI states. This API is inherited from [AppStorageV2](arkts-arkui-arkui-statemanagement-appstoragev2-c.md). It supports persisting application state data to disks and restoring data after application restart, making it suitable for scenarios where UI state data needs to be retained. For details about the UI usage, see [PersistenceV2: Persisting UI States](../../../ui/state-management/arkts-new-persistencev2.md). |
| [UIUtils](arkts-arkui-arkui-statemanagement-uiutils-c.md) | Provides APIs related to state management, including obtaining the original object from a proxy object, converting non-observable data into observable data, dynamically adding and removing state variable listeners, synchronously refreshing state variable modifications, and creating data bindings. It is suitable for scenarios where manual management of state observation, listening, and synchronous refresh is required. |

### Interfaces

| Name | Description |
| --- | --- |
| [CustomComponentContext](arkts-arkui-arkui-statemanagement-customcomponentcontext-i.md) | The **CustomComponentContext** class provides access to component-level services, including the reuse pool. You can obtain an instance through [UIUtils.getCustomComponentContext](arkts-arkui-arkui-statemanagement-uiutils-c.md#getcustomcomponentcontext). |
| [CustomComponentLifecycle](arkts-arkui-arkui-statemanagement-customcomponentlifecycle-i.md) | **CustomComponentLifecycle** is used to monitor changes in the lifecycle of a custom component. You can obtain a **CustomComponentLifecycle** instance through [UIUtils.getLifecycle](arkts-arkui-arkui-statemanagement-uiutils-c.md#getlifecycle). |
| [CustomComponentLifecycleObserver](arkts-arkui-arkui-statemanagement-customcomponentlifecycleobserver-i.md) | After developers register a custom component lifecycle callback, when the lifecycle of the custom component changes, the corresponding lifecycle callback in the listener is triggered. The difference from the lifecycle decorators is that the lifecycle decorators respond to lifecycle events by the component itself, while **CustomComponentLifecycleObserver** observes component lifecycle events from the outside. If only the component itself needs to respond to lifecycle changes, use the lifecycle decorators. If you need to centrally monitor the lifecycles of multiple components, use **CustomComponentLifecycleObserver**. |
| [DecoratorInfo](arkts-arkui-arkui-statemanagement-decoratorinfo-i.md) | Defines the decorator and component information associated with the observable object. |
| [ElementInfo](arkts-arkui-arkui-statemanagement-elementinfo-i.md) | Defines information about the components associated with the observable object, including system components and custom components. |
| [IReusableInfo](arkts-arkui-arkui-statemanagement-ireusableinfo-i.md) | The **IReusableInfo** API provides information about the current number and maximum number of reusable components managed by the reuse pool. |
| [IReusePool](arkts-arkui-arkui-statemanagement-ireusepool-i.md) | Provides the features related to the global reuse pool of a custom component, including querying the current count and upper limit of recycled components and pre-rendering reusable components into the reuse pool. It is suitable for scenarios where you need to manually manage and optimize component reuse efficiency. |
| [MonitorOptions](arkts-arkui-arkui-statemanagement-monitoroptions-i.md) | Defines the optional parameters for [addMonitor](arkts-arkui-arkui-statemanagement-uiutils-c.md#addmonitor), which are used to configure the callback type and whether to enable the wildcard capability. |
| [ObservedResult](arkts-arkui-arkui-statemanagement-observedresult-i.md) | Provides the result of whether the object can be observed. |
| [TypeConstructor](arkts-arkui-arkui-statemanagement-typeconstructor-i.md) | Represents a class constructor. |
| [TypeConstructorWithArgs](arkts-arkui-arkui-statemanagement-typeconstructorwithargs-i.md) | Represents a class constructor that accepts arbitrary arguments. |

### Types

| Name | Description |
| --- | --- |
| [CollectionType](arkts-arkui-collectiontype-t.md) | Defines the types of persistent collection data supported by **globalConnect** using the generic type of the input parameter of **globalConnect**. |
| [GetterCallback](arkts-arkui-gettercallback-t.md) | Defines a callback used to obtain a value. |
| [MonitorCallback](arkts-arkui-monitorcallback-t.md) | A listener callback function of the [IMonitor](../arkts-components/arkts-arkui-common-comp-imonitor-i.md) type. |
| [PersistenceErrorCallback](arkts-arkui-persistenceerrorcallback-t.md) | Defines a callback used to return the cause of the persistence failure. |
| [ReusableComponentConstructor](arkts-arkui-reusablecomponentconstructor-t.md) | Function for initializing the reusable custom component. |
| [SetterCallback](arkts-arkui-settercallback-t.md) | Defines a callback used to set a value. |
| [StorageDefaultCreator](arkts-arkui-storagedefaultcreator-t.md) | Obtains the default constructor. |
| [TaskCallback](arkts-arkui-taskcallback-t.md) | Defines a synchronous callback. |
| [TypeDecorator](arkts-arkui-typedecorator-t.md) | Defines the attribute decorator, which is used to decorate attributes of the custom class in a nested class. |

### Enums

| Name | Description |
| --- | --- |
| [CustomComponentLifecycleState](arkts-arkui-arkui-statemanagement-customcomponentlifecyclestate-e.md) | Current lifecycle status of a custom component. |
