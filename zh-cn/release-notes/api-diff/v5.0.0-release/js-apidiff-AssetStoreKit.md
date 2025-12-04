| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：asset；<br>API声明：function remove(query: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function remove(query: AssetMap): Promise\<void>;<br>差异内容：24000015|api/@ohos.security.asset.d.ts|
|权限变更|类名：Tag；<br>API声明：IS_PERSISTENT = TagType.BOOL \| 0x11<br>差异内容：ohos.permission.STORE_PERSISTENT_DATA|类名：Tag；<br>API声明：IS_PERSISTENT = TagType.BOOL \| 0x11<br>差异内容：NA|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：function addSync(attributes: AssetMap): void;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function removeSync(query: AssetMap): void;<br>差异内容：function removeSync(query: AssetMap): void;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;<br>差异内容：function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function preQuerySync(query: AssetMap): Uint8Array;<br>差异内容：function preQuerySync(query: AssetMap): Uint8Array;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function querySync(query: AssetMap): Array\<AssetMap>;<br>差异内容：function querySync(query: AssetMap): Array\<AssetMap>;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：function postQuerySync(handle: AssetMap): void;<br>差异内容：function postQuerySync(handle: AssetMap): void;|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：SyncType；<br>API声明：TRUSTED_ACCOUNT = 1 \<\< 2<br>差异内容：TRUSTED_ACCOUNT = 1 \<\< 2|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：asset；<br>API声明：enum OperationType<br>差异内容：enum OperationType|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：NEED_SYNC = 0<br>差异内容：NEED_SYNC = 0|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：OperationType；<br>API声明：NEED_LOGOUT = 1<br>差异内容：NEED_LOGOUT = 1|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34<br>差异内容：DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35<br>差异内容：DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36<br>差异内容：DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37<br>差异内容：DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：UPDATE_TIME = TagType.BYTES \| 0x45<br>差异内容：UPDATE_TIME = TagType.BYTES \| 0x45|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：OPERATION_TYPE = TagType.NUMBER \| 0x46<br>差异内容：OPERATION_TYPE = TagType.NUMBER \| 0x46|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：ErrorCode；<br>API声明：NOT_SYSTEM_APPLICATION = 202<br>差异内容：NOT_SYSTEM_APPLICATION = 202|api/@ohos.security.asset.d.ts|
|kit变更|Asset Store Kit|AssetStoreKit|api/@ohos.security.asset.d.ts|
|kit变更|Asset Store Kit|AssetStoreKit|kits/@kit.AssetStoreKit.d.ts|
