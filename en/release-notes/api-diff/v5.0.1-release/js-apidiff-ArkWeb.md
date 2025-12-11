| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: webview;<br>API declaration: interface ScrollOffset<br>Differences: interface ScrollOffset|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: ScrollOffset;<br>API declaration: x: number;<br>Differences: x: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: ScrollOffset;<br>API declaration: y: number;<br>Differences: y: number;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebviewController;<br>API declaration: getScrollOffset(): ScrollOffset;<br>Differences: getScrollOffset(): ScrollOffset;|api/@ohos.web.webview.d.ts|
|New API |NA|Class name: WebContextMenuParam;<br>API declaration: getPreviewWidth(): number;<br>Differences: getPreviewWidth(): number;|component/web.d.ts|
|New API |NA|Class name: WebContextMenuParam;<br>API declaration: getPreviewHeight(): number;<br>Differences: getPreviewHeight(): number;|component/web.d.ts|
|New API |NA|Class name: WebResourceResponse;<br>API declaration: getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>Differences: getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;|component/web.d.ts|
|New API |NA|Class name: WebResourceResponse;<br>API declaration: getResponseIsReady(): boolean;<br>Differences: getResponseIsReady(): boolean;|component/web.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare enum WebElementType<br>Differences: declare enum WebElementType|component/web.d.ts|
|New API |NA|Class name: WebElementType;<br>API declaration: IMAGE = 1<br>Differences: IMAGE = 1|component/web.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare enum WebResponseType<br>Differences: declare enum WebResponseType|component/web.d.ts|
|New API |NA|Class name: WebResponseType;<br>API declaration: LONG_PRESS = 1<br>Differences: LONG_PRESS = 1|component/web.d.ts|
|New API |NA|Class name: global;<br>API declaration: declare interface SelectionMenuOptionsExt<br>Differences: declare interface SelectionMenuOptionsExt|component/web.d.ts|
|New API |NA|Class name: SelectionMenuOptionsExt;<br>API declaration: onAppear?: Callback\<void>;<br>Differences: onAppear?: Callback\<void>;|component/web.d.ts|
|New API |NA|Class name: SelectionMenuOptionsExt;<br>API declaration: onDisappear?: Callback\<void>;<br>Differences: onDisappear?: Callback\<void>;|component/web.d.ts|
|New API |NA|Class name: SelectionMenuOptionsExt;<br>API declaration: preview?: CustomBuilder;<br>Differences: preview?: CustomBuilder;|component/web.d.ts|
|New API |NA|Class name: SelectionMenuOptionsExt;<br>API declaration: menuType?: MenuType;<br>Differences: menuType?: MenuType;|component/web.d.ts|
|New API |NA|Class name: WebAttribute;<br>API declaration: enableHapticFeedback(enabled: boolean): WebAttribute;<br>Differences: enableHapticFeedback(enabled: boolean): WebAttribute;|component/web.d.ts|
|New API |NA|Class name: WebAttribute;<br>API declaration: bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType, options?: SelectionMenuOptionsExt): WebAttribute;<br>Differences: bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType, options?: SelectionMenuOptionsExt): WebAttribute;|component/web.d.ts|
