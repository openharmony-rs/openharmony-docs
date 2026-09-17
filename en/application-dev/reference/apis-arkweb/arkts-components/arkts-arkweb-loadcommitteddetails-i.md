# LoadCommittedDetails

Provides detailed information about the web page that has been submitted for redirection, including whether it is the main document, the navigation type, and more. It is suitable for scenarios where monitoring page navigation behavior is required, improving navigation state management accuracy and user experience.

@interface LoadCommittedDetails [since 11 - 11]

**Since:** 11

**System capability:** SystemCapability.Web.Webview.Core

## didReplaceEntry

```TypeScript
didReplaceEntry: boolean
```

Whether the submitted new entry replaces the existing entry.

The value **true** indicates that the submitted new entry replaces the existing entry, and **false** indicates the opposite.

In certain scenarios for navigation to a subdocument, although the existing entry is not replaced, some attributes are changed.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

Whether it is the main document.

The value **true** indicates the main document, and **false** indicates a non-main document.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## isSameDocument

```TypeScript
isSameDocument: boolean
```

Whether the web page navigation is performed without changing the document.

The value **true** indicates that the web page navigation is performed without changing the document, and **false** indicates that the web page navigation is performed with the document changed.

Examples of same-document navigation: 1. Reference fragment navigation; 2. Navigation triggered by pushState or replaceState; 3. History navigation within the same page.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## navigationType

```TypeScript
navigationType: WebNavigationType
```

Navigation type.

**Type:** [WebNavigationType](arkts-arkweb-webnavigationtype-e.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

URL of the web page to navigate to.

**Type:** string

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Web.Webview.Core
