| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace webview<br>Differences: declare namespace webview|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface WebHeader<br>Differences: interface WebHeader|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHeader;<br>API declaration: headerKey: string;<br>Differences: headerKey: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHeader;<br>API declaration: headerValue: string;<br>Differences: headerValue: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum WebHitTestType<br>Differences: enum WebHitTestType|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: EditText<br>Differences: EditText|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: Email<br>Differences: Email|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: HttpAnchor<br>Differences: HttpAnchor|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: HttpAnchorImg<br>Differences: HttpAnchorImg|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: Img<br>Differences: Img|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: Map<br>Differences: Map|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: Phone<br>Differences: Phone|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebHitTestType;<br>API declaration: Unknown<br>Differences: Unknown|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum SecureDnsMode<br>Differences: enum SecureDnsMode|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecureDnsMode;<br>API declaration: OFF = 0<br>Differences: OFF = 0|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecureDnsMode;<br>API declaration: AUTO = 1<br>Differences: AUTO = 1|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecureDnsMode;<br>API declaration: SECURE_ONLY = 2<br>Differences: SECURE_ONLY = 2|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum SecurityLevel<br>Differences: enum SecurityLevel|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecurityLevel;<br>API declaration: NONE = 0<br>Differences: NONE = 0|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecurityLevel;<br>API declaration: SECURE = 1<br>Differences: SECURE = 1|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecurityLevel;<br>API declaration: WARNING = 2<br>Differences: WARNING = 2|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: SecurityLevel;<br>API declaration: DANGEROUS = 3<br>Differences: DANGEROUS = 3|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface HitTestValue<br>Differences: interface HitTestValue|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HitTestValue;<br>API declaration: type: WebHitTestType;<br>Differences: type: WebHitTestType;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HitTestValue;<br>API declaration: extra: string;<br>Differences: extra: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface WebCustomScheme<br>Differences: interface WebCustomScheme|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCustomScheme;<br>API declaration: schemeName: string;<br>Differences: schemeName: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCustomScheme;<br>API declaration: isSupportCORS: boolean;<br>Differences: isSupportCORS: boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCustomScheme;<br>API declaration: isSupportFetch: boolean;<br>Differences: isSupportFetch: boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface WebStorageOrigin<br>Differences: interface WebStorageOrigin|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorageOrigin;<br>API declaration: origin: string;<br>Differences: origin: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorageOrigin;<br>API declaration: usage: number;<br>Differences: usage: number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorageOrigin;<br>API declaration: quota: number;<br>Differences: quota: number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: function once(type: string, callback: Callback\<void>): void;<br>Differences: function once(type: string, callback: Callback\<void>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebStorage<br>Differences: class WebStorage|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static deleteAllData(incognito?: boolean): void;<br>Differences: static deleteAllData(incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static deleteOrigin(origin: string): void;<br>Differences: static deleteOrigin(origin: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOrigins(): Promise\<Array\<WebStorageOrigin>>;<br>Differences: static getOrigins(): Promise\<Array\<WebStorageOrigin>>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;<br>Differences: static getOrigins(callback: AsyncCallback\<Array\<WebStorageOrigin>>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOriginQuota(origin: string): Promise\<number>;<br>Differences: static getOriginQuota(origin: string): Promise\<number>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;<br>Differences: static getOriginQuota(origin: string, callback: AsyncCallback\<number>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOriginUsage(origin: string): Promise\<number>;<br>Differences: static getOriginUsage(origin: string): Promise\<number>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebStorage;<br>API declaration: static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;<br>Differences: static getOriginUsage(origin: string, callback: AsyncCallback\<number>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebDataBase<br>Differences: class WebDataBase|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDataBase;<br>API declaration: static existHttpAuthCredentials(): boolean;<br>Differences: static existHttpAuthCredentials(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDataBase;<br>API declaration: static deleteHttpAuthCredentials(): void;<br>Differences: static deleteHttpAuthCredentials(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDataBase;<br>API declaration: static getHttpAuthCredentials(host: string, realm: string): Array\<string>;<br>Differences: static getHttpAuthCredentials(host: string, realm: string): Array\<string>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDataBase;<br>API declaration: static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void;<br>Differences: static saveHttpAuthCredentials(host: string, realm: string, username: string, password: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class GeolocationPermissions<br>Differences: class GeolocationPermissions|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static allowGeolocation(origin: string, incognito?: boolean): void;<br>Differences: static allowGeolocation(origin: string, incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static deleteGeolocation(origin: string, incognito?: boolean): void;<br>Differences: static deleteGeolocation(origin: string, incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static deleteAllGeolocation(incognito?: boolean): void;<br>Differences: static deleteAllGeolocation(incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;<br>Differences: static getAccessibleGeolocation(origin: string, incognito?: boolean): Promise\<boolean>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;<br>Differences: static getAccessibleGeolocation(origin: string, callback: AsyncCallback\<boolean>, incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;<br>Differences: static getStoredGeolocation(incognito?: boolean): Promise\<Array\<string>>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: GeolocationPermissions;<br>API declaration: static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;<br>Differences: static getStoredGeolocation(callback: AsyncCallback\<Array\<string>>, incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebCookieManager<br>Differences: class WebCookieManager|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static getCookie(url: string): string;<br>Differences: static getCookie(url: string): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static fetchCookieSync(url: string, incognito?: boolean): string;<br>Differences: static fetchCookieSync(url: string, incognito?: boolean): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static fetchCookie(url: string): Promise\<string>;<br>Differences: static fetchCookie(url: string): Promise\<string>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static fetchCookie(url: string, callback: AsyncCallback\<string>): void;<br>Differences: static fetchCookie(url: string, callback: AsyncCallback\<string>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static setCookie(url: string, value: string): void;<br>Differences: static setCookie(url: string, value: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static configCookieSync(url: string, value: string, incognito?: boolean): void;<br>Differences: static configCookieSync(url: string, value: string, incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static configCookie(url: string, value: string): Promise\<void>;<br>Differences: static configCookie(url: string, value: string): Promise\<void>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static configCookie(url: string, value: string, callback: AsyncCallback\<void>): void;<br>Differences: static configCookie(url: string, value: string, callback: AsyncCallback\<void>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static saveCookieAsync(): Promise\<void>;<br>Differences: static saveCookieAsync(): Promise\<void>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static saveCookieAsync(callback: AsyncCallback\<void>): void;<br>Differences: static saveCookieAsync(callback: AsyncCallback\<void>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static isCookieAllowed(): boolean;<br>Differences: static isCookieAllowed(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static putAcceptCookieEnabled(accept: boolean): void;<br>Differences: static putAcceptCookieEnabled(accept: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static isThirdPartyCookieAllowed(): boolean;<br>Differences: static isThirdPartyCookieAllowed(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static putAcceptThirdPartyCookieEnabled(accept: boolean): void;<br>Differences: static putAcceptThirdPartyCookieEnabled(accept: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static existCookie(incognito?: boolean): boolean;<br>Differences: static existCookie(incognito?: boolean): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static deleteEntireCookie(): void;<br>Differences: static deleteEntireCookie(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearAllCookiesSync(incognito?: boolean): void;<br>Differences: static clearAllCookiesSync(incognito?: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearAllCookies(): Promise\<void>;<br>Differences: static clearAllCookies(): Promise\<void>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearAllCookies(callback: AsyncCallback\<void>): void;<br>Differences: static clearAllCookies(callback: AsyncCallback\<void>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static deleteSessionCookie(): void;<br>Differences: static deleteSessionCookie(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearSessionCookieSync(): void;<br>Differences: static clearSessionCookieSync(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearSessionCookie(): Promise\<void>;<br>Differences: static clearSessionCookie(): Promise\<void>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebCookieManager;<br>API declaration: static clearSessionCookie(callback: AsyncCallback\<void>): void;<br>Differences: static clearSessionCookie(callback: AsyncCallback\<void>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum WebMessageType<br>Differences: enum WebMessageType|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: NOT_SUPPORT<br>Differences: NOT_SUPPORT|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: STRING<br>Differences: STRING|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: NUMBER<br>Differences: NUMBER|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: BOOLEAN<br>Differences: BOOLEAN|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: ARRAY_BUFFER<br>Differences: ARRAY_BUFFER|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: ARRAY<br>Differences: ARRAY|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageType;<br>API declaration: ERROR<br>Differences: ERROR|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebMessageExt<br>Differences: class WebMessageExt|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getType(): WebMessageType;<br>Differences: getType(): WebMessageType;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getString(): string;<br>Differences: getString(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getNumber(): number;<br>Differences: getNumber(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getBoolean(): boolean;<br>Differences: getBoolean(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getArrayBuffer(): ArrayBuffer;<br>Differences: getArrayBuffer(): ArrayBuffer;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getArray(): Array\<string \| number \| boolean>;<br>Differences: getArray(): Array\<string \| number \| boolean>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: getError(): Error;<br>Differences: getError(): Error;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setType(type: WebMessageType): void;<br>Differences: setType(type: WebMessageType): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setString(message: string): void;<br>Differences: setString(message: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setNumber(message: number): void;<br>Differences: setNumber(message: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setBoolean(message: boolean): void;<br>Differences: setBoolean(message: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setArrayBuffer(message: ArrayBuffer): void;<br>Differences: setArrayBuffer(message: ArrayBuffer): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setArray(message: Array\<string \| number \| boolean>): void;<br>Differences: setArray(message: Array\<string \| number \| boolean>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessageExt;<br>API declaration: setError(message: Error): void;<br>Differences: setError(message: Error): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: type WebMessage = ArrayBuffer \| string;<br>Differences: type WebMessage = ArrayBuffer \| string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface WebMessagePort<br>Differences: interface WebMessagePort|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: isExtentionType?: boolean;<br>Differences: isExtentionType?: boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: close(): void;<br>Differences: close(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: postMessageEvent(message: WebMessage): void;<br>Differences: postMessageEvent(message: WebMessage): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: onMessageEvent(callback: (result: WebMessage) => void): void;<br>Differences: onMessageEvent(callback: (result: WebMessage) => void): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: postMessageEventExt(message: WebMessageExt): void;<br>Differences: postMessageEventExt(message: WebMessageExt): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebMessagePort;<br>API declaration: onMessageEventExt(callback: (result: WebMessageExt) => void): void;<br>Differences: onMessageEventExt(callback: (result: WebMessageExt) => void): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface HistoryItem<br>Differences: interface HistoryItem|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HistoryItem;<br>API declaration: icon: image.PixelMap;<br>Differences: icon: image.PixelMap;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HistoryItem;<br>API declaration: historyUrl: string;<br>Differences: historyUrl: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HistoryItem;<br>API declaration: historyRawUrl: string;<br>Differences: historyRawUrl: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: HistoryItem;<br>API declaration: title: string;<br>Differences: title: string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: interface BackForwardList<br>Differences: interface BackForwardList|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: BackForwardList;<br>API declaration: currentIndex: number;<br>Differences: currentIndex: number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: BackForwardList;<br>API declaration: size: number;<br>Differences: size: number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: BackForwardList;<br>API declaration: getItemAtIndex(index: number): HistoryItem;<br>Differences: getItemAtIndex(index: number): HistoryItem;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum JsMessageType<br>Differences: enum JsMessageType|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: NOT_SUPPORT<br>Differences: NOT_SUPPORT|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: STRING<br>Differences: STRING|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: NUMBER<br>Differences: NUMBER|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: BOOLEAN<br>Differences: BOOLEAN|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: ARRAY_BUFFER<br>Differences: ARRAY_BUFFER|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageType;<br>API declaration: ARRAY<br>Differences: ARRAY|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class JsMessageExt<br>Differences: class JsMessageExt|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getType(): JsMessageType;<br>Differences: getType(): JsMessageType;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getString(): string;<br>Differences: getString(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getNumber(): number;<br>Differences: getNumber(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getBoolean(): boolean;<br>Differences: getBoolean(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getArrayBuffer(): ArrayBuffer;<br>Differences: getArrayBuffer(): ArrayBuffer;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: JsMessageExt;<br>API declaration: getArray(): Array\<string \| number \| boolean>;<br>Differences: getArray(): Array\<string \| number \| boolean>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebviewController<br>Differences: class WebviewController|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static initializeWebEngine(): void;<br>Differences: static initializeWebEngine(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void;<br>Differences: static setHttpDns(secureDnsMode: SecureDnsMode, secureDnsConfig: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static setWebDebuggingAccess(webDebuggingAccess: boolean): void;<br>Differences: static setWebDebuggingAccess(webDebuggingAccess: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: enableSafeBrowsing(enable: boolean): void;<br>Differences: enableSafeBrowsing(enable: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: isSafeBrowsingEnabled(): boolean;<br>Differences: isSafeBrowsingEnabled(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: accessForward(): boolean;<br>Differences: accessForward(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: accessBackward(): boolean;<br>Differences: accessBackward(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: accessStep(step: number): boolean;<br>Differences: accessStep(step: number): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: forward(): void;<br>Differences: forward(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: backward(): void;<br>Differences: backward(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: clearHistory(): void;<br>Differences: clearHistory(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: onActive(): void;<br>Differences: onActive(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: onInactive(): void;<br>Differences: onInactive(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: refresh(): void;<br>Differences: refresh(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void;<br>Differences: loadData(data: string, mimeType: string, encoding: string, baseUrl?: string, historyUrl?: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: loadUrl(url: string \| Resource, headers?: Array\<WebHeader>): void;<br>Differences: loadUrl(url: string \| Resource, headers?: Array\<WebHeader>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getHitTest(): WebHitTestType;<br>Differences: getHitTest(): WebHitTestType;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: storeWebArchive(baseName: string, autoName: boolean): Promise\<string>;<br>Differences: storeWebArchive(baseName: string, autoName: boolean): Promise\<string>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback\<string>): void;<br>Differences: storeWebArchive(baseName: string, autoName: boolean, callback: AsyncCallback\<string>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: zoom(factor: number): void;<br>Differences: zoom(factor: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: zoomIn(): void;<br>Differences: zoomIn(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: zoomOut(): void;<br>Differences: zoomOut(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getHitTestValue(): HitTestValue;<br>Differences: getHitTestValue(): HitTestValue;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getWebId(): number;<br>Differences: getWebId(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getUserAgent(): string;<br>Differences: getUserAgent(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getTitle(): string;<br>Differences: getTitle(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getPageHeight(): number;<br>Differences: getPageHeight(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: backOrForward(step: number): void;<br>Differences: backOrForward(step: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: requestFocus(): void;<br>Differences: requestFocus(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: createWebMessagePorts(isExtentionType?: boolean): Array\<WebMessagePort>;<br>Differences: createWebMessagePorts(isExtentionType?: boolean): Array\<WebMessagePort>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: postMessage(name: string, ports: Array\<WebMessagePort>, uri: string): void;<br>Differences: postMessage(name: string, ports: Array\<WebMessagePort>, uri: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: stop(): void;<br>Differences: stop(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>): void;<br>Differences: registerJavaScriptProxy(object: object, name: string, methodList: Array\<string>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: deleteJavaScriptRegister(name: string): void;<br>Differences: deleteJavaScriptRegister(name: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: searchAllAsync(searchString: string): void;<br>Differences: searchAllAsync(searchString: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: clearMatches(): void;<br>Differences: clearMatches(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: searchNext(forward: boolean): void;<br>Differences: searchNext(forward: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: clearSslCache(): void;<br>Differences: clearSslCache(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: clearClientAuthenticationCache(): void;<br>Differences: clearClientAuthenticationCache(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: runJavaScript(script: string): Promise\<string>;<br>Differences: runJavaScript(script: string): Promise\<string>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: runJavaScript(script: string, callback: AsyncCallback\<string>): void;<br>Differences: runJavaScript(script: string, callback: AsyncCallback\<string>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: runJavaScriptExt(script: string): Promise\<JsMessageExt>;<br>Differences: runJavaScriptExt(script: string): Promise\<JsMessageExt>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: runJavaScriptExt(script: string, callback: AsyncCallback\<JsMessageExt>): void;<br>Differences: runJavaScriptExt(script: string, callback: AsyncCallback\<JsMessageExt>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getUrl(): string;<br>Differences: getUrl(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: pageUp(top: boolean): void;<br>Differences: pageUp(top: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: pageDown(bottom: boolean): void;<br>Differences: pageDown(bottom: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getOriginalUrl(): string;<br>Differences: getOriginalUrl(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getFavicon(): image.PixelMap;<br>Differences: getFavicon(): image.PixelMap;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: setNetworkAvailable(enable: boolean): void;<br>Differences: setNetworkAvailable(enable: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: hasImage(): Promise\<boolean>;<br>Differences: hasImage(): Promise\<boolean>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: hasImage(callback: AsyncCallback\<boolean>): void;<br>Differences: hasImage(callback: AsyncCallback\<boolean>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getBackForwardEntries(): BackForwardList;<br>Differences: getBackForwardEntries(): BackForwardList;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: removeCache(clearRom: boolean): void;<br>Differences: removeCache(clearRom: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: scrollTo(x: number, y: number): void;<br>Differences: scrollTo(x: number, y: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: scrollBy(deltaX: number, deltaY: number): void;<br>Differences: scrollBy(deltaX: number, deltaY: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: slideScroll(vx: number, vy: number): void;<br>Differences: slideScroll(vx: number, vy: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: serializeWebState(): Uint8Array;<br>Differences: serializeWebState(): Uint8Array;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: restoreWebState(state: Uint8Array): void;<br>Differences: restoreWebState(state: Uint8Array): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static customizeSchemes(schemes: Array\<WebCustomScheme>): void;<br>Differences: static customizeSchemes(schemes: Array\<WebCustomScheme>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getCertificate(): Promise\<Array\<cert.X509Cert>>;<br>Differences: getCertificate(): Promise\<Array\<cert.X509Cert>>;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getCertificate(callback: AsyncCallback\<Array\<cert.X509Cert>>): void;<br>Differences: getCertificate(callback: AsyncCallback\<Array\<cert.X509Cert>>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: setAudioMuted(mute: boolean): void;<br>Differences: setAudioMuted(mute: boolean): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: prefetchPage(url: string, additionalHeaders?: Array\<WebHeader>): void;<br>Differences: prefetchPage(url: string, additionalHeaders?: Array\<WebHeader>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;<br>Differences: static prepareForPageLoad(url: string, preconnectable: boolean, numSockets: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: setCustomUserAgent(userAgent: string): void;<br>Differences: setCustomUserAgent(userAgent: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getCustomUserAgent(): string;<br>Differences: getCustomUserAgent(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: static setConnectionTimeout(timeout: number): void;<br>Differences: static setConnectionTimeout(timeout: number): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>Differences: setDownloadDelegate(delegate: WebDownloadDelegate): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: startDownload(url: string): void;<br>Differences: startDownload(url: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: postUrl(url: string, postData: ArrayBuffer): void;<br>Differences: postUrl(url: string, postData: ArrayBuffer): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter;<br>Differences: createWebPrintDocumentAdapter(jobName: string): print.PrintDocumentAdapter;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: getSecurityLevel(): SecurityLevel;<br>Differences: getSecurityLevel(): SecurityLevel;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebviewController;<br>API declaration: isIncognitoMode(): boolean;<br>Differences: isIncognitoMode(): boolean;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum WebDownloadState<br>Differences: enum WebDownloadState|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: IN_PROGRESS = 0<br>Differences: IN_PROGRESS = 0|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: COMPLETED<br>Differences: COMPLETED|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: CANCELED<br>Differences: CANCELED|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: INTERRUPTED<br>Differences: INTERRUPTED|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: PENDING<br>Differences: PENDING|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: PAUSED<br>Differences: PAUSED|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadState;<br>API declaration: UNKNOWN<br>Differences: UNKNOWN|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: enum WebDownloadErrorCode<br>Differences: enum WebDownloadErrorCode|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: ERROR_UNKNOWN = 0<br>Differences: ERROR_UNKNOWN = 0|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_FAILED = 1<br>Differences: FILE_FAILED = 1|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_ACCESS_DENIED = 2<br>Differences: FILE_ACCESS_DENIED = 2|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_NO_SPACE = 3<br>Differences: FILE_NO_SPACE = 3|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_NAME_TOO_LONG = 5<br>Differences: FILE_NAME_TOO_LONG = 5|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_TOO_LARGE = 6<br>Differences: FILE_TOO_LARGE = 6|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_TRANSIENT_ERROR = 10<br>Differences: FILE_TRANSIENT_ERROR = 10|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_BLOCKED = 11<br>Differences: FILE_BLOCKED = 11|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_TOO_SHORT = 13<br>Differences: FILE_TOO_SHORT = 13|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_HASH_MISMATCH = 14<br>Differences: FILE_HASH_MISMATCH = 14|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: FILE_SAME_AS_SOURCE = 15<br>Differences: FILE_SAME_AS_SOURCE = 15|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: NETWORK_FAILED = 20<br>Differences: NETWORK_FAILED = 20|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: NETWORK_TIMEOUT = 21<br>Differences: NETWORK_TIMEOUT = 21|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: NETWORK_DISCONNECTED = 22<br>Differences: NETWORK_DISCONNECTED = 22|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: NETWORK_SERVER_DOWN = 23<br>Differences: NETWORK_SERVER_DOWN = 23|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: NETWORK_INVALID_REQUEST = 24<br>Differences: NETWORK_INVALID_REQUEST = 24|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_FAILED = 30<br>Differences: SERVER_FAILED = 30|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_NO_RANGE = 31<br>Differences: SERVER_NO_RANGE = 31|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_BAD_CONTENT = 33<br>Differences: SERVER_BAD_CONTENT = 33|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_UNAUTHORIZED = 34<br>Differences: SERVER_UNAUTHORIZED = 34|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_CERT_PROBLEM = 35<br>Differences: SERVER_CERT_PROBLEM = 35|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_FORBIDDEN = 36<br>Differences: SERVER_FORBIDDEN = 36|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_UNREACHABLE = 37<br>Differences: SERVER_UNREACHABLE = 37|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_CONTENT_LENGTH_MISMATCH = 38<br>Differences: SERVER_CONTENT_LENGTH_MISMATCH = 38|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: SERVER_CROSS_ORIGIN_REDIRECT = 39<br>Differences: SERVER_CROSS_ORIGIN_REDIRECT = 39|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: USER_CANCELED = 40<br>Differences: USER_CANCELED = 40|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: USER_SHUTDOWN = 41<br>Differences: USER_SHUTDOWN = 41|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadErrorCode;<br>API declaration: CRASH = 50<br>Differences: CRASH = 50|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebDownloadItem<br>Differences: class WebDownloadItem|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getGuid(): string;<br>Differences: getGuid(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getCurrentSpeed(): number;<br>Differences: getCurrentSpeed(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getPercentComplete(): number;<br>Differences: getPercentComplete(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getTotalBytes(): number;<br>Differences: getTotalBytes(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getState(): WebDownloadState;<br>Differences: getState(): WebDownloadState;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getLastErrorCode(): WebDownloadErrorCode;<br>Differences: getLastErrorCode(): WebDownloadErrorCode;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getMethod(): string;<br>Differences: getMethod(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getMimeType(): string;<br>Differences: getMimeType(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getUrl(): string;<br>Differences: getUrl(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getSuggestedFileName(): string;<br>Differences: getSuggestedFileName(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: start(downloadPath: string): void;<br>Differences: start(downloadPath: string): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: cancel(): void;<br>Differences: cancel(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: pause(): void;<br>Differences: pause(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: resume(): void;<br>Differences: resume(): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getReceivedBytes(): number;<br>Differences: getReceivedBytes(): number;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: getFullPath(): string;<br>Differences: getFullPath(): string;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: serialize(): Uint8Array;<br>Differences: serialize(): Uint8Array;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadItem;<br>API declaration: static deserialize(serializedData: Uint8Array): WebDownloadItem;<br>Differences: static deserialize(serializedData: Uint8Array): WebDownloadItem;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebDownloadDelegate<br>Differences: class WebDownloadDelegate|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadDelegate;<br>API declaration: onBeforeDownload(callback: Callback\<WebDownloadItem>): void;<br>Differences: onBeforeDownload(callback: Callback\<WebDownloadItem>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadDelegate;<br>API declaration: onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;<br>Differences: onDownloadUpdated(callback: Callback\<WebDownloadItem>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadDelegate;<br>API declaration: onDownloadFinish(callback: Callback\<WebDownloadItem>): void;<br>Differences: onDownloadFinish(callback: Callback\<WebDownloadItem>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadDelegate;<br>API declaration: onDownloadFailed(callback: Callback\<WebDownloadItem>): void;<br>Differences: onDownloadFailed(callback: Callback\<WebDownloadItem>): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: webview;<br>API declaration: class WebDownloadManager<br>Differences: class WebDownloadManager|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadManager;<br>API declaration: static setDownloadDelegate(delegate: WebDownloadDelegate): void;<br>Differences: static setDownloadDelegate(delegate: WebDownloadDelegate): void;|api/@ohos.web.webview.d.ts|
|New API|NA|Class name: WebDownloadManager;<br>API declaration: static resumeDownload(webDownloadItem: WebDownloadItem): void;<br>Differences: static resumeDownload(webDownloadItem: WebDownloadItem): void;|api/@ohos.web.webview.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.web.webview.d.ts<br>Differences: ArkWeb|api/@ohos.web.webview.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.ArkWeb.d.ts<br>Differences: ArkWeb|kits/@kit.ArkWeb.d.ts|
