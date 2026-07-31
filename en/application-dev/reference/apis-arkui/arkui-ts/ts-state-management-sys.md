# State Management with Application-level Variables (System API)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhushilin0206-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=79e4597a11fe0470e85a7a6ec526decbb0cbcff4 translatedAt=2026-07-15T07:41:45.810Z pushedAt=2026-07-16T02:15:38.271Z -->

The state management module provides data storage, persistent data management, UIAbility data storage, and environment state management capabilities required by applications, which is suitable to scenarios such as cross-component state sharing, persistent data storage, and UIAbility data management.

>**NOTE**
>
>The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
>This topic describes only the system APIs provided by the module. For details about its public APIs, see [State Management with Application-level Variables](./ts-state-management.md).

## SubscribedAbstractProperty\<T\>

An abstract property base class of the state management module, providing property change notification and subscriber management capabilities and supporting the creation of one-way/two-way synchronized properties.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### subscribers\_

protected subscribers_: Set\<number\>

A set of subscribers.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description      |
|-----------|--------------|
|Set\<number\>  |Set of subscriber IDs. |

### id\_

private id_

Private member variable ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### info\_

private info_?

Variable information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(subscribeMe?: IPropertySubscriber,info?: string)

Constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber used to receive property change notifications. If not passed, no subscription relationship is established.    |
|info   |string   |No   |Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.   |

### id

id(): number

Called when obtaining the ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description      |
|-----------|--------------|
|number  |Unique ID of the subscription property. |

### createTwoWaySync

createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay\<T\>

