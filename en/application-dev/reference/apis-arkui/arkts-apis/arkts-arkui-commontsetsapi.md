# common_ts_ets_api(System API)

## Summary

### Classes

| Name | Description |
| --- | --- |
| [AppStorage](arkts-arkui-appstorage-c.md) | AppStorage is the global UI state storage center bound to applications. It is created by the UI framework at application startup, which is used to store UI state data in runtime memory, and implement application-level global state sharing. For details about how to use it on the UI, see [AppStorage: Storing Application-wide UI State](../../../ui/state-management/arkts-appstorage.md). |
| [Environment](arkts-arkui-environment-c.md) | Provides the capability to query device environment states. It can inject system environment variables (such as the dark/light mode, language, font scale, and layout direction) into AppStorage, enabling applications to perceive and respond to device environment changes. For details about how to use it on the UI, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md). |
| [LocalStorage](arkts-arkui-localstorage-c.md) | A page-level UI state storage. The parameters received through the [@Entry](../../../apis-arkui/arkui-ts/ts-universal-entry.md#entry) decorator can share the same **LocalStorage** instance within a page. For details about how to use it on the UI, see [LocalStorage: Storing Page-Level UI State](../../../ui/state-management/arkts-localstorage.md). |
| [PersistentStorage](arkts-arkui-persistentstorage-c.md) | Provides the persistent storage capability for UI states. It persists selected AppStorage properties to a file and restores these property values from the file and writes them to AppStorage when applications restart. For details about how to use it on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md). |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md) | An object of a one-way or two-way synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). It is used to establish a data synchronization relationship with a property in AppStorage or LocalStorage. A **SubscribedAbstractProperty** instance needs to be manually released through the [aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted) API to cancel the synchronization relationship and invalidate the instance. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [Environment](arkts-arkui-environment-c-sys.md) | Provides the capability to query device environment states. It can inject system environment variables (such as the dark/light mode, language, font scale, and layout direction) into AppStorage, enabling applications to perceive and respond to device environment changes. For details about how to use it on the UI, see [Environment: Device Environment Query](../../../ui/state-management/arkts-environment.md). |
| [PersistentStorage](arkts-arkui-persistentstorage-c-sys.md) | Provides the persistent storage capability for UI states. It persists selected AppStorage properties to a file and restores these property values from the file and writes them to AppStorage when applications restart. For details about how to use it on the UI, see [PersistentStorage: Persisting Application State](../../../ui/state-management/arkts-persiststorage.md). |
| [SubscribaleAbstract](arkts-arkui-subscribaleabstract-c-sys.md) | A subscribable abstract class used to manage a collection of owned properties, providing the capabilities to add, remove, and notify property changes. |
| [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c-sys.md) | An object of a one-way or two-way synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). It is used to establish a data synchronization relationship with a property in AppStorage or LocalStorage. A **SubscribedAbstractProperty** instance needs to be manually released through the [aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted) API to cancel the synchronization relationship and invalidate the instance. |
| [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md) | Inherits from [SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-subscribedabstractproperty-c.md) to receive one-way synchronization of the parent component's state value. The value is updated when the parent component state changes. |
| [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md) | Inherits from [SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-subscribedabstractproperty-c.md) to implement two-way state data synchronization between parent and child components. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AbstractProperty](arkts-arkui-abstractproperty-i.md) | A reference to a property in AppStorage or LocalStorage. It provides the capabilities to read and modify referenced property data and query property names. Unlike **SubscribedAbstractProperty**, an **AbstractProperty** instance does not need to be manually released. |
| [EnvPropsOptions](arkts-arkui-envpropsoptions-i.md) | Defines a key-value pair object used to specify environment variable names and their default values, passed as a parameter to [envProps](arkts-arkui-environment-c.md#envprops). |
| [PersistPropsOptions](arkts-arkui-persistpropsoptions-i.md) | Defines a key-value pair object used to specify persistent properties and their default values, passed as a parameter to [persistProps](arkts-arkui-persistentstorage-c.md#persistprops). |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | A property subscriber API, which defines the methods that the subscriber needs to implement to receive property change notifications and lifecycle callbacks. |
| [ISinglePropertyChangeSubscriber](arkts-arkui-isinglepropertychangesubscriber-i-sys.md) | Inherits from [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) to subscribe to changes of a single property value. Notifications are received when the subscribed property changes. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [appStorage](arkts-arkui-commontsetsapi-con-sys.md#appstorage) | An application-level global state storage instance that provides state data storage and access capabilities within the application scope. |
<!--DelEnd-->
