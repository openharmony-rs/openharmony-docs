| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|函数变更|类名：WebviewController；<br>API声明：scrollTo(x: number, y: number): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：scrollTo(x: number, y: number, duration?: number): void;<br>差异内容：duration?: number|api/@ohos.web.webview.d.ts|
|函数变更|类名：WebviewController；<br>API声明：scrollBy(deltaX: number, deltaY: number): void;<br>差异内容：NA|类名：WebviewController；<br>API声明：scrollBy(deltaX: number, deltaY: number, duration?: number): void;<br>差异内容：duration?: number|api/@ohos.web.webview.d.ts|
|函数变更|类名：WebAttribute；<br>API声明：nestedScroll(value: NestedScrollOptions): WebAttribute;<br>差异内容：value: NestedScrollOptions|类名：WebAttribute；<br>API声明：nestedScroll(value: NestedScrollOptions \| NestedScrollOptionsExt): WebAttribute;<br>差异内容：value: NestedScrollOptions \| NestedScrollOptionsExt|component/web.d.ts|
|新增API|NA|类名：WebCookieManager；<br>API声明：static fetchCookie(url: string, incognito: boolean): Promise\<string>;<br>差异内容：static fetchCookie(url: string, incognito: boolean): Promise\<string>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebCookieManager；<br>API声明：static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void;<br>差异内容：static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebCookieManager；<br>API声明：static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise\<void>;<br>差异内容：static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise\<void>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：enum PressureLevel<br>差异内容：enum PressureLevel|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PressureLevel；<br>API声明：MEMORY_PRESSURE_LEVEL_MODERATE = 1<br>差异内容：MEMORY_PRESSURE_LEVEL_MODERATE = 1|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PressureLevel；<br>API声明：MEMORY_PRESSURE_LEVEL_CRITICAL = 2<br>差异内容：MEMORY_PRESSURE_LEVEL_CRITICAL = 2|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：class PdfData<br>差异内容：class PdfData|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfData；<br>API声明：pdfArrayBuffer(): Uint8Array;<br>差异内容：pdfArrayBuffer(): Uint8Array;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：webview；<br>API声明：interface PdfConfiguration<br>差异内容：interface PdfConfiguration|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：width: number;<br>差异内容：width: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：height: number;<br>差异内容：height: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：marginTop: number;<br>差异内容：marginTop: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：marginBottom: number;<br>差异内容：marginBottom: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：marginRight: number;<br>差异内容：marginRight: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：marginLeft: number;<br>差异内容：marginLeft: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：scale?: number;<br>差异内容：scale?: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：PdfConfiguration；<br>API声明：shouldPrintBackground?: boolean;<br>差异内容：shouldPrintBackground?: boolean;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：createPdf(configuration: PdfConfiguration, callback: AsyncCallback\<PdfData>): void;<br>差异内容：createPdf(configuration: PdfConfiguration, callback: AsyncCallback\<PdfData>): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：createPdf(configuration: PdfConfiguration): Promise\<PdfData>;<br>差异内容：createPdf(configuration: PdfConfiguration): Promise\<PdfData>;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static getDefaultUserAgent(): string;<br>差异内容：static getDefaultUserAgent(): string;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：static trimMemoryByPressureLevel(level: PressureLevel): void;<br>差异内容：static trimMemoryByPressureLevel(level: PressureLevel): void;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：EventResult；<br>API声明：setGestureEventResult(result: boolean, stopPropagation: boolean): void;<br>差异内容：setGestureEventResult(result: boolean, stopPropagation: boolean): void;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum BlurOnKeyboardHideMode<br>差异内容：declare enum BlurOnKeyboardHideMode|component/web.d.ts|
|新增API|NA|类名：BlurOnKeyboardHideMode；<br>API声明：SILENT<br>差异内容：SILENT|component/web.d.ts|
|新增API|NA|类名：BlurOnKeyboardHideMode；<br>API声明：BLUR<br>差异内容：BLUR|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute;<br>差异内容：blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：forceDisplayScrollBar(enabled: boolean): WebAttribute;<br>差异内容：forceDisplayScrollBar(enabled: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface NestedScrollOptionsExt<br>差异内容：declare interface NestedScrollOptionsExt|component/web.d.ts|
|新增API|NA|类名：NestedScrollOptionsExt；<br>API声明：scrollUp?: NestedScrollMode;<br>差异内容：scrollUp?: NestedScrollMode;|component/web.d.ts|
|新增API|NA|类名：NestedScrollOptionsExt；<br>API声明：scrollDown?: NestedScrollMode;<br>差异内容：scrollDown?: NestedScrollMode;|component/web.d.ts|
|新增API|NA|类名：NestedScrollOptionsExt；<br>API声明：scrollRight?: NestedScrollMode;<br>差异内容：scrollRight?: NestedScrollMode;|component/web.d.ts|
|新增API|NA|类名：NestedScrollOptionsExt；<br>API声明：scrollLeft?: NestedScrollMode;<br>差异内容：scrollLeft?: NestedScrollMode;|component/web.d.ts|
