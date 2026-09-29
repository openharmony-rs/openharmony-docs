# AddFormOptions

```TypeScript
export interface AddFormOptions
```

Defines the add form options.

**Since:** 12

<!--Device-unnamed-export interface AddFormOptions--><!--Device-unnamed-export interface AddFormOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AddFormMenuItem, FormMenuItemStyle, AddFormOptions } from '@kit.ArkUI';
```

## callback

```TypeScript
callback?: AsyncCallback<string>
```

The callback is used to return the form id.

**Type:** [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt;

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AddFormOptions-callback?: AsyncCallback<string>--><!--Device-AddFormOptions-callback?: AsyncCallback<string>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## formBindingData

```TypeScript
formBindingData?: formBindingData.FormBindingData
```

Indicates the form data.

**Type:** [formBindingData.FormBindingData](../../apis-form-kit/arkts-apis/arkts-form-formbindingdata-formbindingdata-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AddFormOptions-formBindingData?: formBindingData.FormBindingData--><!--Device-AddFormOptions-formBindingData?: formBindingData.FormBindingData-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: FormMenuItemStyle
```

The style of the menu item.

**Type:** [FormMenuItemStyle](arkts-arkui-arkui-advanced-formmenu-formmenuitemstyle-i.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-AddFormOptions-style?: FormMenuItemStyle--><!--Device-AddFormOptions-style?: FormMenuItemStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
