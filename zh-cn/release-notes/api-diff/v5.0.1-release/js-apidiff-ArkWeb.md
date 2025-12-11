| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：webview；<br>API声明：interface ScrollOffset<br>差异内容：interface ScrollOffset|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ScrollOffset；<br>API声明：x: number;<br>差异内容：x: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：ScrollOffset；<br>API声明：y: number;<br>差异内容：y: number;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebviewController；<br>API声明：getScrollOffset(): ScrollOffset;<br>差异内容：getScrollOffset(): ScrollOffset;|api/@ohos.web.webview.d.ts|
|新增API|NA|类名：WebContextMenuParam；<br>API声明：getPreviewWidth(): number;<br>差异内容：getPreviewWidth(): number;|component/web.d.ts|
|新增API|NA|类名：WebContextMenuParam；<br>API声明：getPreviewHeight(): number;<br>差异内容：getPreviewHeight(): number;|component/web.d.ts|
|新增API|NA|类名：WebResourceResponse；<br>API声明：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;<br>差异内容：getResponseDataEx(): string \| number \| ArrayBuffer \| Resource \| undefined;|component/web.d.ts|
|新增API|NA|类名：WebResourceResponse；<br>API声明：getResponseIsReady(): boolean;<br>差异内容：getResponseIsReady(): boolean;|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum WebElementType<br>差异内容：declare enum WebElementType|component/web.d.ts|
|新增API|NA|类名：WebElementType；<br>API声明：IMAGE = 1<br>差异内容：IMAGE = 1|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum WebResponseType<br>差异内容：declare enum WebResponseType|component/web.d.ts|
|新增API|NA|类名：WebResponseType；<br>API声明：LONG_PRESS = 1<br>差异内容：LONG_PRESS = 1|component/web.d.ts|
|新增API|NA|类名：global；<br>API声明：declare interface SelectionMenuOptionsExt<br>差异内容：declare interface SelectionMenuOptionsExt|component/web.d.ts|
|新增API|NA|类名：SelectionMenuOptionsExt；<br>API声明：onAppear?: Callback\<void>;<br>差异内容：onAppear?: Callback\<void>;|component/web.d.ts|
|新增API|NA|类名：SelectionMenuOptionsExt；<br>API声明：onDisappear?: Callback\<void>;<br>差异内容：onDisappear?: Callback\<void>;|component/web.d.ts|
|新增API|NA|类名：SelectionMenuOptionsExt；<br>API声明：preview?: CustomBuilder;<br>差异内容：preview?: CustomBuilder;|component/web.d.ts|
|新增API|NA|类名：SelectionMenuOptionsExt；<br>API声明：menuType?: MenuType;<br>差异内容：menuType?: MenuType;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：enableHapticFeedback(enabled: boolean): WebAttribute;<br>差异内容：enableHapticFeedback(enabled: boolean): WebAttribute;|component/web.d.ts|
|新增API|NA|类名：WebAttribute；<br>API声明：bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType, options?: SelectionMenuOptionsExt): WebAttribute;<br>差异内容：bindSelectionMenu(elementType: WebElementType, content: CustomBuilder, responseType: WebResponseType, options?: SelectionMenuOptionsExt): WebAttribute;|component/web.d.ts|
