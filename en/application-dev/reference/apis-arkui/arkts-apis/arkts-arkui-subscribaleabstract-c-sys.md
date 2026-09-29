# SubscribaleAbstract (System API)

```TypeScript
declare abstract class SubscribaleAbstract
```

A subscribable abstract class used to manage a collection of owned properties, providing the capabilities to add, remove, and notify property changes.

**Since:** 7

<!--Device-unnamed-declare abstract class SubscribaleAbstract--><!--Device-unnamed-declare abstract class SubscribaleAbstract-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## addOwningProperty

```TypeScript
public addOwningProperty(subscriber: IPropertySubscriber): void
```

Adds a subscriber to the list of owned properties. When the property is no longer needed, call [removeOwningProperty](#removeowningproperty) or [removeOwningPropertyById](#removeowningpropertybyid) to remove the subscriber from the property list.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public addOwningProperty(subscriber: IPropertySubscriber): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | Yes | Subscriber to add, which will receive property change notifications. |

## constructor

```TypeScript
constructor()
```

A constructor.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-constructor()--><!--Device-SubscribaleAbstract-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## notifyPropertyHasChanged

```TypeScript
protected notifyPropertyHasChanged(propName: string, newValue: any): void
```

Called when notifying a property change.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void--><!--Device-SubscribaleAbstract-protected notifyPropertyHasChanged(propName: string, newValue: any): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Name of the property whose change is to be notified. |
| newValue | any | Yes | New value after the change. |

## removeOwningProperty

```TypeScript
public removeOwningProperty(property: IPropertySubscriber): void
```

Removes a subscriber from the list of owned properties.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void--><!--Device-SubscribaleAbstract-public removeOwningProperty(property: IPropertySubscriber): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | Yes | Subscriber to remove, which must be the subscriber that has been added through [addOwningProperty](#addowningproperty). |

## removeOwningPropertyById

```TypeScript
public removeOwningPropertyById(subscriberId: number): void
```

Removes a subscriber from the list of owned properties by ID.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void--><!--Device-SubscribaleAbstract-public removeOwningPropertyById(subscriberId: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriberId | number | Yes | ID of the subscriber to remove. It must be the ID of the subscriber added through [addOwningProperty](#addowningproperty) and is obtained through [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md).[id()](arkts-arkui-ipropertysubscriber-i-sys.md#id). |

## owningProperties_

```TypeScript
private owningProperties_: Set<number>
```

A collection of owned properties.

**Type:** Set&lt;number&gt;

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-SubscribaleAbstract-private owningProperties_: Set<number>--><!--Device-SubscribaleAbstract-private owningProperties_: Set<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
