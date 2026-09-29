# OH_ArkUI_LeadingMarginSpanDrawInfo
 <!--Kit: ArkUI-->
 <!--Subsystem: ArkUI-->
 <!--Owner: @carnivore233-->
 <!--Designer: @carnivore233-->
 <!--Tester: @mateng_Holtens-->
 <!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=c5dd4bab7b6a1b4fcec6d309a7c458e4b5f07035 translatedAt=2026-09-22T09:23:26.529Z pushedAt=2026-09-22T11:51:39.236Z -->

```c
typedef struct OH_ArkUI_LeadingMarginSpanDrawInfo OH_ArkUI_LeadingMarginSpanDrawInfo
```

## Overview

Defines the custom drawing information for leading margin indentation, including the drawing context information of the current line (such as the drawing area and offset). You can implement custom leading margin indentation drawing logic in the callback function based on this information. It is applicable to scenarios such as adding custom icons or decorative elements to the first line of a paragraph, or implementing special indentation styles, making paragraph layout more flexible and rich. For example, draw a bookmark icon for the first line of a paragraph in a reader application, or draw a custom indentation marker for a specific paragraph in a document editor.<br>Call [OH_ArkUI_LeadingMarginSpanDrawInfo_Create](capi-styled-string-h.md#oh_arkui_leadingmarginspandrawinfo_create) to create the corresponding custom drawing information object for leading margin indentation.<br>Call [OH_ArkUI_LeadingMarginSpanDrawInfo_Destroy](capi-styled-string-h.md#oh_arkui_leadingmarginspandrawinfo_destroy) to destroy the object.<br>This object is used in the callback function registered by [OH_ArkUI_ParagraphStyle_RegisterOnDrawLeadingMarginCallback](capi-styled-string-h.md#oh_arkui_paragraphstyle_registerondrawleadingmargincallback) to provide the drawing context of the current line and the custom drawing information object.

**Since**: 24

**Related module**: [ArkUI_NativeModule](capi-arkui-nativemodule.md)

**Header file**: [styled_string.h](capi-styled-string-h.md)