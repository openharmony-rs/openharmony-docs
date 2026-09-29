# SyncedPropertyTwoWay (System API)

```TypeScript
declare class SyncedPropertyTwoWay<T> extends SubscribedAbstractProperty<T>
  implements ISinglePropertyChangeSubscriber<T>
```

Inherits from [SubscribedAbstractProperty&lt;T&gt;](arkts-arkui-subscribedabstractproperty-c.md) to implement two-way state data synchronization between parent and child components.

**Inheritance/Implementation:** SyncedPropertyTwoWay extends SubscribedAbstractProperty<T> and implements ISinglePropertyChangeSubscriber<T>

**Since:** 7

<!--Device-unnamed-declare class SyncedPropertyTwoWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>--><!--Device-unnamed-declare class SyncedPropertyTwoWay<T> extends SubscribedAbstractProperty<T>  implements ISinglePropertyChangeSubscriber<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void
```

Called when the object is about to be destroyed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyTwoWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void--><!--Device-SyncedPropertyTwoWay-aboutToBeDeleted(unsubscribeMe?: IPropertySubscriber): void-End-->

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

Constructor. When the subscription relationship is no longer needed, call [unlinkSuscriber()](arkts-arkui-subscribedabstractproperty-c-sys.md#unlinksuscriber) to unsubscribe (the subscriber ID is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id)), or call [aboutToBeDeleted()](#abouttobedeleted) of this object to cancel the subscription.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyTwoWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)--><!--Device-SyncedPropertyTwoWay-constructor(source: SubscribedAbstractProperty<T>, subscribeMe?: IPropertySubscriber, info?: string)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [SubscribedAbstractProperty](arkts-arkui-subscribedabstractproperty-c.md)&lt;T&gt; | Yes | Data source for the two-way synchronized property. |
| subscribeMe | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Subscriber used to receive property change notifications. If not passed, no subscription relationship is established. |
| info | string | No | Variable information used to identify the subscription relationship. If not passed, the default value is **undefined**. |

## get

```TypeScript
get(): T
```

Obtains the current value of the property.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyTwoWay-get(): T--><!--Device-SyncedPropertyTwoWay-get(): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| T | Current data value of the two-way synchronized property. |

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

Notifies subscribers that the property value has changed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyTwoWay-hasChanged(newValue: T): void--><!--Device-SyncedPropertyTwoWay-hasChanged(newValue: T): void-End-->

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

<!--Device-SyncedPropertyTwoWay-set(newValue: T): void--><!--Device-SyncedPropertyTwoWay-set(newValue: T): void-End-->

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

Data source for the two-way synchronized property.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SyncedPropertyTwoWay-private source_--><!--Device-SyncedPropertyTwoWay-private source_-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
