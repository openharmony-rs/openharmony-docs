# IPropertySubscriber (System API)

```TypeScript
interface IPropertySubscriber
```

A property subscriber API, which defines the methods that the subscriber needs to implement to receive property change notifications and lifecycle callbacks.

**Since:** 7

<!--Device-unnamed-interface IPropertySubscriber--><!--Device-unnamed-interface IPropertySubscriber-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## aboutToBeDeleted

```TypeScript
aboutToBeDeleted(owningView?: IPropertySubscriber): void
```

Called when the object is about to be destroyed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-IPropertySubscriber-aboutToBeDeleted(owningView?: IPropertySubscriber): void--><!--Device-IPropertySubscriber-aboutToBeDeleted(owningView?: IPropertySubscriber): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| owningView | [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md) | No | Custom component that owns the current property. If not passed, no associated custom component is specified. |

## id

```TypeScript
id(): number
```

Obtains the ID.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-IPropertySubscriber-id(): number--><!--Device-IPropertySubscriber-id(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Unique ID of the subscriber. |
