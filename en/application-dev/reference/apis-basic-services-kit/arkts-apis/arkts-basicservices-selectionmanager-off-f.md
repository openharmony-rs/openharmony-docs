# off

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## off('selectionCompleted')

```TypeScript
function off(type: 'selectionCompleted', callback?: Callback<SelectionInfo>): void
```

Unsubscribes from the word selection completion event. This API is used together with [on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted).

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectionCompleted' | Yes | Type of the event to unsubscribe from. The value is fixed to **'selectionCompleted'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i.md)&gt; | No | Callback to be unregistered, which the callback instance registered using **on**. If this parameter is not specified, this API unregisters all callbacks for the specified type. |
