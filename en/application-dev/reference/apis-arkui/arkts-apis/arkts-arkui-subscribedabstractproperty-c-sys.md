# SubscribedAbstractProperty

```TypeScript
declare abstract class SubscribedAbstractProperty<T>
```

An object of a one-way or two-way synchronized property in [AppStorage](../../../ui/state-management/arkts-appstorage.md) or [LocalStorage](../../../ui/state-management/arkts-localstorage.md). It is used to establish a data synchronization relationship with a property in AppStorage or LocalStorage. A **SubscribedAbstractProperty** instance needs to be manually released through the [aboutToBeDeleted](arkts-arkui-subscribedabstractproperty-c.md#abouttobedeleted) API to cancel the synchronization relationship and invalidate the instance.

> **NOTE:** 

> Since API version 12, AppStorage and LocalStorage support the **Map**, **Set**, and **Date** types, as well as
> **null**, **undefined**, and union types.

**Since:** 9

<!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>--><!--Device-unnamed-declare abstract class SubscribedAbstractProperty<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(
    /**
     * Subscriber used to receive property change notifications. If not passed, no subscription relationship is
     * established.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @systemapi
     * @since 7
     * 
     */
    subscribeMe?: IPropertySubscriber,
    /**
     * Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.
     *
     * @syscap SystemCapability.ArkUI.ArkUI.Full
     * @systemapi
     * @since 7
     * 
     */
    info?: string,
  )
```

Constructor. If the **subscribeMe** parameter has been passed in to establish a subscription relationship, call [unlinkSuscriber()](#unlinksuscriber) to unsubscribe when the subscription relationship is no longer needed (the subscriber ID is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)).

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-constructor(    /**     * Subscriber used to receive property change notifications. If not passed, no subscription relationship is     * established.     *     * @syscap SystemCapability.ArkUI.ArkUI.Full     * @systemapi     * @since 7     *      */    subscribeMe?: IPropertySubscriber,    /**     * Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.     *     * @syscap SystemCapability.ArkUI.ArkUI.Full     * @systemapi     * @since 7     *      */    info?: string,  )--><!--Device-SubscribedAbstractProperty-constructor(    /**     * Subscriber used to receive property change notifications. If not passed, no subscription relationship is     * established.     *     * @syscap SystemCapability.ArkUI.ArkUI.Full     * @systemapi     * @since 7     *      */    subscribeMe?: IPropertySubscriber,    /**     * Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed.     *     * @syscap SystemCapability.ArkUI.ArkUI.Full     * @systemapi     * @since 7     *      */    info?: string,  )-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber used to receive property change notifications. If not passed, no subscription relationship is established. |
| info | string | No | Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed. |

## createOneWaySync

```TypeScript
createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>
```

Creates one-way synchronization. Data changes are transferred only from the data source to the subscriber. When the subscription relationship is no longer needed, call [unlinkSuscriber()](#unlinksuscriber) to cancel the subscription (the subscriber ID is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)), or call [aboutToBeDeleted()](arkts-arkui-syncedpropertyoneway-c-sys.md#abouttobedeleted) of the returned [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md) object to cancel the subscription.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>--><!--Device-SubscribedAbstractProperty-createOneWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyOneWay<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber used to receive property change notifications. If not passed, no subscription relationship is established. |
| info | string | No | Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed. |

**Return value:**

| Type | Description |
| --- | --- |
| [SyncedPropertyOneWay](arkts-arkui-syncedpropertyoneway-c-sys.md)&lt;T&gt; | One-way synchronized property object created, which is used to receive one-way synchronization of the parent component's state value and update its own value when the parent component's state changes. |

## createTwoWaySync

```TypeScript
createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>
```

Creates two-way synchronization. Data changes are transferred bidirectionally between the data source and the subscriber. Compared with [createOneWaySync](#createonewaysync), this API supports two-way synchronization between the data source and the subscriber, and is suitable for scenarios where the subscriber also needs to modify the data source in reverse. If only one-way synchronization from the data source to the subscriber is required, use [createOneWaySync](#createonewaysync). When the subscription relationship is no longer needed, call [unlinkSuscriber()](#unlinksuscriber) to unsubscribe (the subscriber ID is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)), or call [aboutToBeDeleted()](arkts-arkui-syncedpropertytwoway-c-sys.md#abouttobedeleted) of the returned [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md) object to cancel the subscription.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>--><!--Device-SubscribedAbstractProperty-createTwoWaySync(subscribeMe?: IPropertySubscriber, info?: string): SyncedPropertyTwoWay<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber used to receive property change notifications. If not passed, no subscription relationship is established. |
| info | string | No | Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed. |

**Return value:**

| Type | Description |
| --- | --- |
| [SyncedPropertyTwoWay](arkts-arkui-syncedpropertytwoway-c-sys.md)&lt;T&gt; | Two-way synchronized property object created, used for two-way data synchronization and read/write operations between the data source and the subscriber. |

## id

```TypeScript
id(): number
```

Called when obtaining the ID.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-id(): number--><!--Device-SubscribedAbstractProperty-id(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique ID of the subscription property. |

## notifyHasChanged

```TypeScript
protected notifyHasChanged(newValue: T): void
```

Notifies subscribers that the value has changed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-protected notifyHasChanged(newValue: T): void--><!--Device-SubscribedAbstractProperty-protected notifyHasChanged(newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | New value after the change. |

## notifyPropertyRead

```TypeScript
protected notifyPropertyRead(): void
```

Notifies subscribers that the property has been read.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-protected notifyPropertyRead(): void--><!--Device-SubscribedAbstractProperty-protected notifyPropertyRead(): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## numberOfSubscrbers

```TypeScript
numberOfSubscrbers(): number
```

Obtains the number of subscribers.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-numberOfSubscrbers(): number--><!--Device-SubscribedAbstractProperty-numberOfSubscrbers(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of subscribers. |

## unlinkSuscriber

```TypeScript
unlinkSuscriber(subscriberId: number): void
```

Removes a subscriber based on the subscriber ID.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-unlinkSuscriber(subscriberId: number): void--><!--Device-SubscribedAbstractProperty-unlinkSuscriber(subscriberId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriberId | number | Yes | ID of the subscriber to remove. It must be a subscriber ID that has established a subscription relationship through [createTwoWaySync](#createtwowaysync) or [createOneWaySync](#createonewaysync), and is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id). |

## id_

```TypeScript
private id_
```

Unique ID of the subscription property, used to distinguish different subscription property instances in subscription relationship management.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-private id_--><!--Device-SubscribedAbstractProperty-private id_-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## info_

```TypeScript
private info_?
```

Variable information used to identify the subscription relationship.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-private info_?--><!--Device-SubscribedAbstractProperty-private info_?-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## subscribers_

```TypeScript
protected subscribers_: Set<number>
```

A set of subscribers.

**Type:** Set&lt;number&gt;

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribedAbstractProperty-protected subscribers_: Set<number>--><!--Device-SubscribedAbstractProperty-protected subscribers_: Set<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
