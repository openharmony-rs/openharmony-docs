| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: deviceInfo;<br>API declaration: const distributionOSApiName: string;<br>Differences: const distributionOSApiName: string;|api/@ohos.deviceInfo.d.ts|
|New API |NA|Class name: pasteboard;<br>API declaration: enum Pattern<br>Differences: enum Pattern|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: Pattern;<br>API declaration: URL = 0<br>Differences: URL = 0|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: Pattern;<br>API declaration: NUMBER = 1<br>Differences: NUMBER = 1|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: Pattern;<br>API declaration: EMAIL_ADDRESS = 2<br>Differences: EMAIL_ADDRESS = 2|api/@ohos.pasteboard.d.ts|
|New API |NA|Class name: SystemPasteboard;<br>API declaration: detectPatterns(patterns: Array\<Pattern>): Promise\<Array\<Pattern>>;<br>Differences: detectPatterns(patterns: Array\<Pattern>): Promise\<Array\<Pattern>>;|api/@ohos.pasteboard.d.ts|
|New support for atomic services|Class name: global;<br>API declaration: declare namespace customConfig<br>Differences: NA|Class name: global;<br>API declaration: declare namespace customConfig<br>Differences: atomicservice|api/@ohos.customization.customConfig.d.ts|
|New support for atomic services|Class name: customConfig;<br>API declaration: function getChannelId(): string;<br>Differences: NA|Class name: customConfig;<br>API declaration: function getChannelId(): string;<br>Differences: atomicservice|api/@ohos.customization.customConfig.d.ts|
