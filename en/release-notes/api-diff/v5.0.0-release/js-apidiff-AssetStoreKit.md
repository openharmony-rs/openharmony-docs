| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: asset;<br>API declaration: function remove(query: AssetMap): Promise\<void>;<br>Differences: NA|Class name: asset;<br>API declaration: function remove(query: AssetMap): Promise\<void>;<br>Differences: 24000015|api/@ohos.security.asset.d.ts|
|Permission change|Class name: Tag;<br>API declaration: IS_PERSISTENT = TagType.BOOL \| 0x11<br>Differences: ohos.permission.STORE_PERSISTENT_DATA|Class name: Tag;<br>API declaration: IS_PERSISTENT = TagType.BOOL \| 0x11<br>Differences: NA|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function addSync(attributes: AssetMap): void;<br>Differences: function addSync(attributes: AssetMap): void;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function removeSync(query: AssetMap): void;<br>Differences: function removeSync(query: AssetMap): void;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;<br>Differences: function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function preQuerySync(query: AssetMap): Uint8Array;<br>Differences: function preQuerySync(query: AssetMap): Uint8Array;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function querySync(query: AssetMap): Array\<AssetMap>;<br>Differences: function querySync(query: AssetMap): Array\<AssetMap>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function postQuerySync(handle: AssetMap): void;<br>Differences: function postQuerySync(handle: AssetMap): void;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: SyncType;<br>API declaration: TRUSTED_ACCOUNT = 1 \<\< 2<br>Differences: TRUSTED_ACCOUNT = 1 \<\< 2|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum OperationType<br>Differences: enum OperationType|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: OperationType;<br>API declaration: NEED_SYNC = 0<br>Differences: NEED_SYNC = 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: OperationType;<br>API declaration: NEED_LOGOUT = 1<br>Differences: NEED_LOGOUT = 1|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34<br>Differences: DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35<br>Differences: DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36<br>Differences: DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37<br>Differences: DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: UPDATE_TIME = TagType.BYTES \| 0x45<br>Differences: UPDATE_TIME = TagType.BYTES \| 0x45|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: OPERATION_TYPE = TagType.NUMBER \| 0x46<br>Differences: OPERATION_TYPE = TagType.NUMBER \| 0x46|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: NOT_SYSTEM_APPLICATION = 202<br>Differences: NOT_SYSTEM_APPLICATION = 202|api/@ohos.security.asset.d.ts|
|Kit change|Asset Store Kit|AssetStoreKit|api/@ohos.security.asset.d.ts|
|Kit change|Asset Store Kit|AssetStoreKit|kits/@kit.AssetStoreKit.d.ts|
