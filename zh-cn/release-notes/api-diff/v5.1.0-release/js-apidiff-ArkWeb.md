| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：global；<br>API声明：declare enum MixedMode<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum MixedMode<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：All = 0<br>差异内容：crossplatform|类名：MixedMode；<br>API声明：All<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：Compatible = 1<br>差异内容：crossplatform|类名：MixedMode；<br>API声明：Compatible<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：MixedMode；<br>API声明：None = 2<br>差异内容：crossplatform|类名：MixedMode；<br>API声明：None<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare enum CacheMode<br>差异内容：crossplatform|类名：global；<br>API声明：declare enum CacheMode<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Default = 0<br>差异内容：crossplatform|类名：CacheMode；<br>API声明：Default<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：None = 1<br>差异内容：crossplatform|类名：CacheMode；<br>API声明：None<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Online = 2<br>差异内容：crossplatform|类名：CacheMode；<br>API声明：Online<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：CacheMode；<br>API声明：Only = 3<br>差异内容：crossplatform|类名：CacheMode；<br>API声明：Only<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare class FullScreenExitHandler<br>差异内容：crossplatform|类名：global；<br>API声明：declare class FullScreenExitHandler<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenExitHandler；<br>API声明：exitFullScreen(): void;<br>差异内容：crossplatform|类名：FullScreenExitHandler；<br>API声明：exitFullScreen(): void;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface FullScreenEnterEvent<br>差异内容：crossplatform|类名：global；<br>API声明：declare interface FullScreenEnterEvent<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：handler: FullScreenExitHandler;<br>差异内容：crossplatform|类名：FullScreenEnterEvent；<br>API声明：handler: FullScreenExitHandler;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：videoWidth?: number;<br>差异内容：crossplatform|类名：FullScreenEnterEvent；<br>API声明：videoWidth?: number;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：FullScreenEnterEvent；<br>API声明：videoHeight?: number;<br>差异内容：crossplatform|类名：FullScreenEnterEvent；<br>API声明：videoHeight?: number;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：type OnFullScreenEnterCallback = (event: FullScreenEnterEvent) => void;<br>差异内容：crossplatform|类名：global；<br>API声明：type OnFullScreenEnterCallback = (event: FullScreenEnterEvent) => void;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：ConsoleMessage；<br>API声明：getSourceId(): string;<br>差异内容：crossplatform|类名：ConsoleMessage；<br>API声明：getSourceId(): string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：ConsoleMessage；<br>API声明：getLineNumber(): number;<br>差异内容：crossplatform|类名：ConsoleMessage；<br>API声明：getLineNumber(): number;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：getRequestHeader(): Array\<Header>;<br>差异内容：crossplatform|类名：WebResourceRequest；<br>API声明：getRequestHeader(): Array\<Header>;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isRequestGesture(): boolean;<br>差异内容：crossplatform|类名：WebResourceRequest；<br>API声明：isRequestGesture(): boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isMainFrame(): boolean;<br>差异内容：crossplatform|类名：WebResourceRequest；<br>API声明：isMainFrame(): boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：isRedirect(): boolean;<br>差异内容：crossplatform|类名：WebResourceRequest；<br>API声明：isRedirect(): boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceRequest；<br>API声明：getRequestMethod(): string;<br>差异内容：crossplatform|类名：WebResourceRequest；<br>API声明：getRequestMethod(): string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseData(): string;<br>差异内容：crossplatform|类名：WebResourceResponse；<br>API声明：getResponseData(): string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>差异内容：crossplatform|类名：WebResourceResponse；<br>API声明：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getReasonMessage(): string;<br>差异内容：crossplatform|类名：WebResourceResponse；<br>API声明：getReasonMessage(): string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseHeader(): Array\<Header>;<br>差异内容：crossplatform|类名：WebResourceResponse；<br>API声明：getResponseHeader(): Array\<Header>;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebResourceResponse；<br>API声明：getResponseIsReady(): boolean;<br>差异内容：crossplatform|类名：WebResourceResponse；<br>API声明：getResponseIsReady(): boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface Header<br>差异内容：crossplatform|类名：global；<br>API声明：declare interface Header<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：Header；<br>API声明：headerKey: string;<br>差异内容：crossplatform|类名：Header；<br>API声明：headerKey: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：Header；<br>API声明：headerValue: string;<br>差异内容：crossplatform|类名：Header；<br>API声明：headerValue: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebOptions；<br>API声明：incognitoMode?: boolean;<br>差异内容：crossplatform|类名：WebOptions；<br>API声明：incognitoMode?: boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface OnBeforeUnloadEvent<br>差异内容：crossplatform|类名：global；<br>API声明：declare interface OnBeforeUnloadEvent<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：url: string;<br>差异内容：crossplatform|类名：OnBeforeUnloadEvent；<br>API声明：url: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：message: string;<br>差异内容：crossplatform|类名：OnBeforeUnloadEvent；<br>API声明：message: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnBeforeUnloadEvent；<br>API声明：result: JsResult;<br>差异内容：crossplatform|类名：OnBeforeUnloadEvent；<br>API声明：result: JsResult;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnDownloadStartEvent；<br>API声明：contentDisposition: string;<br>差异内容：crossplatform|类名：OnDownloadStartEvent；<br>API声明：contentDisposition: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface OnRefreshAccessedHistoryEvent<br>差异内容：crossplatform|类名：global；<br>API声明：declare interface OnRefreshAccessedHistoryEvent<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnRefreshAccessedHistoryEvent；<br>API声明：url: string;<br>差异内容：crossplatform|类名：OnRefreshAccessedHistoryEvent；<br>API声明：url: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：OnRefreshAccessedHistoryEvent；<br>API声明：isRefreshed: boolean;<br>差异内容：crossplatform|类名：OnRefreshAccessedHistoryEvent；<br>API声明：isRefreshed: boolean;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：global；<br>API声明：declare interface JavaScriptProxy<br>差异内容：crossplatform|类名：global；<br>API声明：declare interface JavaScriptProxy<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：object: object;<br>差异内容：crossplatform|类名：JavaScriptProxy；<br>API声明：object: object;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：name: string;<br>差异内容：crossplatform|类名：JavaScriptProxy；<br>API声明：name: string;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：methodList: Array\<string>;<br>差异内容：crossplatform|类名：JavaScriptProxy；<br>API声明：methodList: Array\<string>;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：controller: WebController \| WebviewController;<br>差异内容：crossplatform|类名：JavaScriptProxy；<br>API声明：controller: WebController \| WebviewController;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：JavaScriptProxy；<br>API声明：asyncMethodList?: Array\<string>;<br>差异内容：crossplatform|类名：JavaScriptProxy；<br>API声明：asyncMethodList?: Array\<string>;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onlineImageAccess(onlineImageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：onlineImageAccess(onlineImageAccess: boolean): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：domStorageAccess(domStorageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：domStorageAccess(domStorageAccess: boolean): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：imageAccess(imageAccess: boolean): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：imageAccess(imageAccess: boolean): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：mixedMode(mixedMode: MixedMode): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：mixedMode(mixedMode: MixedMode): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：javaScriptProxy(javaScriptProxy: JavaScriptProxy): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：cacheMode(cacheMode: CacheMode): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：cacheMode(cacheMode: CacheMode): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onBeforeUnload(callback: Callback\<OnBeforeUnloadEvent, boolean>): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：onBeforeUnload(callback: Callback\<OnBeforeUnloadEvent, boolean>): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onRefreshAccessedHistory(callback: Callback\<OnRefreshAccessedHistoryEvent>): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：onRefreshAccessedHistory(callback: Callback\<OnRefreshAccessedHistoryEvent>): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onFullScreenExit(callback: () => void): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：onFullScreenExit(callback: () => void): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：onFullScreenEnter(callback: OnFullScreenEnterCallback): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：WebAttribute；<br>API声明：blockNetwork(block: boolean): WebAttribute;<br>差异内容：crossplatform|类名：WebAttribute；<br>API声明：blockNetwork(block: boolean): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：interface WebStorageOrigin<br>差异内容：crossplatform|类名：webview；<br>API声明：interface WebStorageOrigin<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：origin: string;<br>差异内容：crossplatform|类名：WebStorageOrigin；<br>API声明：origin: string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：usage: number;<br>差异内容：crossplatform|类名：WebStorageOrigin；<br>API声明：usage: number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：quota: number;<br>差异内容：crossplatform|类名：WebStorageOrigin；<br>API声明：quota: number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebStorage<br>差异内容：crossplatform|类名：webview；<br>API声明：class WebStorage<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static deleteAllData(incognito?: boolean): void;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static deleteAllData(incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static deleteOrigin(origin: string): void;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static deleteOrigin(origin: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOrigins(): Promise\<Array\<WebStorageOrigin>>;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOrigins(): Promise\<Array\<WebStorageOrigin>>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string): Promise\<number>;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string): Promise\<number>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string): Promise\<number>;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string): Promise\<number>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class GeolocationPermissions<br>差异内容：crossplatform|类名：webview；<br>API声明：class GeolocationPermissions<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static allowGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static allowGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static deleteGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static deleteGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static deleteAllGeolocation(incognito?: boolean): void;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static deleteAllGeolocation(incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;<br>差异内容：crossplatform|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebCookieManager；<br>API声明：static existCookie(incognito?: boolean): boolean;<br>差异内容：crossplatform|类名：WebCookieManager；<br>API声明：static existCookie(incognito?: boolean): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebCookieManager；<br>API声明：static clearSessionCookie(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|类名：WebCookieManager；<br>API声明：static clearSessionCookie(callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebMessageType<br>差异内容：crossplatform|类名：webview；<br>API声明：enum WebMessageType<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：STRING<br>差异内容：crossplatform|类名：WebMessageType；<br>API声明：STRING<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：NUMBER<br>差异内容：crossplatform|类名：WebMessageType；<br>API声明：NUMBER<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：BOOLEAN<br>差异内容：crossplatform|类名：WebMessageType；<br>API声明：BOOLEAN<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：ARRAY<br>差异内容：crossplatform|类名：WebMessageType；<br>API声明：ARRAY<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：ERROR<br>差异内容：crossplatform|类名：WebMessageType；<br>API声明：ERROR<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebMessageExt<br>差异内容：crossplatform|类名：webview；<br>API声明：class WebMessageExt<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getType(): WebMessageType;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getType(): WebMessageType;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getString(): string;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getString(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getNumber(): number;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getNumber(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getError(): Error;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：getError(): Error;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setType(type: WebMessageType): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setType(type: WebMessageType): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setString(message: string): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setString(message: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setNumber(message: number): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setNumber(message: number): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setBoolean(message: boolean): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setBoolean(message: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setArray(message: Array\<string \| number \| boolean>): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setArray(message: Array\<string \| number \| boolean>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setError(message: Error): void;<br>差异内容：crossplatform|类名：WebMessageExt；<br>API声明：setError(message: Error): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessagePort；<br>API声明：postMessageEventExt(message: WebMessageExt): void;<br>差异内容：crossplatform|类名：WebMessagePort；<br>API声明：postMessageEventExt(message: WebMessageExt): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessagePort；<br>API声明：onMessageEventExt(callback: (result: WebMessageExt) => void): void;<br>差异内容：crossplatform|类名：WebMessagePort；<br>API声明：onMessageEventExt(callback: (result: WebMessageExt) => void): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum JsMessageType<br>差异内容：crossplatform|类名：webview；<br>API声明：enum JsMessageType<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：STRING<br>差异内容：crossplatform|类名：JsMessageType；<br>API声明：STRING<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：NUMBER<br>差异内容：crossplatform|类名：JsMessageType；<br>API声明：NUMBER<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：BOOLEAN<br>差异内容：crossplatform|类名：JsMessageType；<br>API声明：BOOLEAN<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：ARRAY<br>差异内容：crossplatform|类名：JsMessageType；<br>API声明：ARRAY<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class JsMessageExt<br>差异内容：crossplatform|类名：webview；<br>API声明：class JsMessageExt<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getType(): JsMessageType;<br>差异内容：crossplatform|类名：JsMessageExt；<br>API声明：getType(): JsMessageType;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getString(): string;<br>差异内容：crossplatform|类名：JsMessageExt；<br>API声明：getString(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getNumber(): number;<br>差异内容：crossplatform|类名：JsMessageExt；<br>API声明：getNumber(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：crossplatform|类名：JsMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：crossplatform|类名：JsMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：zoomIn(): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：zoomIn(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：zoomOut(): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：zoomOut(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：getWebId(): number;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：getWebId(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>, asyncMethodList?: Array\<string>, permission?: string): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>, asyncMethodList?: Array\<string>, permission?: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：deleteJavaScriptRegister(name: string): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：deleteJavaScriptRegister(name: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer): Promise\<JsMessageExt>;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer): Promise\<JsMessageExt>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer, callback: AsyncCallback\<JsMessageExt>): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer, callback: AsyncCallback\<JsMessageExt>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：pageUp(top: boolean): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：pageUp(top: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：pageDown(bottom: boolean): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：pageDown(bottom: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：getOriginalUrl(): string;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：getOriginalUrl(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：startDownload(url: string): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：startDownload(url: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：postUrl(url: string, postData: ArrayBuffer): void;<br>差异内容：crossplatform|类名：WebviewController；<br>API声明：postUrl(url: string, postData: ArrayBuffer): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebDownloadState<br>差异内容：crossplatform|类名：webview；<br>API声明：enum WebDownloadState<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：IN_PROGRESS = 0<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：IN_PROGRESS = 0<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：COMPLETED<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：COMPLETED<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：CANCELED<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：CANCELED<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：INTERRUPTED<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：INTERRUPTED<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：PENDING<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：PENDING<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：PAUSED<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：PAUSED<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：UNKNOWN<br>差异内容：crossplatform|类名：WebDownloadState；<br>API声明：UNKNOWN<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebDownloadErrorCode<br>差异内容：crossplatform|类名：webview；<br>API声明：enum WebDownloadErrorCode<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadErrorCode；<br>API声明：USER_CANCELED = 40<br>差异内容：crossplatform|类名：WebDownloadErrorCode；<br>API声明：USER_CANCELED = 40<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadItem<br>差异内容：crossplatform|类名：webview；<br>API声明：class WebDownloadItem<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getGuid(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getGuid(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getCurrentSpeed(): number;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getCurrentSpeed(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getPercentComplete(): number;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getPercentComplete(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getTotalBytes(): number;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getTotalBytes(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getState(): WebDownloadState;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getState(): WebDownloadState;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getLastErrorCode(): WebDownloadErrorCode;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getLastErrorCode(): WebDownloadErrorCode;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getMethod(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getMethod(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getMimeType(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getMimeType(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getUrl(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getUrl(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getSuggestedFileName(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getSuggestedFileName(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：start(downloadPath: string): void;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：start(downloadPath: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：cancel(): void;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：cancel(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：pause(): void;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：pause(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：resume(): void;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：resume(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getReceivedBytes(): number;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getReceivedBytes(): number;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getFullPath(): string;<br>差异内容：crossplatform|类名：WebDownloadItem；<br>API声明：getFullPath(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadDelegate<br>差异内容：crossplatform|类名：webview；<br>API声明：class WebDownloadDelegate<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onBeforeDownload(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|类名：WebDownloadDelegate；<br>API声明：onBeforeDownload(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|类名：WebDownloadDelegate；<br>API声明：onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadFinish(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|类名：WebDownloadDelegate；<br>API声明：onDownloadFinish(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadFailed(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|类名：WebDownloadDelegate；<br>API声明：onDownloadFailed(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadManager<br>差异内容：crossplatform|类名：webview；<br>API声明：class WebDownloadManager<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadManager；<br>API声明：static setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：crossplatform|类名：WebDownloadManager；<br>API声明：static setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API废弃版本变更|类名：WebAttribute；<br>API声明：selectionMenuOptions(expandedMenuOptions: Array\<ExpandedMenuItemOptions>): WebAttribute;<br>差异内容：20|类名：WebAttribute；<br>API声明：selectionMenuOptions(expandedMenuOptions: Array\<ExpandedMenuItemOptions>): WebAttribute;<br>差异内容：NA|component/web.d.ts|
|API废弃版本变更|类名：global；<br>API声明：declare interface ExpandedMenuItemOptions<br>差异内容：20|类名：global；<br>API声明：declare interface ExpandedMenuItemOptions<br>差异内容：NA|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：content: ResourceStr;<br>差异内容：20|类名：ExpandedMenuItemOptions；<br>API声明：content: ResourceStr;<br>差异内容：NA|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：startIcon?: ResourceStr;<br>差异内容：20|类名：ExpandedMenuItemOptions；<br>API声明：startIcon?: ResourceStr;<br>差异内容：NA|component/web.d.ts|
|API废弃版本变更|类名：ExpandedMenuItemOptions；<br>API声明：action: (selectedText: {<br>        plainText: string;<br>    }) => void;<br>差异内容：20|类名：ExpandedMenuItemOptions；<br>API声明：action: (selectedText: {<br>        plainText: string;<br>    }) => void;<br>差异内容：NA|component/web.d.ts|
|API废弃版本变更|类名：WebviewController；<br>API声明：getHitTest(): WebHitTestType;<br>差异内容：18|类名：WebviewController；<br>API声明：getHitTest(): WebHitTestType;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API废弃版本变更|类名：WebviewController；<br>API声明：getHitTestValue(): HitTestValue;<br>差异内容：18|类名：WebviewController；<br>API声明：getHitTestValue(): HitTestValue;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：enableIntelligentTrackingPrevention(enable: boolean): void;<br>差异内容：801|类名：WebviewController；<br>API声明：enableIntelligentTrackingPrevention(enable: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：isIntelligentTrackingPreventionEnabled(): boolean;<br>差异内容：801|类名：WebviewController；<br>API声明：isIntelligentTrackingPreventionEnabled(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：static addIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：801|类名：WebviewController；<br>API声明：static addIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：static removeIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：801|类名：WebviewController；<br>API声明：static removeIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：static clearIntelligentTrackingPreventionBypassingList(): void;<br>差异内容：801|类名：WebviewController；<br>API声明：static clearIntelligentTrackingPreventionBypassingList(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：enableAdsBlock(enable: boolean): void;<br>差异内容：801|类名：WebviewController；<br>API声明：enableAdsBlock(enable: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：isAdsBlockEnabled(): boolean;<br>差异内容：801|类名：WebviewController；<br>API声明：isAdsBlockEnabled(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：WebviewController；<br>API声明：isAdsBlockEnabledForCurPage(): boolean;<br>差异内容：801|类名：WebviewController；<br>API声明：isAdsBlockEnabledForCurPage(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static setAdsBlockRules(rulesFile: string, replace: boolean): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static setAdsBlockRules(rulesFile: string, replace: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static addAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static addAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static addAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static addAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static removeAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static removeAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static removeAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static removeAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static clearAdsBlockDisallowedList(): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static clearAdsBlockDisallowedList(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除错误码|类名：AdsBlockManager；<br>API声明：static clearAdsBlockAllowedList(): void;<br>差异内容：801|类名：AdsBlockManager；<br>API声明：static clearAdsBlockAllowedList(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|错误码变更|类名：WebviewController；<br>API声明：static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;<br>差异内容：17100002,17100013|类名：WebviewController；<br>API声明：static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;<br>差异内容：171000013,17100002|api/@ohos.web.webview.d.ts|
|删除API|类名：webview；<br>API声明：enum ArkWebEngineVersion<br>差异内容：enum ArkWebEngineVersion|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：ArkWebEngineVersion；<br>API声明：SYSTEM_DEFAULT = 0<br>差异内容：SYSTEM_DEFAULT = 0|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：ArkWebEngineVersion；<br>API声明：M114 = 1<br>差异内容：M114 = 1|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：ArkWebEngineVersion；<br>API声明：M132 = 2<br>差异内容：M132 = 2|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：webview；<br>API声明：enum ControllerAttachState<br>差异内容：enum ControllerAttachState|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：ControllerAttachState；<br>API声明：UNATTACHED = 0<br>差异内容：UNATTACHED = 0|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：ControllerAttachState；<br>API声明：ATTACHED = 1<br>差异内容：ATTACHED = 1|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：webview；<br>API声明：enum WebBlanklessErrorCode<br>差异内容：enum WebBlanklessErrorCode|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：ERR_UNKNOWN = -1<br>差异内容：ERR_UNKNOWN = -1|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：ERR_INVALID_PARAM = -2<br>差异内容：ERR_INVALID_PARAM = -2|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：ERR_CONTROLLER_NOT_INITED = -3<br>差异内容：ERR_CONTROLLER_NOT_INITED = -3|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：ERR_KEY_NOT_MATCH = -4<br>差异内容：ERR_KEY_NOT_MATCH = -4|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebBlanklessErrorCode；<br>API声明：ERR_SIGNIFICANT_CHANGE = -5<br>差异内容：ERR_SIGNIFICANT_CHANGE = -5|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：webview；<br>API声明：interface BlanklessInfo<br>差异内容：interface BlanklessInfo|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：BlanklessInfo；<br>API声明：errCode: WebBlanklessErrorCode;<br>差异内容：errCode: WebBlanklessErrorCode;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：BlanklessInfo；<br>API声明：similarity: number;<br>差异内容：similarity: number;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：BlanklessInfo；<br>API声明：loadingTime: number;<br>差异内容：loadingTime: number;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void;<br>差异内容：static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static getActiveWebEngineVersion(): ArkWebEngineVersion;<br>差异内容：static getActiveWebEngineVersion(): ArkWebEngineVersion;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static removeAllCache(clearRom: boolean): void;<br>差异内容：static removeAllCache(clearRom: boolean): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getLastHitTest(): HitTestValue;<br>差异内容：getLastHitTest(): HitTestValue;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getPageOffset(): ScrollOffset;<br>差异内容：getPageOffset(): ScrollOffset;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static setAppCustomUserAgent(userAgent: string): void;<br>差异内容：static setAppCustomUserAgent(userAgent: string): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static setUserAgentForHosts(userAgent: string, hosts: Array\<string>): void;<br>差异内容：static setUserAgentForHosts(userAgent: string, hosts: Array\<string>): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getAttachState(): ControllerAttachState;<br>差异内容：getAttachState(): ControllerAttachState;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：on(type: 'controllerAttachStateChange', callback: Callback\<ControllerAttachState>): void;<br>差异内容：on(type: 'controllerAttachStateChange', callback: Callback\<ControllerAttachState>): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：off(type: 'controllerAttachStateChange', callback?: Callback\<ControllerAttachState>): void;<br>差异内容：off(type: 'controllerAttachStateChange', callback?: Callback\<ControllerAttachState>): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：waitForAttached(timeout: number): Promise\<ControllerAttachState>;<br>差异内容：waitForAttached(timeout: number): Promise\<ControllerAttachState>;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getProgress(): number;<br>差异内容：getProgress(): number;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：avoidVisibleViewportBottom(avoidHeight: number): void;<br>差异内容：avoidVisibleViewportBottom(avoidHeight: number): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getBlanklessInfoWithKey(key: string): BlanklessInfo;<br>差异内容：getBlanklessInfoWithKey(key: string): BlanklessInfo;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：setBlanklessLoadingWithKey(key: string, is_start: boolean): WebBlanklessErrorCode;<br>差异内容：setBlanklessLoadingWithKey(key: string, is_start: boolean): WebBlanklessErrorCode;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static clearBlanklessLoadingCache(keys?: Array\<string>): void;<br>差异内容：static clearBlanklessLoadingCache(keys?: Array\<string>): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static setBlanklessLoadingCacheCapacity(capacity: number): number;<br>差异内容：static setBlanklessLoadingCacheCapacity(capacity: number): number;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：getErrorPageEnabled(): boolean;<br>差异内容：getErrorPageEnabled(): boolean;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：setErrorPageEnabled(enable: boolean): void;<br>差异内容：setErrorPageEnabled(enable: boolean): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static enablePrivateNetworkAccess(enable: boolean): void;<br>差异内容：static enablePrivateNetworkAccess(enable: boolean): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static isPrivateNetworkAccessEnabled(): boolean;<br>差异内容：static isPrivateNetworkAccessEnabled(): boolean;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebviewController；<br>API声明：static setWebDestroyMode(mode: WebDestroyMode): void;<br>差异内容：static setWebDestroyMode(mode: WebDestroyMode): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebResourceHandler；<br>API声明：didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void;<br>差异内容：didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void;|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：webview；<br>API声明：enum WebDestroyMode<br>差异内容：enum WebDestroyMode|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebDestroyMode；<br>API声明：NORMAL_MODE = 0<br>差异内容：NORMAL_MODE = 0|NA|api/@ohos.web.webview.d.ts|
|删除API|类名：WebDestroyMode；<br>API声明：FAST_MODE = 1<br>差异内容：FAST_MODE = 1|NA|api/@ohos.web.webview.d.ts|
|起始版本有变化|类名：OnShowFileSelectorEvent；<br>API声明：result: FileSelectorResult;<br>差异内容：12|类名：OnShowFileSelectorEvent；<br>API声明：result: FileSelectorResult;<br>差异内容：11|component/web.d.ts|
|起始版本有变化|类名：OnShowFileSelectorEvent；<br>API声明：fileSelector: FileSelectorParam;<br>差异内容：12|类名：OnShowFileSelectorEvent；<br>API声明：fileSelector: FileSelectorParam;<br>差异内容：11|component/web.d.ts|
|新增kit|类名：global；<br>API声明：component\web.d.ts<br>差异内容：NA|类名：global；<br>API声明：component\web.d.ts<br>差异内容：ArkWeb|component/web.d.ts|
|API从支持元服务到不支持元服务|类名：webview；<br>API声明：enum ProxySchemeFilter<br>差异内容：atomicservice|类名：webview；<br>API声明：enum ProxySchemeFilter<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxySchemeFilter；<br>API声明：MATCH_ALL_SCHEMES = 0<br>差异内容：atomicservice|类名：ProxySchemeFilter；<br>API声明：MATCH_ALL_SCHEMES = 0<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTP = 1<br>差异内容：atomicservice|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTP = 1<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTPS = 2<br>差异内容：atomicservice|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTPS = 2<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：webview；<br>API声明：class ProxyConfig<br>差异内容：atomicservice|类名：webview；<br>API声明：class ProxyConfig<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：insertBypassRule(bypassRule: string): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：insertBypassRule(bypassRule: string): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：insertDirectRule(schemeFilter?: ProxySchemeFilter): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：insertDirectRule(schemeFilter?: ProxySchemeFilter): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：bypassHostnamesWithoutPeriod(): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：bypassHostnamesWithoutPeriod(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：clearImplicitRules(): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：clearImplicitRules(): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：enableReverseBypass(reverse: boolean): void;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：enableReverseBypass(reverse: boolean): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：getBypassRules(): Array\<string>;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：getBypassRules(): Array\<string>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：getProxyRules(): Array\<ProxyRule>;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：getProxyRules(): Array\<ProxyRule>;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyConfig；<br>API声明：isReverseBypassEnabled(): boolean;<br>差异内容：atomicservice|类名：ProxyConfig；<br>API声明：isReverseBypassEnabled(): boolean;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：webview；<br>API声明：class ProxyRule<br>差异内容：atomicservice|类名：webview；<br>API声明：class ProxyRule<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyRule；<br>API声明：getSchemeFilter(): ProxySchemeFilter;<br>差异内容：atomicservice|类名：ProxyRule；<br>API声明：getSchemeFilter(): ProxySchemeFilter;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyRule；<br>API声明：getUrl(): string;<br>差异内容：atomicservice|类名：ProxyRule；<br>API声明：getUrl(): string;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：webview；<br>API声明：type OnProxyConfigChangeCallback = () => void;<br>差异内容：atomicservice|类名：webview；<br>API声明：type OnProxyConfigChangeCallback = () => void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：webview；<br>API声明：class ProxyController<br>差异内容：atomicservice|类名：webview；<br>API声明：class ProxyController<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyController；<br>API声明：static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void;<br>差异内容：atomicservice|类名：ProxyController；<br>API声明：static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|API从支持元服务到不支持元服务|类名：ProxyController；<br>API声明：static removeProxyOverride(callback: OnProxyConfigChangeCallback): void;<br>差异内容：atomicservice|类名：ProxyController；<br>API声明：static removeProxyOverride(callback: OnProxyConfigChangeCallback): void;<br>差异内容：NA|api/@ohos.web.webview.d.ts|
|删除同名函数|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void;<br>差异内容：static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void;|类名：global；<br>API声明：<br>差异内容：NA|api/@ohos.web.webview.d.ts|
