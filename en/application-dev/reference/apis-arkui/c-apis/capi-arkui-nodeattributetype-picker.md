# Picker

## Overview

Enumerates the attribute types that can be set by ArkUI on the native side.

**Since**: 12

**Related module**: [ArkUI_NativeModule](capi-arkui-arkui-nativemodule.md)

**Header file**: [native_node.h](capi-native-node-h.md)

### NODE_PICKER_SELECTED_TEXT_STYLE

```c
NODE_PICKER_SELECTED_TEXT_STYLE = 1018007
```

**Description**

Text style of the selected item of the <b>Picker</b> component. This property can be set, reset, and fetched on demand.<br> ** Parameter format of [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md) when setting attributes: * *<br><ul> <li>.object: text style of the selected item. The parameter type is [ArkUI_PickerComponentTextStyle](capi-arkui-nativemodule-arkui-pickercomponenttextstyle.md). Use [OH_ArkUI_PickerComponentTextStyle_Create](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_create) to create an instance. Use [OH_ArkUI_PickerComponentTextStyle_SetColor](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setcolor), [OH_ArkUI_PickerComponentTextStyle_SetFontSize](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setfontsize), [OH_ArkUI_PickerComponentTextStyle_SetFontWeight](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setfontweight), [OH_ArkUI_PickerComponentTextStyle_SetMinFontSize](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setminfontsize), [OH_ArkUI_PickerComponentTextStyle_SetMaxFontSize](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setmaxfontsize), [OH_ArkUI_PickerComponentTextStyle_SetOverflow](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_setoverflow) After the attribute is set, pass the pointer to **.object**. After the setting is complete, call [OH_ArkUI_PickerComponentTextStyle_Dispose](capi-picker-h.md#oh_arkui_pickercomponenttextstyle_dispose) to destroy the instance. If this parameter is not set, the default style is used. </li> </ul><br> ** Format of the return value [ArkUI_AttributeItem](capi-arkui-nativemodule-arkui-attributeitem.md): * *<br><ul> <li>.object: text style of the selected item. The parameter type is [ArkUI_PickerComponentTextStyle](capi-arkui-nativemodule-arkui-pickercomponenttextstyle.md). </li> </ul>

**Since**: 26.1.0


