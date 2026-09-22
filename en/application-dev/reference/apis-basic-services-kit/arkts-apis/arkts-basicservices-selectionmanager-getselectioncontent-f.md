# getSelectionContent

## Modules to Import

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';
```

## getSelectionContent

```TypeScript
function getSelectionContent(): Promise<string>
```

Obtains the content of the selected text. This API uses a promise to return the result. This API must be called in the [on('selectionCompleted')](arkts-basicservices-selectionmanager-on-f.md#onselectioncompleted) callback and is valid only after the word selection completion event is triggered.

**Since:** 24

**System capability:** SystemCapability.SelectionInput.Selection

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the content of the selected text. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [33600001](../errorcode-selection.md#33600001-word-selection-service-invocation-error) | Selection service invocation exception. |
| [33600004](../errorcode-selection.md#33600004-the-api-is-called-too-frequently) | The interface is called too frequently. |
| [33600005](../errorcode-selection.md#33600005-incorrect-api-call-timing) | The interface is called at the wrong time. |
| [33600006](../errorcode-selection.md#33600006-word-selection-prohibited-in-the-current-application) | The current application is prohibited from accessing content. |
| [33600007](../errorcode-selection.md#33600007-selected-text-is-out-of-range) | The length of selected content is out of range. |
| [33600008](../errorcode-selection.md#33600008-content-acquisition-timed-out) | Getting the selected content times out. |

**Examples**

```TypeScript
import { selectionManager } from '@kit.BasicServicesKit';

// Subscribe to the word selection completion event and obtain the selected text in the callback.
selectionManager.on('selectionCompleted', async (info: selectionManager.SelectionInfo) => {
  try {
    // Obtain the content of the selected text.
    let content = await selectionManager.getSelectionContent();
    console.info(`Succeeded in getting selection content: ${content}`);
  } catch (err) {
    console.error(`Failed to get selection content. Error code: ${err.code}, error message: ${err.message}`);
  }
});
```
