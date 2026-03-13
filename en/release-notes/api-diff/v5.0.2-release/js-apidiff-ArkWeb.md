| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|Function change|Class name: WebviewController;<br>API declaration: scrollTo(x: number, y: number): void;<br>DIfferences: NA|Class name: WebviewController;<br>API declaration: scrollTo(x: number, y: number, duration?: number): void;<br>DIfferences: duration?: number|api/@ohos.web.webview.d.ts|
|Function change|Class name: WebviewController;<br>API declaration: scrollBy(deltaX: number, deltaY: number): void;<br>DIfferences: NA|Class name: WebviewController;<br>API declaration: scrollBy(deltaX: number, deltaY: number, duration?: number): void;<br>DIfferences: duration?: number|api/@ohos.web.webview.d.ts|
|Function change|Class name: WebAttribute;<br>API declaration: nestedScroll(value: NestedScrollOptions): WebAttribute;<br>DIfferences: value: NestedScrollOptions|Class name: WebAttribute;<br>API declaration: nestedScroll(value: NestedScrollOptions \| NestedScrollOptionsExt): WebAttribute;<br>DIfferences: value: NestedScrollOptions \| NestedScrollOptionsExt|component/web.d.ts|
|New API |NA|Class name: WebCookieManager;<br>API declaration: static fetchCookie(url: string, incognito: boolean): Promise\<string>;<br>DIfferences: static fetchCookie(url: string, incognito: boolean): Promise\<string>;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebCookieManager;<br>API declaration: static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void;<br>DIfferences: static configCookieSync(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): void;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebCookieManager;<br>API declaration: static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise\<void>;<br>DIfferences: static configCookie(url: string, value: string, incognito: boolean, includeHttpOnly: boolean): Promise\<void>;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: webview;<br>API declaration: enum PressureLevel<br>DIfferences: enum PressureLevel|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PressureLevel;<br>API declaration: MEMORY_PRESSURE_LEVEL_MODERATE = 1<br>DIfferences: MEMORY_PRESSURE_LEVEL_MODERATE = 1|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PressureLevel;<br>API declaration: MEMORY_PRESSURE_LEVEL_CRITICAL = 2<br>DIfferences: MEMORY_PRESSURE_LEVEL_CRITICAL = 2|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: webview;<br>API declaration: class PdfData<br>DIfferences: class PdfData|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfData;<br>API declaration: pdfArrayBuffer(): Uint8Array;<br>DIfferences: pdfArrayBuffer(): Uint8Array;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: webview;<br>API declaration: interface PdfConfiguration<br>DIfferences: interface PdfConfiguration|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: width: number;<br>DIfferences: width: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: height: number;<br>DIfferences: height: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: marginTop: number;<br>DIfferences: marginTop: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: marginBottom: number;<br>DIfferences: marginBottom: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: marginRight: number;<br>DIfferences: marginRight: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: marginLeft: number;<br>DIfferences: marginLeft: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: scale?: number;<br>DIfferences: scale?: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: PdfConfiguration;<br>API declaration: shouldPrintBackground?: boolean;<br>DIfferences: shouldPrintBackground?: boolean;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebviewController;<br>API declaration: createPdf(configuration: PdfConfiguration, callback: AsyncCallback\<PdfData>): void;<br>DIfferences: createPdf(configuration: PdfConfiguration, callback: AsyncCallback\<PdfData>): void;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebviewController;<br>API declaration: createPdf(configuration: PdfConfiguration): Promise\<PdfData>;<br>DIfferences: createPdf(configuration: PdfConfiguration): Promise\<PdfData>;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebviewController;<br>API declaration: static getDefaultUserAgent(): string;<br>DIfferences: static getDefaultUserAgent(): string;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebviewController;<br>API declaration: static trimMemoryByPressureLevel(level: PressureLevel): void;<br>DIfferences: static trimMemoryByPressureLevel(level: PressureLevel): void;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: EventResult;<br>API declaration: setGestureEventResult(result: boolean, stopPropagation: boolean): void;<br>DIfferences: setGestureEventResult(result: boolean, stopPropagation: boolean): void;|component/web.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare enum BlurOnKeyboardHideMode<br>DIfferences: declare enum BlurOnKeyboardHideMode|component/web.d.ts|
|New API |NA|Class name: BlurOnKeyboardHideMode;<br>API declaration: SILENT<br>DIfferences: SILENT|component/web.d.ts|
|New API |NA|Class name: BlurOnKeyboardHideMode;<br>API declaration: BLUR<br>DIfferences: BLUR|component/web.d.ts|
|New API |NA|Class name: WebAttribute;<br>API declaration: blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute;<br>DIfferences: blurOnKeyboardHideMode(mode: BlurOnKeyboardHideMode): WebAttribute;|component/web.d.ts|
|New API |NA|Class name: WebAttribute;<br>API declaration: forceDisplayScrollBar(enabled: boolean): WebAttribute;<br>DIfferences: forceDisplayScrollBar(enabled: boolean): WebAttribute;|component/web.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare interface NestedScrollOptionsExt<br>DIfferences: declare interface NestedScrollOptionsExt|component/web.d.ts|
|New API |NA|Class name: NestedScrollOptionsExt;<br>API declaration: scrollUp?: NestedScrollMode;<br>DIfferences: scrollUp?: NestedScrollMode;|component/web.d.ts|
|New API |NA|Class name: NestedScrollOptionsExt;<br>API declaration: scrollDown?: NestedScrollMode;<br>DIfferences: scrollDown?: NestedScrollMode;|component/web.d.ts|
|New API |NA|Class name: NestedScrollOptionsExt;<br>API declaration: scrollRight?: NestedScrollMode;<br>DIfferences: scrollRight?: NestedScrollMode;|component/web.d.ts|
|New API |NA|Class name: NestedScrollOptionsExt;<br>API declaration: scrollLeft?: NestedScrollMode;<br>DIfferences: scrollLeft?: NestedScrollMode;|component/web.d.ts|
