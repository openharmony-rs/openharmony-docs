# FontOptions

```TypeScript
interface FontOptions
```

Information about the custom font to register.

> **NOTE:** 
> 
> Directly using **font** can lead to the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the
> [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context by using the
> [getFont](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).

**Since:** 9

<!--Device-font-interface FontOptions--><!--Device-font-interface FontOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## familyName

```TypeScript
familyName: string | Resource
```

Name of the font to register. It is recommended to use letters, digits, and underscores.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FontOptions-familyName: string | Resource--><!--Device-FontOptions-familyName: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## familySrc

```TypeScript
familySrc: string | Resource
```

File path of the font to register. This parameter supports **Resource** references, **$rawfile** paths, relative paths, and absolute paths.

**Note:** 

When reading resources in the system sandbox path, you are advised to use a string with the **file://** path prefix. Ensure that the file exists in the sandbox directory and has read permission.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-FontOptions-familySrc: string | Resource--><!--Device-FontOptions-familySrc: string | Resource-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
