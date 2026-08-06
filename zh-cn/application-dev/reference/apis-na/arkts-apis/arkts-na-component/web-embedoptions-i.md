# EmbedOptions

Defines the Embed Options.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface EmbedOptions--><!--Device-unnamed-export declare interface EmbedOptions-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## supportCssDisplayChange

```TypeScript
supportCssDisplayChange?: boolean
```

Whether the \_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ event supports display-related attributes of the embed element. \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_Default value is false. If true, the changes of the display-related attributes of the embed element will be reported through the \_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ event.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-EmbedOptions-supportCssDisplayChange?: boolean--><!--Device-EmbedOptions-supportCssDisplayChange?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## supportDefaultIntrinsicSize

```TypeScript
supportDefaultIntrinsicSize?: boolean
```

Whether the embed element support the default intrinsic size of 300 * 150, expressed in CSS pixels. \_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_When CSS size is set, the embed element size is CSS size, otherwise it is intrinsic size. \_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_If true, then the intrinsic size is 300 * 150. \_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_If false, the embed element will not be rendered when the CSS size is not set.

**类型：** boolean

**默认值：** false

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-EmbedOptions-supportDefaultIntrinsicSize?: boolean--><!--Device-EmbedOptions-supportDefaultIntrinsicSize?: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

