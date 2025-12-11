| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|删除错误码|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：201|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：NA|api/@ohos.security.asset.d.ts|
|删除错误码|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：201|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：NA|api/@ohos.security.asset.d.ts|
|新增API|NA|类名：Tag；<br>API声明：REQUIRE_ATTR_ENCRYPTED = TagType.BOOL \| 0x47<br>差异内容：REQUIRE_ATTR_ENCRYPTED = TagType.BOOL \| 0x47|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace asset<br>差异内容：NA|类名：global；<br>API声明：declare namespace asset<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function add(attributes: AssetMap): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：NA|类名：asset；<br>API声明：function addSync(attributes: AssetMap): void;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function remove(query: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function remove(query: AssetMap): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function removeSync(query: AssetMap): void;<br>差异内容：NA|类名：asset；<br>API声明：function removeSync(query: AssetMap): void;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function update(query: AssetMap, attributesToUpdate: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function update(query: AssetMap, attributesToUpdate: AssetMap): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;<br>差异内容：NA|类名：asset；<br>API声明：function updateSync(query: AssetMap, attributesToUpdate: AssetMap): void;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function preQuery(query: AssetMap): Promise\<Uint8Array>;<br>差异内容：NA|类名：asset；<br>API声明：function preQuery(query: AssetMap): Promise\<Uint8Array>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function preQuerySync(query: AssetMap): Uint8Array;<br>差异内容：NA|类名：asset；<br>API声明：function preQuerySync(query: AssetMap): Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function query(query: AssetMap): Promise\<Array\<AssetMap>>;<br>差异内容：NA|类名：asset；<br>API声明：function query(query: AssetMap): Promise\<Array\<AssetMap>>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function querySync(query: AssetMap): Array\<AssetMap>;<br>差异内容：NA|类名：asset；<br>API声明：function querySync(query: AssetMap): Array\<AssetMap>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function postQuery(handle: AssetMap): Promise\<void>;<br>差异内容：NA|类名：asset；<br>API声明：function postQuery(handle: AssetMap): Promise\<void>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：function postQuerySync(handle: AssetMap): void;<br>差异内容：NA|类名：asset；<br>API声明：function postQuerySync(handle: AssetMap): void;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：type AssetMap = Map\<Tag, Value>;<br>差异内容：NA|类名：asset；<br>API声明：type AssetMap = Map\<Tag, Value>;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：type Value = boolean \| number \| Uint8Array;<br>差异内容：NA|类名：asset；<br>API声明：type Value = boolean \| number \| Uint8Array;<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum Accessibility<br>差异内容：NA|类名：asset；<br>API声明：enum Accessibility<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Accessibility；<br>API声明：DEVICE_POWERED_ON = 0<br>差异内容：NA|类名：Accessibility；<br>API声明：DEVICE_POWERED_ON = 0<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Accessibility；<br>API声明：DEVICE_FIRST_UNLOCKED = 1<br>差异内容：NA|类名：Accessibility；<br>API声明：DEVICE_FIRST_UNLOCKED = 1<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Accessibility；<br>API声明：DEVICE_UNLOCKED = 2<br>差异内容：NA|类名：Accessibility；<br>API声明：DEVICE_UNLOCKED = 2<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum AuthType<br>差异内容：NA|类名：asset；<br>API声明：enum AuthType<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：AuthType；<br>API声明：NONE = 0x00<br>差异内容：NA|类名：AuthType；<br>API声明：NONE = 0x00<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：AuthType；<br>API声明：ANY = 0xFF<br>差异内容：NA|类名：AuthType；<br>API声明：ANY = 0xFF<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum SyncType<br>差异内容：NA|类名：asset；<br>API声明：enum SyncType<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：SyncType；<br>API声明：NEVER = 0<br>差异内容：NA|类名：SyncType；<br>API声明：NEVER = 0<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：SyncType；<br>API声明：THIS_DEVICE = 1 \<\< 0<br>差异内容：NA|类名：SyncType；<br>API声明：THIS_DEVICE = 1 \<\< 0<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：SyncType；<br>API声明：TRUSTED_DEVICE = 1 \<\< 1<br>差异内容：NA|类名：SyncType；<br>API声明：TRUSTED_DEVICE = 1 \<\< 1<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：SyncType；<br>API声明：TRUSTED_ACCOUNT = 1 \<\< 2<br>差异内容：NA|类名：SyncType；<br>API声明：TRUSTED_ACCOUNT = 1 \<\< 2<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum ConflictResolution<br>差异内容：NA|类名：asset；<br>API声明：enum ConflictResolution<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ConflictResolution；<br>API声明：OVERWRITE = 0<br>差异内容：NA|类名：ConflictResolution；<br>API声明：OVERWRITE = 0<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ConflictResolution；<br>API声明：THROW_ERROR = 1<br>差异内容：NA|类名：ConflictResolution；<br>API声明：THROW_ERROR = 1<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum ReturnType<br>差异内容：NA|类名：asset；<br>API声明：enum ReturnType<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ReturnType；<br>API声明：ALL = 0<br>差异内容：NA|类名：ReturnType；<br>API声明：ALL = 0<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ReturnType；<br>API声明：ATTRIBUTES = 1<br>差异内容：NA|类名：ReturnType；<br>API声明：ATTRIBUTES = 1<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum TagType<br>差异内容：NA|类名：asset；<br>API声明：enum TagType<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：TagType；<br>API声明：BOOL = 0x01 \<\< 28<br>差异内容：NA|类名：TagType；<br>API声明：BOOL = 0x01 \<\< 28<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：TagType；<br>API声明：NUMBER = 0x02 \<\< 28<br>差异内容：NA|类名：TagType；<br>API声明：NUMBER = 0x02 \<\< 28<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：TagType；<br>API声明：BYTES = 0x03 \<\< 28<br>差异内容：NA|类名：TagType；<br>API声明：BYTES = 0x03 \<\< 28<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum Tag<br>差异内容：NA|类名：asset；<br>API声明：enum Tag<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：SECRET = TagType.BYTES \| 0x01<br>差异内容：NA|类名：Tag；<br>API声明：SECRET = TagType.BYTES \| 0x01<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：ALIAS = TagType.BYTES \| 0x02<br>差异内容：NA|类名：Tag；<br>API声明：ALIAS = TagType.BYTES \| 0x02<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：ACCESSIBILITY = TagType.NUMBER \| 0x03<br>差异内容：NA|类名：Tag；<br>API声明：ACCESSIBILITY = TagType.NUMBER \| 0x03<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：REQUIRE_PASSWORD_SET = TagType.BOOL \| 0x04<br>差异内容：NA|类名：Tag；<br>API声明：REQUIRE_PASSWORD_SET = TagType.BOOL \| 0x04<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：AUTH_TYPE = TagType.NUMBER \| 0x05<br>差异内容：NA|类名：Tag；<br>API声明：AUTH_TYPE = TagType.NUMBER \| 0x05<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：AUTH_VALIDITY_PERIOD = TagType.NUMBER \| 0x06<br>差异内容：NA|类名：Tag；<br>API声明：AUTH_VALIDITY_PERIOD = TagType.NUMBER \| 0x06<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：AUTH_CHALLENGE = TagType.BYTES \| 0x07<br>差异内容：NA|类名：Tag；<br>API声明：AUTH_CHALLENGE = TagType.BYTES \| 0x07<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：AUTH_TOKEN = TagType.BYTES \| 0x08<br>差异内容：NA|类名：Tag；<br>API声明：AUTH_TOKEN = TagType.BYTES \| 0x08<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：SYNC_TYPE = TagType.NUMBER \| 0x10<br>差异内容：NA|类名：Tag；<br>API声明：SYNC_TYPE = TagType.NUMBER \| 0x10<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_1 = TagType.BYTES \| 0x20<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_1 = TagType.BYTES \| 0x20<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_2 = TagType.BYTES \| 0x21<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_2 = TagType.BYTES \| 0x21<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_3 = TagType.BYTES \| 0x22<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_3 = TagType.BYTES \| 0x22<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_4 = TagType.BYTES \| 0x23<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_CRITICAL_4 = TagType.BYTES \| 0x23<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_1 = TagType.BYTES \| 0x30<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_1 = TagType.BYTES \| 0x30<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_2 = TagType.BYTES \| 0x31<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_2 = TagType.BYTES \| 0x31<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_3 = TagType.BYTES \| 0x32<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_3 = TagType.BYTES \| 0x32<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_4 = TagType.BYTES \| 0x33<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_4 = TagType.BYTES \| 0x33<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_1 = TagType.BYTES \| 0x34<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_2 = TagType.BYTES \| 0x35<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_3 = TagType.BYTES \| 0x36<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37<br>差异内容：NA|类名：Tag；<br>API声明：DATA_LABEL_NORMAL_LOCAL_4 = TagType.BYTES \| 0x37<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：RETURN_TYPE = TagType.NUMBER \| 0x40<br>差异内容：NA|类名：Tag；<br>API声明：RETURN_TYPE = TagType.NUMBER \| 0x40<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：RETURN_LIMIT = TagType.NUMBER \| 0x41<br>差异内容：NA|类名：Tag；<br>API声明：RETURN_LIMIT = TagType.NUMBER \| 0x41<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：RETURN_OFFSET = TagType.NUMBER \| 0x42<br>差异内容：NA|类名：Tag；<br>API声明：RETURN_OFFSET = TagType.NUMBER \| 0x42<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：RETURN_ORDERED_BY = TagType.NUMBER \| 0x43<br>差异内容：NA|类名：Tag；<br>API声明：RETURN_ORDERED_BY = TagType.NUMBER \| 0x43<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：CONFLICT_RESOLUTION = TagType.NUMBER \| 0x44<br>差异内容：NA|类名：Tag；<br>API声明：CONFLICT_RESOLUTION = TagType.NUMBER \| 0x44<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：Tag；<br>API声明：UPDATE_TIME = TagType.BYTES \| 0x45<br>差异内容：NA|类名：Tag；<br>API声明：UPDATE_TIME = TagType.BYTES \| 0x45<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：asset；<br>API声明：enum ErrorCode<br>差异内容：NA|类名：asset；<br>API声明：enum ErrorCode<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：INVALID_ARGUMENT = 401<br>差异内容：NA|类名：ErrorCode；<br>API声明：INVALID_ARGUMENT = 401<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：SERVICE_UNAVAILABLE = 24000001<br>差异内容：NA|类名：ErrorCode；<br>API声明：SERVICE_UNAVAILABLE = 24000001<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：NOT_FOUND = 24000002<br>差异内容：NA|类名：ErrorCode；<br>API声明：NOT_FOUND = 24000002<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：DUPLICATED = 24000003<br>差异内容：NA|类名：ErrorCode；<br>API声明：DUPLICATED = 24000003<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：ACCESS_DENIED = 24000004<br>差异内容：NA|类名：ErrorCode；<br>API声明：ACCESS_DENIED = 24000004<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：STATUS_MISMATCH = 24000005<br>差异内容：NA|类名：ErrorCode；<br>API声明：STATUS_MISMATCH = 24000005<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：OUT_OF_MEMORY = 24000006<br>差异内容：NA|类名：ErrorCode；<br>API声明：OUT_OF_MEMORY = 24000006<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：DATA_CORRUPTED = 24000007<br>差异内容：NA|类名：ErrorCode；<br>API声明：DATA_CORRUPTED = 24000007<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：DATABASE_ERROR = 24000008<br>差异内容：NA|类名：ErrorCode；<br>API声明：DATABASE_ERROR = 24000008<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：CRYPTO_ERROR = 24000009<br>差异内容：NA|类名：ErrorCode；<br>API声明：CRYPTO_ERROR = 24000009<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：IPC_ERROR = 24000010<br>差异内容：NA|类名：ErrorCode；<br>API声明：IPC_ERROR = 24000010<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：BMS_ERROR = 24000011<br>差异内容：NA|类名：ErrorCode；<br>API声明：BMS_ERROR = 24000011<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：ACCOUNT_ERROR = 24000012<br>差异内容：NA|类名：ErrorCode；<br>API声明：ACCOUNT_ERROR = 24000012<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：ACCESS_TOKEN_ERROR = 24000013<br>差异内容：NA|类名：ErrorCode；<br>API声明：ACCESS_TOKEN_ERROR = 24000013<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：FILE_OPERATION_ERROR = 24000014<br>差异内容：NA|类名：ErrorCode；<br>API声明：FILE_OPERATION_ERROR = 24000014<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：GET_SYSTEM_TIME_ERROR = 24000015<br>差异内容：NA|类名：ErrorCode；<br>API声明：GET_SYSTEM_TIME_ERROR = 24000015<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：LIMIT_EXCEEDED = 24000016<br>差异内容：NA|类名：ErrorCode；<br>API声明：LIMIT_EXCEEDED = 24000016<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
|API从不支持元服务到支持元服务|类名：ErrorCode；<br>API声明：UNSUPPORTED = 24000017<br>差异内容：NA|类名：ErrorCode；<br>API声明：UNSUPPORTED = 24000017<br>差异内容：atomicservice|api/@ohos.security.asset.d.ts|
