| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：201|api/@ohos.security.asset.d.ts|
|新增错误码|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：NA|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：201|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function querySyncResult(query: AssetMap): Promise\<SyncResult>;<br>差异内容：function querySyncResult(query: AssetMap): Promise\<SyncResult>;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：enum WrapType<br>差异内容：enum WrapType|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：WrapType；<br>API声明：NEVER = 0<br>差异内容：NEVER = 0|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：WrapType；<br>API声明：TRUSTED_ACCOUNT = 1<br>差异内容：TRUSTED_ACCOUNT = 1|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：interface SyncResult<br>差异内容：interface SyncResult|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：SyncResult；<br>API声明：readonly resultCode: number;<br>差异内容：readonly resultCode: number;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：SyncResult；<br>API声明：readonly totalCount?: number;<br>差异内容：readonly totalCount?: number;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：SyncResult；<br>API声明：readonly failedCount?: number;<br>差异内容：readonly failedCount?: number;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：GROUP_ID = TagType.BYTES \| 0x48<br>差异内容：GROUP_ID = TagType.BYTES \| 0x48|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：WRAP_TYPE = TagType.NUMBER \| 0x49<br>差异内容：WRAP_TYPE = TagType.NUMBER \| 0x49|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：PARAM_VERIFICATION_FAILED = 24000018<br>差异内容：PARAM_VERIFICATION_FAILED = 24000018|api/@ohos.security.asset.d.ts|
