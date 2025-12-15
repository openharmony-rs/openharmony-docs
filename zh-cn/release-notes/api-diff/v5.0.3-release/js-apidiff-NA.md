| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare enum MixedMode<br>差异内容：NA|类名：global；<br>API声明：declare enum MixedMode<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：All<br>差异内容：NA|类名：MixedMode；<br>API声明：All = 0<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：Compatible<br>差异内容：NA|类名：MixedMode；<br>API声明：Compatible = 1<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：None<br>差异内容：NA|类名：MixedMode；<br>API声明：None = 2<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum CacheMode<br>差异内容：NA|类名：global；<br>API声明：declare enum CacheMode<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Default<br>差异内容：NA|类名：CacheMode；<br>API声明：Default = 0<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：None<br>差异内容：NA|类名：CacheMode；<br>API声明：None = 1<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Online<br>差异内容：NA|类名：CacheMode；<br>API声明：Online = 2<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Only<br>差异内容：NA|类名：CacheMode；<br>API声明：Only = 3<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class FullScreenExitHandler<br>差异内容：NA|类名：global；<br>API声明：declare class FullScreenExitHandler<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenExitHandler；<br>API声明：exitFullScreen(): void;<br>差异内容：NA|类名：FullScreenExitHandler；<br>API声明：exitFullScreen(): void;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface FullScreenEnterEvent<br>差异内容：NA|类名：global；<br>API声明：declare interface FullScreenEnterEvent<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：handler: FullScreenExitHandler;<br>差异内容：NA|类名：FullScreenEnterEvent；<br>API声明：handler: FullScreenExitHandler;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：videoWidth?: number;<br>差异内容：NA|类名：FullScreenEnterEvent；<br>API声明：videoWidth?: number;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：videoHeight?: number;<br>差异内容：NA|类名：FullScreenEnterEvent；<br>API声明：videoHeight?: number;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：type OnFullScreenEnterCallback = (event: FullScreenEnterEvent) => void;<br>差异内容：NA|类名：global；<br>API声明：type OnFullScreenEnterCallback = (event: FullScreenEnterEvent) => void;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：ConsoleMessage；<br>API声明：getSourceId(): string;<br>差异内容：NA|类名：ConsoleMessage；<br>API声明：getSourceId(): string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：ConsoleMessage；<br>API声明：getLineNumber(): number;<br>差异内容：NA|类名：ConsoleMessage；<br>API声明：getLineNumber(): number;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：getRequestHeader(): Array\<Header>;<br>差异内容：NA|类名：WebResourceRequest；<br>API声明：getRequestHeader(): Array\<Header>;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isRequestGesture(): boolean;<br>差异内容：NA|类名：WebResourceRequest；<br>API声明：isRequestGesture(): boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isMainFrame(): boolean;<br>差异内容：NA|类名：WebResourceRequest；<br>API声明：isMainFrame(): boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isRedirect(): boolean;<br>差异内容：NA|类名：WebResourceRequest；<br>API声明：isRedirect(): boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：getRequestMethod(): string;<br>差异内容：NA|类名：WebResourceRequest；<br>API声明：getRequestMethod(): string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseData(): string;<br>差异内容：NA|类名：WebResourceResponse；<br>API声明：getResponseData(): string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>差异内容：NA|类名：WebResourceResponse；<br>API声明：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getReasonMessage(): string;<br>差异内容：NA|类名：WebResourceResponse；<br>API声明：getReasonMessage(): string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseHeader(): Array\<Header>;<br>差异内容：NA|类名：WebResourceResponse；<br>API声明：getResponseHeader(): Array\<Header>;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseIsReady(): boolean;<br>差异内容：NA|类名：WebResourceResponse；<br>API声明：getResponseIsReady(): boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface Header<br>差异内容：NA|类名：global；<br>API声明：declare interface Header<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：Header；<br>API声明：headerKey: string;<br>差异内容：NA|类名：Header；<br>API声明：headerKey: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：Header；<br>API声明：headerValue: string;<br>差异内容：NA|类名：Header；<br>API声明：headerValue: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebOptions；<br>API声明：incognitoMode?: boolean;<br>差异内容：NA|类名：WebOptions；<br>API声明：incognitoMode?: boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface OnBeforeUnloadEvent<br>差异内容：NA|类名：global；<br>API声明：declare interface OnBeforeUnloadEvent<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：url: string;<br>差异内容：NA|类名：OnBeforeUnloadEvent；<br>API声明：url: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：message: string;<br>差异内容：NA|类名：OnBeforeUnloadEvent；<br>API声明：message: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：result: JsResult;<br>差异内容：NA|类名：OnBeforeUnloadEvent；<br>API声明：result: JsResult;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnDownloadStartEvent；<br>API声明：contentDisposition: string;<br>差异内容：NA|类名：OnDownloadStartEvent；<br>API声明：contentDisposition: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface OnRefreshAccessedHistoryEvent<br>差异内容：NA|类名：global；<br>API声明：declare interface OnRefreshAccessedHistoryEvent<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnRefreshAccessedHistoryEvent；<br>API声明：url: string;<br>差异内容：NA|类名：OnRefreshAccessedHistoryEvent；<br>API声明：url: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：OnRefreshAccessedHistoryEvent；<br>API声明：isRefreshed: boolean;<br>差异内容：NA|类名：OnRefreshAccessedHistoryEvent；<br>API声明：isRefreshed: boolean;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface JavaScriptProxy<br>差异内容：NA|类名：global；<br>API声明：declare interface JavaScriptProxy<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：object: object;<br>差异内容：NA|类名：JavaScriptProxy；<br>API声明：object: object;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：name: string;<br>差异内容：NA|类名：JavaScriptProxy；<br>API声明：name: string;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：methodList: Array\<string>;<br>差异内容：NA|类名：JavaScriptProxy；<br>API声明：methodList: Array\<string>;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：controller: WebController \| WebviewController;<br>差异内容：NA|类名：JavaScriptProxy；<br>API声明：controller: WebController \| WebviewController;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：asyncMethodList?: Array\<string>;<br>差异内容：NA|类名：JavaScriptProxy；<br>API声明：asyncMethodList?: Array\<string>;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onlineImageAccess(onlineImageAccess: boolean): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：onlineImageAccess(onlineImageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：domStorageAccess(domStorageAccess: boolean): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：domStorageAccess(domStorageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：imageAccess(imageAccess: boolean): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：imageAccess(imageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：mixedMode(mixedMode: MixedMode): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：mixedMode(mixedMode: MixedMode): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：cacheMode(cacheMode: CacheMode): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：cacheMode(cacheMode: CacheMode): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onBeforeUnload(callback: Callback\<OnBeforeUnloadEvent, boolean>): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：onBeforeUnload(callback: Callback\<OnBeforeUnloadEvent, boolean>): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onRefreshAccessedHistory(callback: Callback\<OnRefreshAccessedHistoryEvent>): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：onRefreshAccessedHistory(callback: Callback\<OnRefreshAccessedHistoryEvent>): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onFullScreenExit(callback: () => void): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：onFullScreenExit(callback: () => void): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：blockNetwork(block: boolean): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：blockNetwork(block: boolean): WebAttribute;<br>差异内容：crossplatform|component/web.d.ts|
|API废弃版本变更|类名：WebAttribute；<br>API声明：selectionMenuOptions(expandedMenuOptions: Array\<ExpandedMenuItemOptions>): WebAttribute;<br>差异内容：NA|类名：WebAttribute；<br>API声明：selectionMenuOptions(expandedMenuOptions: Array\<ExpandedMenuItemOptions>): WebAttribute;<br>差异内容：20|component/web.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare interface ExpandedMenuItemOptions<br>差异内容：NA|类名：global；<br>API声明：declare interface ExpandedMenuItemOptions<br>差异内容：20|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：content: ResourceStr;<br>差异内容：NA|类名：ExpandedMenuItemOptions；<br>API声明：content: ResourceStr;<br>差异内容：20|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：startIcon?: ResourceStr;<br>差异内容：NA|类名：ExpandedMenuItemOptions；<br>API声明：startIcon?: ResourceStr;<br>差异内容：20|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：action: (selectedText: {<br>        plainText: string;<br>    }) => void;<br>差异内容：NA|类名：ExpandedMenuItemOptions；<br>API声明：action: (selectedText: {<br>        plainText: string;<br>    }) => void;<br>差异内容：20|component/web.d.ts|
|函数变更|类名：RectAttribute；<br>API声明：radiusWidth(value: number \| string): RectAttribute;<br>差异内容：value: number \| string|类名：RectAttribute；<br>API声明：radiusWidth(value: Length): RectAttribute;<br>差异内容：value: Length|component/rect.d.ts|
|函数变更|类名：RectAttribute；<br>API声明：radiusHeight(value: number \| string): RectAttribute;<br>差异内容：value: number \| string|类名：RectAttribute；<br>API声明：radiusHeight(value: Length): RectAttribute;<br>差异内容：value: Length|component/rect.d.ts|
|函数变更|类名：RectAttribute；<br>API声明：radius(value: number \| string \| Array\<any>): RectAttribute;<br>差异内容：value: number \| string \| Array\<any>|类名：RectAttribute；<br>API声明：radius(value: Length \| Array\<any>): RectAttribute;<br>差异内容：value: Length \| Array\<any>|component/rect.d.ts|
|新增API|NA|类名：global；<br>API声明：interface LineOptions<br>差异内容：interface LineOptions|component/line.d.ts|
|新增API|NA|类名：LineOptions；<br>API声明：width?: Length;<br>差异内容：width?: Length;|component/line.d.ts|
|新增API|NA|类名：LineOptions；<br>API声明：height?: Length;<br>差异内容：height?: Length;|component/line.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RectOptions<br>差异内容：declare interface RectOptions|component/rect.d.ts|
|新增API|NA|类名：RectOptions；<br>API声明：width?: Length;<br>差异内容：width?: Length;|component/rect.d.ts|
|新增API|NA|类名：RectOptions；<br>API声明：height?: Length;<br>差异内容：height?: Length;|component/rect.d.ts|
|新增API|NA|类名：RectOptions；<br>API声明：radius?: Length \| Array\<any>;<br>差异内容：radius?: Length \| Array\<any>;|component/rect.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface RoundedRectOptions<br>差异内容：declare interface RoundedRectOptions|component/rect.d.ts|
|新增API|NA|类名：RoundedRectOptions；<br>API声明：width?: Length;<br>差异内容：width?: Length;|component/rect.d.ts|
|新增API|NA|类名：RoundedRectOptions；<br>API声明：height?: Length;<br>差异内容：height?: Length;|component/rect.d.ts|
|新增API|NA|类名：RoundedRectOptions；<br>API声明：radiusWidth?: Length;<br>差异内容：radiusWidth?: Length;|component/rect.d.ts|
|新增API|NA|类名：RoundedRectOptions；<br>API声明：radiusHeight?: Length;<br>差异内容：radiusHeight?: Length;|component/rect.d.ts|
|新增API|NA|类名：global；<br>API声明：type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string;<br>差异内容：type OnOverrideErrorPageCallback = (errorPageEvent: OnErrorReceiveEvent) => string;|component/web.d.ts|
|新增API|NA|类名：WebMediaOptions；<br>API声明：audioSessionType?: AudioSessionType;<br>差异内容：audioSessionType?: AudioSessionType;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void;<br>差异内容：type MouseInfoCallback = (event: NativeEmbedMouseInfo) => void;|component/web.d.ts|
|新增API|NA|类名：FileSelectorParam；<br>API声明：getMimeTypes(): Array\<string>;<br>差异内容：getMimeTypes(): Array\<string>;|component/web.d.ts|
|新增API|NA|类名：WebContextMenuResult；<br>API声明：redo(): void;<br>差异内容：redo(): void;|component/web.d.ts|
|新增API|NA|类名：WebContextMenuResult；<br>API声明：undo(): void;<br>差异内容：undo(): void;|component/web.d.ts|
|新增API|NA|类名：WebContextMenuResult；<br>API声明：pasteAndMatchStyle(): void;<br>差异内容：pasteAndMatchStyle(): void;|component/web.d.ts|
|新增API|NA|类名：EventResult；<br>API声明：setMouseEventResult(result: boolean, stopPropagation?: boolean): void;<br>差异内容：setMouseEventResult(result: boolean, stopPropagation?: boolean): void;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface NativeEmbedMouseInfo<br>差异内容：declare interface NativeEmbedMouseInfo|component/web.d.ts|
|新增API|NA|类名：NativeEmbedMouseInfo；<br>API声明：embedId?: string;<br>差异内容：embedId?: string;|component/web.d.ts|
|新增API|NA|类名：NativeEmbedMouseInfo；<br>API声明：mouseEvent?: MouseEvent;<br>差异内容：mouseEvent?: MouseEvent;|component/web.d.ts|
|新增API|NA|类名：NativeEmbedMouseInfo；<br>API声明：result?: EventResult;<br>差异内容：result?: EventResult;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OnLoadStartedEvent<br>差异内容：declare interface OnLoadStartedEvent|component/web.d.ts|
|新增API|NA|类名：OnLoadStartedEvent；<br>API声明：url: string;<br>差异内容：url: string;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OnLoadFinishedEvent<br>差异内容：declare interface OnLoadFinishedEvent|component/web.d.ts|
|新增API|NA|类名：OnLoadFinishedEvent；<br>API声明：url: string;<br>差异内容：url: string;|component/web.d.ts|
|新增API|NA|类名：OnTitleReceiveEvent；<br>API声明：isRealTitle?: boolean;<br>差异内容：isRealTitle?: boolean;|component/web.d.ts|
|新增API|NA|类名：OnBeforeUnloadEvent；<br>API声明：isReload?: boolean;<br>差异内容：isReload?: boolean;|component/web.d.ts|
|新增API|NA|类名：OnSslErrorEventReceiveEvent；<br>API声明：certChainData?: Array\<Uint8Array>;<br>差异内容：certChainData?: Array\<Uint8Array>;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OnPdfScrollEvent<br>差异内容：declare interface OnPdfScrollEvent|component/web.d.ts|
|新增API|NA|类名：OnPdfScrollEvent；<br>API声明：url: string;<br>差异内容：url: string;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface OnPdfLoadEvent<br>差异内容：declare interface OnPdfLoadEvent|component/web.d.ts|
|新增API|NA|类名：OnPdfLoadEvent；<br>API声明：result: PdfLoadResult;<br>差异内容：result: PdfLoadResult;|component/web.d.ts|
|新增API|NA|类名：OnPdfLoadEvent；<br>API声明：url: string;<br>差异内容：url: string;|component/web.d.ts|
|新增API|NA|类名：WebElementType；<br>API声明：LINK = 2<br>差异内容：LINK = 2|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum WebBypassVsyncCondition<br>差异内容：declare enum WebBypassVsyncCondition|component/web.d.ts|
|新增API|NA|类名：WebBypassVsyncCondition；<br>API声明：NONE = 0<br>差异内容：NONE = 0|component/web.d.ts|
|新增API|NA|类名：WebBypassVsyncCondition；<br>API声明：SCROLLBY_FROM_ZERO_OFFSET = 1<br>差异内容：SCROLLBY_FROM_ZERO_OFFSET = 1|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum AudioSessionType<br>差异内容：declare enum AudioSessionType|component/web.d.ts|
|新增API|NA|类名：AudioSessionType；<br>API声明：AMBIENT = 3<br>差异内容：AMBIENT = 3|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum PdfLoadResult<br>差异内容：declare enum PdfLoadResult|component/web.d.ts|
|新增API|NA|类名：PdfLoadResult；<br>API声明：LOAD_SUCCESS = 0<br>差异内容：LOAD_SUCCESS = 0|component/web.d.ts|
|新增API|NA|类名：PdfLoadResult；<br>API声明：PARSE_ERROR_FILE = 1<br>差异内容：PARSE_ERROR_FILE = 1|component/web.d.ts|
|新增API|NA|类名：PdfLoadResult；<br>API声明：PARSE_ERROR_FORMAT = 2<br>差异内容：PARSE_ERROR_FORMAT = 2|component/web.d.ts|
|新增API|NA|类名：PdfLoadResult；<br>API声明：PARSE_ERROR_PASSWORD = 3<br>差异内容：PARSE_ERROR_PASSWORD = 3|component/web.d.ts|
|新增API|NA|类名：PdfLoadResult；<br>API声明：PARSE_ERROR_HANDLER = 4<br>差异内容：PARSE_ERROR_HANDLER = 4|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface PreviewMenuOptions<br>差异内容：declare interface PreviewMenuOptions|component/web.d.ts|
|新增API|NA|类名：PreviewMenuOptions；<br>API声明：hapticFeedbackMode?: HapticFeedbackMode;<br>差异内容：hapticFeedbackMode?: HapticFeedbackMode;|component/web.d.ts|
|新增API|NA|类名：SelectionMenuOptionsExt；<br>API声明：previewMenuOptions?: PreviewMenuOptions;<br>差异内容：previewMenuOptions?: PreviewMenuOptions;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onLoadStarted(callback: Callback\<OnLoadStartedEvent>): WebAttribute;<br>差异内容：onLoadStarted(callback: Callback\<OnLoadStartedEvent>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onLoadFinished(callback: Callback\<OnLoadFinishedEvent>): WebAttribute;<br>差异内容：onLoadFinished(callback: Callback\<OnLoadFinishedEvent>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute;<br>差异内容：onOverrideErrorPage(callback: OnOverrideErrorPageCallback): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onPdfScrollAtBottom(callback: Callback\<OnPdfScrollEvent>): WebAttribute;<br>差异内容：onPdfScrollAtBottom(callback: Callback\<OnPdfScrollEvent>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onPdfLoadEvent(callback: Callback\<OnPdfLoadEvent>): WebAttribute;<br>差异内容：onPdfLoadEvent(callback: Callback\<OnPdfLoadEvent>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onNativeEmbedMouseEvent(callback: MouseInfoCallback): WebAttribute;<br>差异内容：onNativeEmbedMouseEvent(callback: MouseInfoCallback): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute;<br>差异内容：optimizeParserBudget(optimizeParserBudget: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：enableFollowSystemFontWeight(follow: boolean): WebAttribute;<br>差异内容：enableFollowSystemFontWeight(follow: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：enableWebAVSession(enabled: boolean): WebAttribute;<br>差异内容：enableWebAVSession(enabled: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：runJavaScriptOnDocumentStart(scripts: Array\<ScriptItem>): WebAttribute;<br>差异内容：runJavaScriptOnDocumentStart(scripts: Array\<ScriptItem>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：runJavaScriptOnDocumentEnd(scripts: Array\<ScriptItem>): WebAttribute;<br>差异内容：runJavaScriptOnDocumentEnd(scripts: Array\<ScriptItem>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：runJavaScriptOnHeadEnd(scripts: Array\<ScriptItem>): WebAttribute;<br>差异内容：runJavaScriptOnHeadEnd(scripts: Array\<ScriptItem>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：nativeEmbedOptions(options?: EmbedOptions): WebAttribute;<br>差异内容：nativeEmbedOptions(options?: EmbedOptions): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：enableDataDetector(enable: boolean): WebAttribute;<br>差异内容：enableDataDetector(enable: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute;<br>差异内容：dataDetectorConfig(config: TextDataDetectorConfig): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：onActivateContent(callback: Callback\<void>): WebAttribute;<br>差异内容：onActivateContent(callback: Callback\<void>): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute;<br>差异内容：bypassVsyncCondition(condition: WebBypassVsyncCondition): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：gestureFocusMode(mode: GestureFocusMode): WebAttribute;<br>差异内容：gestureFocusMode(mode: GestureFocusMode): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：SslErrorEvent；<br>API声明：certChainData?: Array\<Uint8Array>;<br>差异内容：certChainData?: Array\<Uint8Array>;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface EmbedOptions<br>差异内容：declare interface EmbedOptions|component/web.d.ts|
|新增API|NA|类名：EmbedOptions；<br>API声明：supportDefaultIntrinsicSize?: boolean;<br>差异内容：supportDefaultIntrinsicSize?: boolean;|component/web.d.ts|
|新增API|NA|类名：EmbedOptions；<br>API声明：supportCssDisplayChange?: boolean;<br>差异内容：supportCssDisplayChange?: boolean;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum GestureFocusMode<br>差异内容：declare enum GestureFocusMode|component/web.d.ts|
|新增API|NA|类名：GestureFocusMode；<br>API声明：DEFAULT = 0<br>差异内容：DEFAULT = 0|component/web.d.ts|
|新增API|NA|类名：GestureFocusMode；<br>API声明：GESTURE_TAP_AND_LONG_PRESS = 1<br>差异内容：GESTURE_TAP_AND_LONG_PRESS = 1|component/web.d.ts|
|起始版本有变化|类名：OnShowFileSelectorEvent；<br>API声明：result: FileSelectorResult;<br>差异内容：11|类名：OnShowFileSelectorEvent；<br>API声明：result: FileSelectorResult;<br>差异内容：12|component/web.d.ts|
|起始版本有变化|类名：OnShowFileSelectorEvent；<br>API声明：fileSelector: FileSelectorParam;<br>差异内容：11|类名：OnShowFileSelectorEvent；<br>API声明：fileSelector: FileSelectorParam;<br>差异内容：12|component/web.d.ts|
|删除kit|类名：global；<br>API声明：component\line.d.ts<br>差异内容：ArkUI|类名：global；<br>API声明：component\line.d.ts<br>差异内容：NA|component/line.d.ts|
|删除kit|类名：global；<br>API声明：component\rect.d.ts<br>差异内容：ArkUI|类名：global；<br>API声明：component\rect.d.ts<br>差异内容：NA|component/rect.d.ts|
|删除kit|类名：global；<br>API声明：component\web.d.ts<br>差异内容：ArkWeb|类名：global；<br>API声明：component\web.d.ts<br>差异内容：NA|component/web.d.ts|
|类新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：SslErrorHandler；<br>API声明：handleCancel(): void;<br>差异内容：handleCancel(): void;|类名：SslErrorHandler；<br>API声明：handleCancel(abortLoading: boolean): void;<br>差异内容：handleCancel(abortLoading: boolean): void;|component/web.d.ts|
