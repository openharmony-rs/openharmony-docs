# WebCustomScheme

Defines a custom URL scheme.

@interface WebCustomScheme [since 9 - 11]

**Since:** 9

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## isCodeCacheSupported

```TypeScript
isCodeCacheSupported?: boolean
```

Whether JavaScript resources of the scheme with this option set support code cache generation.

**true** indicates that JavaScript resources of the scheme with this option set support code cache generation, and **false** indicates that they do not support code cache generation.

Default value: false.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## isCspBypassing

```TypeScript
isCspBypassing?: boolean
```

Whether the scheme with this option set can bypass Content Security Policy (CSP) checks.

**true** indicates that the scheme with this option set can bypass CSP checks, and **false** indicates that it cannot bypass CSP checks.

Default value: true.

When **isStandard** is set to **true**, this value should not be set. If **isCspBypassing** is still set to **true** in this case, the CSP bypass behavior may not meet expectations.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isDisplayIsolated

```TypeScript
isDisplayIsolated?: boolean
```

Whether the content of the scheme with this option set can only be displayed or accessed from other content of the same scheme.

**true** indicates that the content of the scheme with this option set can only be displayed or accessed from other content of the same scheme, and **false** indicates that the content of the scheme with this option set can be displayed or accessed from content of other schemes.

Default value: true.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isLocal

```TypeScript
isLocal?: boolean
```

Whether the scheme is treated with the same security rules as those applied to file URLs.

The value **true** indicates that the scheme is treated with the same security rules as those applied to file URLs, and the value **false** indicates the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isSecure

```TypeScript
isSecure?: boolean
```

Whether the scheme is treated with the same security rules as those applied to HTTPS URLs. The value **true** indicates that the scheme is treated with the same security rules as those applied to HTTPS URLs, and **false** indicates the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isStandard

```TypeScript
isStandard?: boolean
```

Whether the scheme with this option set is processed as a standard scheme. A standard scheme must comply with the URL parsing rules defined in RFC 1738 section 3.1 and the URL normalization rules defined in RFC 3986 section 6.2.

**true** indicates that the scheme with this option set is processed as a standard scheme, and **false** indicates that it is not processed as a standard scheme.

Default value: true.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## isSupportCORS

```TypeScript
isSupportCORS: boolean
```

Whether to support cross-origin resource sharing (CORS).

The value **true** means to support cross-origin resource sharing (CORS), and **false** means the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## isSupportFetch

```TypeScript
isSupportFetch: boolean
```

Whether to support fetch requests.

The value **true** means to support fetch requests, and **false** means the opposite.

Default value: **true**.

**Type:** boolean

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## schemeName

```TypeScript
schemeName: string
```

Custom protocol name. The maximum length is 32, and only lowercase letters, digits, '.', '+', and '-' are supported. It must start with a letter. If the preceding restrictions are not met, the custom protocol configuration does not take effect.

**Type:** string

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