Creates two-way synchronization. Data changes are transferred bidirectionally between the data source and the subscriber. When the subscription relationship is no longer needed, call [unlinkSuscriber()](#unlinksuscriber) to cancel the subscription (the subscriber ID is obtained through [IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)), or call [aboutToBeDeleted()](#abouttobedeleted-1) of the returned [SyncedPropertyTwoWay](#syncedpropertytwowayt) object to cancel the subscription.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber used to receive property change notifications. If not passed, no subscription relationship is established.    |
|info   |string   |No   |Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.   |

**Return value**

|Type  |Description      |
|-----------|--------------|
|[SyncedPropertyTwoWay\<T\>](#syncedpropertytwowayt)  |Two-way synchronized property.|

### createOneWaySync

createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay\<T\>

Creates one-way synchronization. Data changes are transferred only from the data source to the subscriber. When the subscription relationship is no longer needed, call [unlinkSuscriber()](#unlinksuscriber) to cancel the subscription (the subscriber ID is obtained through [IPropertySubscriber](#ipropertysubscriber).[id()](#id-1)), or call [aboutToBeDeleted()](#abouttobedeleted-2) of the returned [SyncedPropertyOneWay](#syncedpropertyonewayt) object to cancel the subscription.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber used to receive property change notifications. If not passed, no subscription relationship is established.    |
|info   |string   |No   |Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.   |

**Return value**

|Type  |Description      |
|-----------|--------------|
|[SyncedPropertyOneWay\<T\>](#syncedpropertyonewayt)  |One-way synchronized property. |

### unlinkSuscriber

unlinkSuscriber(subscriberId: number): void

Removes a subscriber.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscriberId   |number   |Yes   |ID of the subscriber to remove, obtained through [IPropertySubscriber](#ipropertysubscriber).[id()](#id-1).    |

### notifyHasChanged

protected notifyHasChanged(newValue: T): void

Notifies subscribers that the value has changed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes  |New value after the change.   |

### notifyPropertyRead

protected notifyPropertyRead(): void

Notifies subscribers that the property has been read.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### numberOfSubscrbers

numberOfSubscrbers(): number

Obtains the number of subscribers.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description      |
|-----------|--------------|
|number  |Number of subscribers.|

## IPropertySubscriber

A property subscriber API, which defines the methods that the subscriber needs to implement to receive property change notifications and lifecycle callbacks.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### id

id(): number

Obtains the ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description      |
|-----------|--------------|
|number  |Unique ID of the subscriber. |

### aboutToBeDeleted

aboutToBeDeleted(owningView?: IPropertySubscriber): void

Called when the object is about to be destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|owningView   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Custom component that owns the current property. If not passed, no associated custom component is specified.    |

## SyncedPropertyTwoWay\<T\>

Inherits from [SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt) to implement two-way state data synchronization between parent and child components.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### source\_

private source_

Data source for the two-way synchronized property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(source: SubscribedAbstractProperty\<T\>, subscribeMe?: IPropertySubscriber, info?: string)

Constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|source   |[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)   |Yes  |Data source for the two-way synchronized property.   |
|subscribeMe|[IPropertySubscriber](#ipropertysubscriber)|No|Subscriber used to receive property change notifications. If not passed, no subscription relationship is established.|
|info|string|No|Variable information used to identify the subscription relationship. If not passed, the default value is **undefined**.|

### aboutToBeDeleted

aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void

Called when the object is about to be destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|unsubscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber to remove. If not passed, all subscribers are removed.    |

### hasChanged

hasChanged(newValue: T): void

Notifies subscribers that the property value has changed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description  |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes   |New value after the change.     |

### get

get(): T

Obtains the current value of the property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description    |
|------|------------|
|T   |Current data value of the two-way synchronized property.    |

### set

set(newValue: T): void

Sets a new value for the property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes   |New value to set.    |

## SyncedPropertyOneWay\<T\>

Inherits from [SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt) to receive one-way synchronization of the parent component's state value. The value is updated when the parent component state changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### wrappedValue\_

private wrappedValue_

Value used for one-way binding.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### source\_

private source_

A data source for the one-way synchronized property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(source: SubscribedAbstractProperty\<T\>, subscribeMe?: IPropertySubscriber, info?: string)

Constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|source   |[SubscribedAbstractProperty\<T\>](#subscribedabstractpropertyt)   |Yes  |Data source for the one-way synchronized property.   |
|subscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber used to receive property change notifications. If not passed, no subscription relationship is established.   |
|info  |string   |No   |Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.   |

### aboutToBeDeleted

aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void

Called when the object is about to be destroyed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|unsubscribeMe   |[IPropertySubscriber](#ipropertysubscriber)   |No   |Subscriber to remove. If not passed, all subscribers are removed.    |

### hasChanged

hasChanged(newValue: T): void

Notifies subscribers that the property value has changed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description  |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes   |New value after the change.     |

### get

get(): T

Obtains data.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description    |
|------|------------|
|T   |Current data value of the one-way synchronized property.    |

### set

set(newValue: T): void

Sets a new value for the property.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes   |New value to set.    |

## ISinglePropertyChangeSubscriber\<T\>

Inherits from [IPropertySubscriber](#ipropertysubscriber) to subscribe to changes of a single property value. Notifications are received when the subscribed property changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### hasChanged

hasChanged(newValue: T): void

Notifies subscribers that the property value has changed.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|newValue   |T   |Yes   |New value after the change.    |

## SubscribaleAbstract

A subscribable abstract class used to manage a collection of owned properties, providing the capabilities to add, remove, and notify property changes.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### owningProperties\_

private owningProperties_: Set\<number\>

A collection of owned properties.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

|Type  |Description    |
|------|------------|
|Set\<number\>   |Set of the IDs of the subscribers who own properties.    |

### constructor

constructor()

A constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### notifyPropertyHasChanged

protected notifyPropertyHasChanged(propName: string, newValue: any): void

Called when notifying a property change.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|propName   |string   |Yes  |Property name.   |
|newValue   |any   |Yes   |New value after the change.   |

### addOwningProperty

public addOwningProperty(subscriber: IPropertySubscriber): void

Adds a subscriber to the list of owned properties. When the property is no longer needed, call [removeOwningProperty](#removeowningproperty) or [removeOwningPropertyById](#removeowningpropertybyid) to remove the subscriber from the property list.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscriber   |[IPropertySubscriber](#ipropertysubscriber)   |Yes   |Subscriber to add, which will receive property change notifications.    |

### removeOwningProperty

public removeOwningProperty(property: IPropertySubscriber): void

Removes a subscriber from the list of owned properties.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|property|[IPropertySubscriber](#ipropertysubscriber)|Yes|Subscriber to remove, which must have been added through [addOwningProperty](#addowningproperty).|

### removeOwningPropertyById

public removeOwningPropertyById(subscriberId: number): void

Removes a subscriber from the list of owned properties by ID.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|subscriberId   |number   |Yes   |ID of the subscriber to remove. It must be the ID of the subscriber added through [addOwningProperty](#addowningproperty) and is obtained through [IPropertySubscriber](#ipropertysubscriber).[id()](#id-1).    |

## Environment

An environment class used to manage the environment state during application runtime, providing access to device environment properties.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

A constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## PersistentStorage

A persistent storage class used to manage persistent data of applications. It can associate specified AppStorage properties with persistent storage to persistently save and restore data.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor(appStorage: AppStorage, storage: Storage)

A constructor.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

|Name  |Type  |Mandatory  |Description            |
|---------|-----------|------------|--------------|
|appStorage   |AppStorage   |Yes   |Application-level storage object. PersistentStorage performs persistent management based on this object.    |
|storage   |Storage   |Yes   |Persistent storage object, used to actually read and write persistent data.    |

## appStorage

declare const appStorage: AppStorage

An application-level global state storage instance that provides state data storage and access capabilities within the application scope.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Type   |Description         |
|----------|------------|
|AppStorage   |Application-level global state storage instance.  |