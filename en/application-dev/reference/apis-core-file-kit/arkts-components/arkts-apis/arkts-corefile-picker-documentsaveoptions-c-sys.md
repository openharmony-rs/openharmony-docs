# DocumentSaveOptions

Defines the options for saving documents.

**Since:** 9

**System capability:** SystemCapability.FileManagement.UserFileService

## Modules to Import

```TypeScript
import { picker } from '@kit.CoreFileKit';
```

## themeColor

```TypeScript
themeColor?: CustomColors
```

Theme color parameter. By default, it is left empty and follows the color settings of the **FilePicker**. When it is set to specific theme color properties, such as [fontEmphasize and compBackgroundEmphasize](../../apis-arkui/arkts-apis/arkts-arkui-arkui-theme-colors-i.md), the launched **FilePicker** will adapt to the theme color accordingly. This API can be called on smartphones but has no effect on other devices.

**Type:** [CustomColors](../../apis-arkui/arkts-apis/arkts-arkui-customcolors-t.md)

**Since:** 18

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
