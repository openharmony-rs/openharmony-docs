# EmbedOptions

Configuration for Web same-layer rendering. Configures Web same-layer rendering options, including support for fixed size and CSS display properties. It is suitable for scenarios where same-layer element rendering optimization is required, improving rendering compatibility and flexibility.

**Since:** 16

**System capability:** SystemCapability.Web.Webview.Core

## supportCssDisplayChange

```TypeScript
supportCssDisplayChange?: boolean
```

Whether the same-layer rendering visibility API supports the display attribute.

By default, the visibility status of same-layer tags relative to the viewport is supported.

If this attribute is set to **true**, CSS attributes can be displayed, including visibility, display, width, and height.

Otherwise, CSS attributes are not displayed, and only same-layer tags are visible relative to the viewport.

**Type:** boolean

**Default:** false

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

## supportDefaultIntrinsicSize

```TypeScript
supportDefaultIntrinsicSize?: boolean
```

Whether a same-layer rendering element supports the fixed size of 300 × 150.

When the size of an element is set using CSS on the HTML5 side, the size of the same-layer rendering element uses the CSS size. Otherwise, the size is fixed.

If the value is **true**, the fixed size is 300 × 150.

If the value is **false** and the CSS size is not set on the HTML5 side, the same-layer rendering elements are not rendered.

Default value: **false**.

Unit: px.

**Type:** boolean

**Default:** false

**Since:** 16

**System capability:** SystemCapability.Web.Webview.Core

## supportTransformRotateAndSkew

```TypeScript
supportTransformRotateAndSkew?: boolean
```

Whether the same-layer rendering component supports CSS transform rotate and skew. This attribute takes effect only when enableNativeEmbedMode is enabled and cannot be dynamically modified. When set to **true**, the same-layer rendering component correctly handles CSS transform rotate/skew. When set to **false** or not set, retains the original behavior.

**Type:** boolean

**Default:** false

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Web.Webview.Core
