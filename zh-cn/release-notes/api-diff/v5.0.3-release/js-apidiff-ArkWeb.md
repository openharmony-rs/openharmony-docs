| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：webview；<br>API声明：interface WebStorageOrigin<br>差异内容：NA|类名：webview；<br>API声明：interface WebStorageOrigin<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：origin: string;<br>差异内容：NA|类名：WebStorageOrigin；<br>API声明：origin: string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：usage: number;<br>差异内容：NA|类名：WebStorageOrigin；<br>API声明：usage: number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorageOrigin；<br>API声明：quota: number;<br>差异内容：NA|类名：WebStorageOrigin；<br>API声明：quota: number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebStorage<br>差异内容：NA|类名：webview；<br>API声明：class WebStorage<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static deleteAllData(incognito?: boolean): void;<br>差异内容：NA|类名：WebStorage；<br>API声明：static deleteAllData(incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static deleteOrigin(origin: string): void;<br>差异内容：NA|类名：WebStorage；<br>API声明：static deleteOrigin(origin: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOrigins(): Promise\<Array\<WebStorageOrigin>>;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOrigins(): Promise\<Array\<WebStorageOrigin>>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string): Promise\<number>;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string): Promise\<number>;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string): Promise\<number>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：WebStorage；<br>API声明：static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class GeolocationPermissions<br>差异内容：NA|类名：webview；<br>API声明：class GeolocationPermissions<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static allowGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static allowGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static deleteGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static deleteGeolocation(origin: string, incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static deleteAllGeolocation(incognito?: boolean): void;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static deleteAllGeolocation(incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;<br>差异内容：NA|类名：GeolocationPermissions；<br>API声明：static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebCookieManager；<br>API声明：static existCookie(incognito?: boolean): boolean;<br>差异内容：NA|类名：WebCookieManager；<br>API声明：static existCookie(incognito?: boolean): boolean;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebCookieManager；<br>API声明：static clearSessionCookie(callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：WebCookieManager；<br>API声明：static clearSessionCookie(callback: AsyncCallback\<void>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebMessageType<br>差异内容：NA|类名：webview；<br>API声明：enum WebMessageType<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：STRING<br>差异内容：NA|类名：WebMessageType；<br>API声明：STRING<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：NUMBER<br>差异内容：NA|类名：WebMessageType；<br>API声明：NUMBER<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：BOOLEAN<br>差异内容：NA|类名：WebMessageType；<br>API声明：BOOLEAN<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：ARRAY<br>差异内容：NA|类名：WebMessageType；<br>API声明：ARRAY<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageType；<br>API声明：ERROR<br>差异内容：NA|类名：WebMessageType；<br>API声明：ERROR<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebMessageExt<br>差异内容：NA|类名：webview；<br>API声明：class WebMessageExt<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getType(): WebMessageType;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getType(): WebMessageType;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getString(): string;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getString(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getNumber(): number;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getNumber(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：getError(): Error;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：getError(): Error;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setType(type: WebMessageType): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setType(type: WebMessageType): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setString(message: string): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setString(message: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setNumber(message: number): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setNumber(message: number): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setBoolean(message: boolean): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setBoolean(message: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setArray(message: Array\<string \| number \| boolean>): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setArray(message: Array\<string \| number \| boolean>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessageExt；<br>API声明：setError(message: Error): void;<br>差异内容：NA|类名：WebMessageExt；<br>API声明：setError(message: Error): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessagePort；<br>API声明：postMessageEventExt(message: WebMessageExt): void;<br>差异内容：NA|类名：WebMessagePort；<br>API声明：postMessageEventExt(message: WebMessageExt): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebMessagePort；<br>API声明：onMessageEventExt(callback: (result: WebMessageExt) => void): void;<br>差异内容：NA|类名：WebMessagePort；<br>API声明：onMessageEventExt(callback: (result: WebMessageExt) => void): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum JsMessageType<br>差异内容：NA|类名：webview；<br>API声明：enum JsMessageType<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：STRING<br>差异内容：NA|类名：JsMessageType；<br>API声明：STRING<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：NUMBER<br>差异内容：NA|类名：JsMessageType；<br>API声明：NUMBER<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：BOOLEAN<br>差异内容：NA|类名：JsMessageType；<br>API声明：BOOLEAN<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageType；<br>API声明：ARRAY<br>差异内容：NA|类名：JsMessageType；<br>API声明：ARRAY<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class JsMessageExt<br>差异内容：NA|类名：webview；<br>API声明：class JsMessageExt<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getType(): JsMessageType;<br>差异内容：NA|类名：JsMessageExt；<br>API声明：getType(): JsMessageType;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getString(): string;<br>差异内容：NA|类名：JsMessageExt；<br>API声明：getString(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getNumber(): number;<br>差异内容：NA|类名：JsMessageExt；<br>API声明：getNumber(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：NA|类名：JsMessageExt；<br>API声明：getBoolean(): boolean;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：JsMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：NA|类名：JsMessageExt；<br>API声明：getArray(): Array\<string \| number \| boolean>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：zoomIn(): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：zoomIn(): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：zoomOut(): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：zoomOut(): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：getWebId(): number;<br>差异内容：NA|类名：WebviewController；<br>API声明：getWebId(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>, asyncMethodList?: Array\<string>, permission?: string): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>, asyncMethodList?: Array\<string>, permission?: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：deleteJavaScriptRegister(name: string): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：deleteJavaScriptRegister(name: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer): Promise\<JsMessageExt>;<br>差异内容：NA|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer): Promise\<JsMessageExt>;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer, callback: AsyncCallback\<JsMessageExt>): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：runJavaScriptExt(script: string \| ArrayBuffer, callback: AsyncCallback\<JsMessageExt>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：pageUp(top: boolean): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：pageUp(top: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：pageDown(bottom: boolean): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：pageDown(bottom: boolean): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：getOriginalUrl(): string;<br>差异内容：NA|类名：WebviewController；<br>API声明：getOriginalUrl(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：startDownload(url: string): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：startDownload(url: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebviewController；<br>API声明：postUrl(url: string, postData: ArrayBuffer): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：postUrl(url: string, postData: ArrayBuffer): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebDownloadState<br>差异内容：NA|类名：webview；<br>API声明：enum WebDownloadState<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：IN_PROGRESS = 0<br>差异内容：NA|类名：WebDownloadState；<br>API声明：IN_PROGRESS = 0<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：COMPLETED<br>差异内容：NA|类名：WebDownloadState；<br>API声明：COMPLETED<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：CANCELED<br>差异内容：NA|类名：WebDownloadState；<br>API声明：CANCELED<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：INTERRUPTED<br>差异内容：NA|类名：WebDownloadState；<br>API声明：INTERRUPTED<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：PENDING<br>差异内容：NA|类名：WebDownloadState；<br>API声明：PENDING<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：PAUSED<br>差异内容：NA|类名：WebDownloadState；<br>API声明：PAUSED<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadState；<br>API声明：UNKNOWN<br>差异内容：NA|类名：WebDownloadState；<br>API声明：UNKNOWN<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：enum WebDownloadErrorCode<br>差异内容：NA|类名：webview；<br>API声明：enum WebDownloadErrorCode<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadErrorCode；<br>API声明：USER_CANCELED = 40<br>差异内容：NA|类名：WebDownloadErrorCode；<br>API声明：USER_CANCELED = 40<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadItem<br>差异内容：NA|类名：webview；<br>API声明：class WebDownloadItem<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getGuid(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getGuid(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getCurrentSpeed(): number;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getCurrentSpeed(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getPercentComplete(): number;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getPercentComplete(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getTotalBytes(): number;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getTotalBytes(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getState(): WebDownloadState;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getState(): WebDownloadState;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getLastErrorCode(): WebDownloadErrorCode;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getLastErrorCode(): WebDownloadErrorCode;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getMethod(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getMethod(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getMimeType(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getMimeType(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getUrl(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getUrl(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getSuggestedFileName(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getSuggestedFileName(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：start(downloadPath: string): void;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：start(downloadPath: string): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：cancel(): void;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：cancel(): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：pause(): void;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：pause(): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：resume(): void;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：resume(): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getReceivedBytes(): number;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getReceivedBytes(): number;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadItem；<br>API声明：getFullPath(): string;<br>差异内容：NA|类名：WebDownloadItem；<br>API声明：getFullPath(): string;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadDelegate<br>差异内容：NA|类名：webview；<br>API声明：class WebDownloadDelegate<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onBeforeDownload(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|类名：WebDownloadDelegate；<br>API声明：onBeforeDownload(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|类名：WebDownloadDelegate；<br>API声明：onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadFinish(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|类名：WebDownloadDelegate；<br>API声明：onDownloadFinish(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadDelegate；<br>API声明：onDownloadFailed(callback: Callback\<WebDownloadItem>): void;<br>差异内容：NA|类名：WebDownloadDelegate；<br>API声明：onDownloadFailed(callback: Callback\<WebDownloadItem>): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：webview；<br>API声明：class WebDownloadManager<br>差异内容：NA|类名：webview；<br>API声明：class WebDownloadManager<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API跨平台权限变更|类名：WebDownloadManager；<br>API声明：static setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：NA|类名：WebDownloadManager；<br>API声明：static setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>差异内容：crossplatform|api/@ohos.web.webview.d.ts|
|API废弃版本变更|类名：WebviewController；<br>API声明：getHitTest(): WebHitTestType;<br>差异内容：NA|类名：WebviewController；<br>API声明：getHitTest(): WebHitTestType;<br>差异内容：18|api/@ohos.web.webview.d.ts|
|API废弃版本变更|类名：WebviewController；<br>API声明：getHitTestValue(): HitTestValue;<br>差异内容：NA|类名：WebviewController；<br>API声明：getHitTestValue(): HitTestValue;<br>差异内容：18|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：enableIntelligentTrackingPrevention(enable: boolean): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：enableIntelligentTrackingPrevention(enable: boolean): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：isIntelligentTrackingPreventionEnabled(): boolean;<br>差异内容：NA|类名：WebviewController；<br>API声明：isIntelligentTrackingPreventionEnabled(): boolean;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：static addIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：static addIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：static removeIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：static removeIntelligentTrackingPreventionBypassingList(hostList: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：static clearIntelligentTrackingPreventionBypassingList(): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：static clearIntelligentTrackingPreventionBypassingList(): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：enableAdsBlock(enable: boolean): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：enableAdsBlock(enable: boolean): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：isAdsBlockEnabled(): boolean;<br>差异内容：NA|类名：WebviewController；<br>API声明：isAdsBlockEnabled(): boolean;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：WebviewController；<br>API声明：isAdsBlockEnabledForCurPage(): boolean;<br>差异内容：NA|类名：WebviewController；<br>API声明：isAdsBlockEnabledForCurPage(): boolean;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static setAdsBlockRules(rulesFile: string, replace: boolean): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static setAdsBlockRules(rulesFile: string, replace: boolean): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static addAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static addAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static addAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static addAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static removeAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static removeAdsBlockDisallowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static removeAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static removeAdsBlockAllowedList(domainSuffixes: Array\<string>): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static clearAdsBlockDisallowedList(): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static clearAdsBlockDisallowedList(): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|新增错误码|类名：AdsBlockManager；<br>API声明：static clearAdsBlockAllowedList(): void;<br>差异内容：NA|类名：AdsBlockManager；<br>API声明：static clearAdsBlockAllowedList(): void;<br>差异内容：801|api/@ohos.web.webview.d.ts|
|错误码变更|类名：WebviewController；<br>API声明：static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;<br>差异内容：171000013,17100002|类名：WebviewController；<br>API声明：static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;<br>差异内容：17100002,17100013|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum ArkWebEngineVersion<br>差异内容：enum ArkWebEngineVersion|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ArkWebEngineVersion；<br>API声明：SYSTEM_DEFAULT = 0<br>差异内容：SYSTEM_DEFAULT = 0|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ArkWebEngineVersion；<br>API声明：M114 = 1<br>差异内容：M114 = 1|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ArkWebEngineVersion；<br>API声明：M132 = 2<br>差异内容：M132 = 2|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebCookieManager；<br>API声明：static saveCookieSync(): void;<br>差异内容：static saveCookieSync(): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum ControllerAttachState<br>差异内容：enum ControllerAttachState|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ControllerAttachState；<br>API声明：UNATTACHED = 0<br>差异内容：UNATTACHED = 0|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ControllerAttachState；<br>API声明：ATTACHED = 1<br>差异内容：ATTACHED = 1|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum WebBlanklessErrorCode<br>差异内容：enum WebBlanklessErrorCode|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：ERR_UNKNOWN = -1<br>差异内容：ERR_UNKNOWN = -1|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：ERR_INVALID_PARAM = -2<br>差异内容：ERR_INVALID_PARAM = -2|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：ERR_CONTROLLER_NOT_INITED = -3<br>差异内容：ERR_CONTROLLER_NOT_INITED = -3|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：ERR_KEY_NOT_MATCH = -4<br>差异内容：ERR_KEY_NOT_MATCH = -4|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebBlanklessErrorCode；<br>API声明：ERR_SIGNIFICANT_CHANGE = -5<br>差异内容：ERR_SIGNIFICANT_CHANGE = -5|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：interface BlanklessInfo<br>差异内容：interface BlanklessInfo|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：BlanklessInfo；<br>API声明：errCode: WebBlanklessErrorCode;<br>差异内容：errCode: WebBlanklessErrorCode;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：BlanklessInfo；<br>API声明：similarity: number;<br>差异内容：similarity: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：BlanklessInfo；<br>API声明：loadingTime: number;<br>差异内容：loadingTime: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void;<br>差异内容：static setActiveWebEngineVersion(engineVersion: ArkWebEngineVersion): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static getActiveWebEngineVersion(): ArkWebEngineVersion;<br>差异内容：static getActiveWebEngineVersion(): ArkWebEngineVersion;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static removeAllCache(clearRom: boolean): void;<br>差异内容：static removeAllCache(clearRom: boolean): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getLastHitTest(): HitTestValue;<br>差异内容：getLastHitTest(): HitTestValue;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getPageOffset(): ScrollOffset;<br>差异内容：getPageOffset(): ScrollOffset;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static setAppCustomUserAgent(userAgent: string): void;<br>差异内容：static setAppCustomUserAgent(userAgent: string): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static setUserAgentForHosts(userAgent: string, hosts: Array\<string>): void;<br>差异内容：static setUserAgentForHosts(userAgent: string, hosts: Array\<string>): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getAttachState(): ControllerAttachState;<br>差异内容：getAttachState(): ControllerAttachState;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：on(type: 'controllerAttachStateChange', callback: Callback\<ControllerAttachState>): void;<br>差异内容：on(type: 'controllerAttachStateChange', callback: Callback\<ControllerAttachState>): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：off(type: 'controllerAttachStateChange', callback?: Callback\<ControllerAttachState>): void;<br>差异内容：off(type: 'controllerAttachStateChange', callback?: Callback\<ControllerAttachState>): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：waitForAttached(timeout: number): Promise\<ControllerAttachState>;<br>差异内容：waitForAttached(timeout: number): Promise\<ControllerAttachState>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getProgress(): number;<br>差异内容：getProgress(): number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：avoidVisibleViewportBottom(avoidHeight: number): void;<br>差异内容：avoidVisibleViewportBottom(avoidHeight: number): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getBlanklessInfoWithKey(key: string): BlanklessInfo;<br>差异内容：getBlanklessInfoWithKey(key: string): BlanklessInfo;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：setBlanklessLoadingWithKey(key: string, is_start: boolean): WebBlanklessErrorCode;<br>差异内容：setBlanklessLoadingWithKey(key: string, is_start: boolean): WebBlanklessErrorCode;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static clearBlanklessLoadingCache(keys?: Array\<string>): void;<br>差异内容：static clearBlanklessLoadingCache(keys?: Array\<string>): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static setBlanklessLoadingCacheCapacity(capacity: number): number;<br>差异内容：static setBlanklessLoadingCacheCapacity(capacity: number): number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getErrorPageEnabled(): boolean;<br>差异内容：getErrorPageEnabled(): boolean;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：setErrorPageEnabled(enable: boolean): void;<br>差异内容：setErrorPageEnabled(enable: boolean): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static enablePrivateNetworkAccess(enable: boolean): void;<br>差异内容：static enablePrivateNetworkAccess(enable: boolean): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static isPrivateNetworkAccessEnabled(): boolean;<br>差异内容：static isPrivateNetworkAccessEnabled(): boolean;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static setWebDestroyMode(mode: WebDestroyMode): void;<br>差异内容：static setWebDestroyMode(mode: WebDestroyMode): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum ProxySchemeFilter<br>差异内容：enum ProxySchemeFilter|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxySchemeFilter；<br>API声明：MATCH_ALL_SCHEMES = 0<br>差异内容：MATCH_ALL_SCHEMES = 0|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTP = 1<br>差异内容：MATCH_HTTP = 1|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxySchemeFilter；<br>API声明：MATCH_HTTPS = 2<br>差异内容：MATCH_HTTPS = 2|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：class ProxyConfig<br>差异内容：class ProxyConfig|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：insertBypassRule(bypassRule: string): void;<br>差异内容：insertBypassRule(bypassRule: string): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：insertDirectRule(schemeFilter?: ProxySchemeFilter): void;<br>差异内容：insertDirectRule(schemeFilter?: ProxySchemeFilter): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void;<br>差异内容：insertProxyRule(proxyRule: string, schemeFilter?: ProxySchemeFilter): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：bypassHostnamesWithoutPeriod(): void;<br>差异内容：bypassHostnamesWithoutPeriod(): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：clearImplicitRules(): void;<br>差异内容：clearImplicitRules(): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：enableReverseBypass(reverse: boolean): void;<br>差异内容：enableReverseBypass(reverse: boolean): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：getBypassRules(): Array\<string>;<br>差异内容：getBypassRules(): Array\<string>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：getProxyRules(): Array\<ProxyRule>;<br>差异内容：getProxyRules(): Array\<ProxyRule>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyConfig；<br>API声明：isReverseBypassEnabled(): boolean;<br>差异内容：isReverseBypassEnabled(): boolean;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：class ProxyRule<br>差异内容：class ProxyRule|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyRule；<br>API声明：getSchemeFilter(): ProxySchemeFilter;<br>差异内容：getSchemeFilter(): ProxySchemeFilter;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyRule；<br>API声明：getUrl(): string;<br>差异内容：getUrl(): string;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：type OnProxyConfigChangeCallback = () => void;<br>差异内容：type OnProxyConfigChangeCallback = () => void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：class ProxyController<br>差异内容：class ProxyController|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyController；<br>API声明：static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void;<br>差异内容：static applyProxyOverride(proxyConfig: ProxyConfig, callback: OnProxyConfigChangeCallback): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ProxyController；<br>API声明：static removeProxyOverride(callback: OnProxyConfigChangeCallback): void;<br>差异内容：static removeProxyOverride(callback: OnProxyConfigChangeCallback): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum WebDestroyMode<br>差异内容：enum WebDestroyMode|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebDestroyMode；<br>API声明：NORMAL_MODE = 0<br>差异内容：NORMAL_MODE = 0|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebDestroyMode；<br>API声明：FAST_MODE = 1<br>差异内容：FAST_MODE = 1|api/@ohos.web.webview.d.ts|
|类新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>差异内容：static setWebDebuggingAccess(webDebuggingAccess: boolean): void;|类名：WebviewController；<br>API声明：static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void;<br>差异内容：static setWebDebuggingAccess(webDebuggingAccess: boolean, port: number): void;|api/@ohos.web.webview.d.ts|
|类新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：WebResourceHandler；<br>API声明：didFail(code: WebNetErrorList): void;<br>差异内容：didFail(code: WebNetErrorList): void;|类名：WebResourceHandler；<br>API声明：didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void;<br>差异内容：didFail(code: WebNetErrorList, completeIfNoResponse: boolean): void;|api/@ohos.web.webview.d.ts|
