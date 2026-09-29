# NativeEmbedParamItem

```TypeScript
declare interface NativeEmbedParamItem
```

Provides detailed information about the **param** element embedded in the same-layer rendering tag **object**, including the status and parameters. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy.

**Since:** 21

<!--Device-unnamed-declare interface NativeEmbedParamItem--><!--Device-unnamed-declare interface NativeEmbedParamItem-End-->

**System capability:** SystemCapability.Web.Webview.Core

## id

```TypeScript
id: string
```

ID of the **param** element.

**Type:** string

**Since:** 21

<!--Device-NativeEmbedParamItem-id: string--><!--Device-NativeEmbedParamItem-id: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## name

```TypeScript
name?: string
```

Name of the **param** element.

**Type:** string

**Since:** 21

<!--Device-NativeEmbedParamItem-name?: string--><!--Device-NativeEmbedParamItem-name?: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## status

```TypeScript
status: NativeEmbedParamStatus
```

Status change type of the **param** element.

**Type:** [NativeEmbedParamStatus](arkts-arkweb-web-comp-nativeembedparamstatus-e.md)

**Since:** 21

<!--Device-NativeEmbedParamItem-status: NativeEmbedParamStatus--><!--Device-NativeEmbedParamItem-status: NativeEmbedParamStatus-End-->

**System capability:** SystemCapability.Web.Webview.Core

## value

```TypeScript
value?: string
```

Value of the **param** element.

**Type:** string

**Since:** 21

<!--Device-NativeEmbedParamItem-value?: string--><!--Device-NativeEmbedParamItem-value?: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
