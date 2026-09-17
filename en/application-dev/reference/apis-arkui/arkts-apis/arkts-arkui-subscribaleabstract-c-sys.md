# SubscribaleAbstract (System API)

Defines the Subscribale base class.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## addOwningProperty

```TypeScript
public addOwningProperty(subscriber: IPropertySubscriber): void
```

Adds a subscriber to the list of owned properties.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriber | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | Yes | Subscriber. |

## constructor

```TypeScript
constructor()
```

Constructor.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## notifyPropertyHasChanged

```TypeScript
protected notifyPropertyHasChanged(propName: string, newValue: any): void
```

Notify subscribers that a property value has changed.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| propName | string | Yes | Property name. |
| newValue | any | Yes | New value after the change. |

## removeOwningProperty

```TypeScript
public removeOwningProperty(property: IPropertySubscriber): void
```

Removes a subscriber from the list of owned properties.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | Yes | Subscriber to remove. |

## removeOwningPropertyById

```TypeScript
public removeOwningPropertyById(subscriberId: number): void
```

Removes a subscriber from the list of owned properties by ID.

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| subscriberId | number | Yes | ID of the subscriber to remove. |

## owningProperties_

```TypeScript
private owningProperties_: Set<number>
```

A set of property IDs that this instance owns.

**Type:** Set&lt;number&gt;

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
