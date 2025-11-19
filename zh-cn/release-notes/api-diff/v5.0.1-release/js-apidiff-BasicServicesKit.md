| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：deviceInfo；<br>API声明：const distributionOSApiName: string;<br>差异内容：const distributionOSApiName: string;|api/@ohos.deviceInfo.d.ts|
|新增API|NA|类名：pasteboard；<br>API声明：enum Pattern<br>差异内容：enum Pattern|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：Pattern；<br>API声明：URL = 0<br>差异内容：URL = 0|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：Pattern；<br>API声明：NUMBER = 1<br>差异内容：NUMBER = 1|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：Pattern；<br>API声明：EMAIL_ADDRESS = 2<br>差异内容：EMAIL_ADDRESS = 2|api/@ohos.pasteboard.d.ts|
|新增API|NA|类名：SystemPasteboard；<br>API声明：detectPatterns(patterns: Array\<Pattern>): Promise\<Array\<Pattern>>;<br>差异内容：detectPatterns(patterns: Array\<Pattern>): Promise\<Array\<Pattern>>;|api/@ohos.pasteboard.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace customConfig<br>差异内容：NA|类名：global；<br>API声明：declare namespace customConfig<br>差异内容：atomicservice|api/@ohos.customization.customConfig.d.ts|
|API从不支持元服务到支持元服务|类名：customConfig；<br>API声明：function getChannelId(): string;<br>差异内容：NA|类名：customConfig；<br>API声明：function getChannelId(): string;<br>差异内容：atomicservice|api/@ohos.customization.customConfig.d.ts|
