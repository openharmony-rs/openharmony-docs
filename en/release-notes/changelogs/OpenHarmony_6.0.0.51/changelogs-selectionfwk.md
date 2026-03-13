# Word Selection Service Framework Changelog

## cl.selectionfwk.1 The text Property Is Deleted from SelectionInfo Returned by the Word Selection Notification API

**Access Level**

System API

**Change Reason**

When the selection service detects that the user selects text, the returned [SelectionInfo](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager.md#selectioninfo) no longer contains the **text** property. In addition, the [getSelectionContent](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager.md#getselectioncontent) method is used to obtain the selected text content, thereby decoupling the word selection notification from the text content acquisition.

**Change Impact**

Application adaptation is required.

The decoupling of the word selection notification from the text content acquisition allows you to handle the behavior more flexibly after the word selection event is listened for. In addition, the **text** property is no longer returned, which may affect the existing code logic that depends on this property. You need to adjust the code logic based on the new API specifications.

**Start API Level**

22

**Change Since**

OpenHarmony SDK 6.0.0.51

**Key API/Component Changes**
| Class          | Property Deleted                                                |
| -------------- | ------------------------------------------------------------ |
| SelectionInfo | text: string |

**Adaptation Guide**

You need to adjust the existing code logic based on the new API specifications. After the word selection event is listened for, the [getSelectionContent](../../../application-dev/reference/apis-basic-services-kit/js-apis-selectionInput-selectionManager.md#getselectioncontent) method is used to obtain the selected text content.

```ts
selectionManager.on('selectionCompleted', async (info: selectionManagerSelectionInfo) => {
  try {
    let content = await selectionManager.getSelectionContent();
  } catch (err) {
    console.error(`Failed to get selection content: ${JSON.stringify(err)}`);
  }
});
```
