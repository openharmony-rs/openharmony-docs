# LoadCommittedDetails

Defines the load committed details.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface LoadCommittedDetails--><!--Device-unnamed-export declare interface LoadCommittedDetails-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## didReplaceEntry

```TypeScript
didReplaceEntry: boolean
```

True if the committed entry has replaced the existing one. Note that in case of subframes, the NavigationEntry and FrameNavigationEntry objects don't actually get replaced - they're reused, but with updated attributes.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-LoadCommittedDetails-didReplaceEntry: boolean--><!--Device-LoadCommittedDetails-didReplaceEntry: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isMainFrame

```TypeScript
isMainFrame: boolean
```

Check whether the request is for getting the main frame.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-LoadCommittedDetails-isMainFrame: boolean--><!--Device-LoadCommittedDetails-isMainFrame: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## isSameDocument

```TypeScript
isSameDocument: boolean
```

Whether the navigation happened without changing document. Examples of same document navigations are: 1. reference fragment navigations. 2. pushState/replaceState. 3. same page history navigation

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-LoadCommittedDetails-isSameDocument: boolean--><!--Device-LoadCommittedDetails-isSameDocument: boolean-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## navigationType

```TypeScript
navigationType: WebNavigationType
```

The type of the navigation.

**类型：** WebNavigationType

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-LoadCommittedDetails-navigationType: WebNavigationType--><!--Device-LoadCommittedDetails-navigationType: WebNavigationType-End-->

**系统能力：** SystemCapability.Web.Webview.Core

## url

```TypeScript
url: string
```

The url to navigate.

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-LoadCommittedDetails-url: string--><!--Device-LoadCommittedDetails-url: string-End-->

**系统能力：** SystemCapability.Web.Webview.Core

