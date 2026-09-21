# on

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## on('selectionCompleted')

```TypeScript
function on(type: 'selectionCompleted', callback: Callback<SelectionInfo>): void
```

Subscribes to the word selection completion event. This API is used together with [off('selectionCompleted')](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted).

[off('selectionCompleted')](arkts-basicservices-selectionmanager-off-f.md#offselectioncompleted) is used to unsubscribe from the event.

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'selectionCompleted' | Yes | Event type, which is **'selectionCompleted'**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i.md)&gt; | Yes | Callback used to return [SelectionInfo](arkts-basicservices-selectionmanager-selectioninfo-i.md). This callback is triggered only when the user selects text using the mouse or touchpad (by double-clicking, triple-clicking, or sliding the left mouse button) and then presses **Ctrl**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600003](../errorcode-selection.md#33600003-api-caller-and-word-selection-application-mismatched) | The application calling the API does not match the application selected in the system settings. |

**Examples**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

try {
  // Subscribe to the word selection completion event.
  selectionManager.on('selectionCompleted', (info: selectionManager.SelectionInfo) => {
    console.info('Enter the callback function.');
  });
} catch (err) {
  console.error(`Failed to register selectionCompleted callback. Error code: ${err.code}, error message: ${err.message}`);
}
```
