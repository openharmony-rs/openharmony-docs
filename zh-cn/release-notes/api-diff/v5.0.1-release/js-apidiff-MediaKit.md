| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：AVPlayer；<br>API声明：on(type: 'amplitudeUpdate', callback: Callback\<Array\<number>>): void;<br>差异内容：on(type: 'amplitudeUpdate', callback: Callback\<Array\<number>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：AVPlayer；<br>API声明：off(type: 'amplitudeUpdate', callback?: Callback\<Array\<number>>): void;<br>差异内容：off(type: 'amplitudeUpdate', callback?: Callback\<Array\<number>>): void;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredAudioLanguage?: string;<br>差异内容：preferredAudioLanguage?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackStrategy；<br>API声明：preferredSubtitleLanguage?: string;<br>差异内容：preferredSubtitleLanguage?: string;|api/@ohos.multimedia.media.d.ts|
|新增API|NA|类名：PlaybackSpeed；<br>API声明：SPEED_FORWARD_3_00_X = 7<br>差异内容：SPEED_FORWARD_3_00_X = 7|api/@ohos.multimedia.media.d.ts|
|API从不支持元服务到支持元服务|类名：media；<br>API声明：function createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource;<br>差异内容：NA|类名：media；<br>API声明：function createMediaSourceWithUrl(url: string, headers?: Record\<string, string>): MediaSource;<br>差异内容：atomicservice|api/@ohos.multimedia.media.d.ts|
