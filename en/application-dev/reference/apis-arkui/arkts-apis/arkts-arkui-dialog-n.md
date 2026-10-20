# dialog(Dialog Box)

```TypeScript
declare namespace dialog
```

Provides unified dialog APIs.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare namespace dialog--><!--Device-unnamed-declare namespace dialog-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i.md) | Base options shared by all dialog types. |
| [DialogButton](arkts-arkui-dialog-dialogbutton-i.md) | Button configuration for fixed-style dialog. |
| [DialogCustomOptions](arkts-arkui-dialog-dialogcustomoptions-i.md) | Options for the custom-style dialog. The dialog content is provided as the first parameter of present() method, not inside this options object. |
| [DialogMessage](arkts-arkui-dialog-dialogmessage-i.md) | Message options for the dialog box, combining message content with text style. |
| [DialogSheet](arkts-arkui-dialog-dialogsheet-i.md) | The information of sheet item for action sheet style. |
| [DialogStyleOptions](arkts-arkui-dialog-dialogstyleoptions-i.md) | Options for the fixed-style dialog. |
| [DialogTextStyleOptions](arkts-arkui-dialog-dialogtextstyleoptions-i.md) | Defines DialogTextStyleOptions in the dialog. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [DialogBaseOptions](arkts-arkui-dialog-dialogbaseoptions-i-sys.md) | Base options shared by all dialog types. |
<!--DelEnd-->
