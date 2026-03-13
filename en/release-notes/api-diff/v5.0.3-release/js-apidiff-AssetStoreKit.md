| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: asset;<br>API declaration: function add(attributes: AssetMap): Promise\<void>;<br>DIfferences: NA|Class name: asset;<br>API declaration: function add(attributes: AssetMap): Promise\<void>;<br>DIfferences: 201|api/@ohos.security.asset.d.ts|
|New error code|Class name: asset;<br>API declaration: function addSync(attributes: AssetMap): void;<br>DIfferences: NA|Class name: asset;<br>API declaration: function addSync(attributes: AssetMap): void;<br>DIfferences: 201|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: asset;<br>API declaration: function querySyncResult(query: AssetMap): Promise\<SyncResult>;<br>DIfferences: function querySyncResult(query: AssetMap): Promise\<SyncResult>;|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: asset;<br>API declaration: enum WrapType<br>DIfferences: enum WrapType|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: WrapType;<br>API declaration: NEVER = 0<br>DIfferences: NEVER = 0|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: WrapType;<br>API declaration: TRUSTED_ACCOUNT = 1<br>DIfferences: TRUSTED_ACCOUNT = 1|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: asset;<br>API declaration: interface SyncResult<br>DIfferences: interface SyncResult|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: SyncResult;<br>API declaration: readonly resultCode: number;<br>DIfferences: readonly resultCode: number;|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: SyncResult;<br>API declaration: readonly totalCount?: number;<br>DIfferences: readonly totalCount?: number;|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: SyncResult;<br>API declaration: readonly failedCount?: number;<br>DIfferences: readonly failedCount?: number;|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: Tag;<br>API declaration: GROUP_ID = TagType.BYTES \| 0x48<br>DIfferences: GROUP_ID = TagType.BYTES \| 0x48|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: Tag;<br>API declaration: WRAP_TYPE = TagType.NUMBER \| 0x49<br>DIfferences: WRAP_TYPE = TagType.NUMBER \| 0x49|api/@ohos.security.asset.d.ts|
|New API |NA|Class name: ErrorCode;<br>API declaration: PARAM_VERIFICATION_FAILED = 24000018<br>DIfferences: PARAM_VERIFICATION_FAILED = 24000018|api/@ohos.security.asset.d.ts|
