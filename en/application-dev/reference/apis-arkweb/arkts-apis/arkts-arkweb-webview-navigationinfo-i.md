# NavigationInfo

```TypeScript
interface NavigationInfo
```

Navigation information passed to the [NavigationThrottle](arkts-arkweb-webview-navigationthrottle-i.md) callback. Different fields are valid in different callback phases:  
- **willStartRequest**: url, isMainFrame, hasUserGesture, pageTransition, requestMethod, and isRendererInitiated  
are valid.  
- **willRedirectRequest**: url (redirect target), isMainFrame, hasUserGesture, isRedirect, pageTransition,  
requestMethod and isRendererInitiated are valid.  
- **willProcessResponse**: URL, isMainFrame, statusCode, mimeType, and contentDisposition are valid.  
- **willFailRequest**: URL, isMainFrame, errorCode, and errorDescription are valid.

**Since:** 26.1.0

<!--Device-webview-interface NavigationInfo--><!--Device-webview-interface NavigationInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## contentDisposition

```TypeScript
contentDisposition: string
```

Content-Disposition header of the response. This parameter is valid only in willProcessResponse.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-contentDisposition: string--><!--Device-NavigationInfo-contentDisposition: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## errorCode

```TypeScript
errorCode: WebNetErrorList
```

Network error code. This parameter is valid only in willFailRequest. See [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md) for details.

**Type:** [WebNetErrorList](arkts-arkweb-web-neterrorlist-webneterrorlist-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-errorCode: WebNetErrorList--><!--Device-NavigationInfo-errorCode: WebNetErrorList-End-->

**System capability:** SystemCapability.Web.Webview.Core

## errorDescription

```TypeScript
errorDescription: string
```

Error description. This parameter is valid only in willFailRequest.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-errorDescription: string--><!--Device-NavigationInfo-errorDescription: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## hasUserGesture

```TypeScript
hasUserGesture: boolean
```

Whether navigation is triggered by user gestures.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-hasUserGesture: boolean--><!--Device-NavigationInfo-hasUserGesture: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

Whether to navigate the main frame.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-isMainFrame: boolean--><!--Device-NavigationInfo-isMainFrame: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isRedirect

```TypeScript
isRedirect: boolean
```

Indicates whether redirection is performed on the server. This parameter is valid only in willRedirectRequest.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-isRedirect: boolean--><!--Device-NavigationInfo-isRedirect: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## isRendererInitiated

```TypeScript
isRendererInitiated: boolean
```

Whether navigation is initiated by the rendering process. `true` indicates that it is initiated by the rendering process(such as clicking a link or redirecting a script). `false` indicates that the request is initiated by a browser process (for example, through an API). Valid for the first time in the willStartRequest phase; The subsequent phases remain the same.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-isRendererInitiated: boolean--><!--Device-NavigationInfo-isRendererInitiated: boolean-End-->

**System capability:** SystemCapability.Web.Webview.Core

## mimeType

```TypeScript
mimeType: string
```

MIME(Multipurpose Internet Mail Extensions) type of the response. This parameter is valid only in willProcessResponse.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-mimeType: string--><!--Device-NavigationInfo-mimeType: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## pageTransition

```TypeScript
pageTransition: number
```

Page redirection value, which is obtained by bitwise ORing the core type and modifier flag defined in PageTransition. The mask constants (`CORE_MASK`, `QUALATOR_MASK`, and `IS_REDIRECT_MASK`) can be used for disassembly.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-pageTransition: number--><!--Device-NavigationInfo-pageTransition: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## requestMethod

```TypeScript
requestMethod: string
```

HTTP method of the navigation request, such as `GET` and `POST`. Valid for the first time in the willStartRequest phase; It may be updated in the willRedirectRequest phase(for example, redirection may change the method). The subsequent phases remain the same.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-requestMethod: string--><!--Device-NavigationInfo-requestMethod: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## statusCode

```TypeScript
statusCode: number
```

HTTP status code of the response. The value ranges from 100 to 599. This parameter is valid only in willProcessResponse.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-statusCode: number--><!--Device-NavigationInfo-statusCode: number-End-->

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the navigation request.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-NavigationInfo-url: string--><!--Device-NavigationInfo-url: string-End-->

**System capability:** SystemCapability.Web.Webview.Core
