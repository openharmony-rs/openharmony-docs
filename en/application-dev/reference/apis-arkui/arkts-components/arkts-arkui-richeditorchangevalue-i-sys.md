# RichEditorChangeValue

Defines image and text change information.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changeReason

```TypeScript
changeReason?: TextChangeReason
```

Reason for the component content change, used to identify the operation type that triggers the content change (such as user input, paste, cut, and so on). It must be obtained by registering the onWillChange callback. Developers can make corresponding processing decisions for different change reasons in the onWillChange callback based on the value of changeReason. The default value of this field is undefined.

**Type:** [TextChangeReason](../arkts-apis/arkts-arkui-textchangereason-e-sys.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
