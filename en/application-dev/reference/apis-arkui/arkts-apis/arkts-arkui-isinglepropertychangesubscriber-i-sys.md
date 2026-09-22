# ISinglePropertyChangeSubscriber (System API)

```TypeScript
interface ISinglePropertyChangeSubscriber<T> extends IPropertySubscriber
```

Inherits from [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md). Represents a subscriber that subscribes to changes in a property value.

**Inheritance/Implementation:** ISinglePropertyChangeSubscriber extends [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

Notifies subscribers that the property value has changed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| newValue | T | Yes | Instance of the T type. |
