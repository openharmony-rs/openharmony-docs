# FontOptions

Information about the custom font to register.

> **NOTE:** 
> 
> Directly using **font** can lead to the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context). To avoid this, obtain the
> [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context by using the
> [getFont](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont) API in
> [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## familyName

```TypeScript
familyName: string | Resource
```

Name of the custom font to register.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## familySrc

```TypeScript
familySrc: string | Resource
```

Path of the custom font file to register.

**NOTE:** 

If the font file to specify is a resource located within the system sandbox directory, you are advised to use a string with the **file://** path prefix. Ensure the target file exists in the sandbox path and has read permissions granted.

**Type:** string &#124; [Resource](arkts-arkui-resource-t.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
