| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：AdComponent；<br>API声明：@Prop<br>    rollPlayState?: number;<br>差异内容：@Prop<br>    rollPlayState?: number;|api/@ohos.advertising.AdComponent.d.ets|
|新增API|NA|类名：advertising；<br>API声明：function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, needRefresh: boolean): void;<br>差异内容：function registerWebAdInterface(controller: web_webview.WebviewController, context: common.UIAbilityContext, needRefresh: boolean): void;|api/@ohos.advertising.d.ts|
|新增API|NA|类名：advertising；<br>API声明：function deleteWebAdInterface(controller: web_webview.WebviewController, needRefresh: boolean): void;<br>差异内容：function deleteWebAdInterface(controller: web_webview.WebviewController, needRefresh: boolean): void;|api/@ohos.advertising.d.ts|
|API从不支持元服务到支持元服务|类名：AdComponent；<br>API声明：@BuilderParam<br>    adRenderer?: () => void;<br>差异内容：NA|类名：AdComponent；<br>API声明：@BuilderParam<br>    adRenderer?: () => void;<br>差异内容：atomicservice|api/@ohos.advertising.AdComponent.d.ets|
