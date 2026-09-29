# SyncedPropertyOneWay (System API)

```TypeScript
declare class SyncedPropertyOneWay<T> extends SubscribedAbstractProperty<T>
  implements ISinglePropertyChangeSubscriber<T>
```

Inherits from [SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-subscribedabstractproperty-c.md) to receive one-way synchronization of the parent component's state value. The value is updated when the parent component state changes.

**Inheritance/Implementation:** SyncedPropertyOneWay extends SubscribedAbstractProperty<T> and implements ISinglePropertyChangeSubscriber<T>

**Since:** 7

<!--Device-unnamed-declare class SyncedPropertyOneWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>--><!--Device-unnamed-declare class SyncedPropertyOneWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void
```

Called when the object is about to be destroyed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void--><!--Device-SyncedPropertyOneWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| unsubscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber to remove, which must be the subscriber who has established a subscription relationship. If not passed, all subscribers are removed. |

## constructor

```TypeScript
constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)
```

Constructor. When the subscription relationship is no longer needed, call [unlinkSuscriber](arkts-arkui-subscribedabstractproperty-c-sys.md#unlinksuscriber) to unsubscribe (the subscriber ID is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)), or call [aboutToBeDeleted()](#abouttobedeleted) of this object to cancel the subscription.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)--><!--Device-SyncedPropertyOneWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Yes | Data source for the one-way synchronized property. |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber used to receive property change notifications. If not passed, no subscription relationship is established. |
| info | string | No | Variable information used to identify the subscription relationship. Defaults to **undefined** if not passed. |

## get

```TypeScript
get(): T
```

Obtains data.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-get(): T--><!--Device-SyncedPropertyOneWay-get(): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| T | Current data value of the one-way synchronized property. |

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

Notifies subscribers that the property value has changed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-hasChanged(newValue: T): void--><!--Device-SyncedPropertyOneWay-hasChanged(newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | New value after the change. |

## set

```TypeScript
set(newValue: T): void
```

Sets a new value for the property.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-set(newValue: T): void--><!--Device-SyncedPropertyOneWay-set(newValue: T): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | New value to set. |

## source_

```TypeScript
private source_
```

A data source for the one-way synchronized property.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-private source_--><!--Device-SyncedPropertyOneWay-private source_-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## wrappedValue_

```TypeScript
private wrappedValue_
```

Value used for one-way binding.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyOneWay-private wrappedValue_--><!--Device-SyncedPropertyOneWay-private wrappedValue_-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
