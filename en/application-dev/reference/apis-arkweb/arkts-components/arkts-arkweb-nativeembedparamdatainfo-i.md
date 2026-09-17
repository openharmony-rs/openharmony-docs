# NativeEmbedParamDataInfo

Provides detailed information about the same-layer tag when the **param** element embedded in the **object** tag changes, including the tag ID and parameter items. It is suitable for scenarios where monitoring param element changes is required, improving same-layer element management flexibility and accuracy.

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## embedId

```TypeScript
embedId: string
```

Unique ID of the same-layer tag.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## objectAttributeId

```TypeScript
objectAttributeId?: string
```

ID of the same-layer tag.

**Type:** string

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core

## paramItems

```TypeScript
paramItems?: Array<NativeEmbedParamItem>
```

Detailed information about the changed param elements, including the status change type, ID, parameter name, and parameter value of each param element.

**Type:** Array&lt;[NativeEmbedParamItem](arkts-arkweb-nativeembedparamitem-i.md)&gt;

**Since:** 21

**System capability:** SystemCapability.Web.Webview.Core
