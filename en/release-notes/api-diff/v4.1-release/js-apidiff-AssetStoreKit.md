| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace asset<br>Differences: declare namespace asset|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function add(attributes: AssetMap): Promise\<void>;<br>Differences: function add(attributes: AssetMap): Promise\<void>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function remove(query: AssetMap): Promise\<void>;<br>Differences: function remove(query: AssetMap): Promise\<void>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function update(query: AssetMap, attributesToUpdate: AssetMap): Promise\<void>;<br>Differences: function update(query: AssetMap, attributesToUpdate: AssetMap): Promise\<void>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function preQuery(query: AssetMap): Promise\<Uint8Array>;<br>Differences: function preQuery(query: AssetMap): Promise\<Uint8Array>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function query(query: AssetMap): Promise\<Array\<AssetMap>>;<br>Differences: function query(query: AssetMap): Promise\<Array\<AssetMap>>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: function postQuery(handle: AssetMap): Promise\<void>;<br>Differences: function postQuery(handle: AssetMap): Promise\<void>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: type AssetMap = Map\<Tag, Value>;<br>Differences: type AssetMap = Map\<Tag, Value>;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: type Value = boolean \| number \| Uint8Array;<br>Differences: type Value = boolean \| number \| Uint8Array;|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum Accessibility<br>Differences: enum Accessibility|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Accessibility;<br>API declaration: DEVICE_POWERED_ON = 0<br>Differences: DEVICE_POWERED_ON = 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Accessibility;<br>API declaration: DEVICE_FIRST_UNLOCKED = 1<br>Differences: DEVICE_FIRST_UNLOCKED = 1|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Accessibility;<br>API declaration: DEVICE_UNLOCKED = 2<br>Differences: DEVICE_UNLOCKED = 2|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum AuthType<br>Differences: enum AuthType|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: AuthType;<br>API declaration: NONE = 0x00<br>Differences: NONE = 0x00|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: AuthType;<br>API declaration: ANY = 0xFF<br>Differences: ANY = 0xFF|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum SyncType<br>Differences: enum SyncType|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: SyncType;<br>API declaration: NEVER = 0<br>Differences: NEVER = 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: SyncType;<br>API declaration: THIS_DEVICE = 1 \<\< 0<br>Differences: THIS_DEVICE = 1 \<\< 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: SyncType;<br>API declaration: TRUSTED_DEVICE = 1 \<\< 1<br>Differences: TRUSTED_DEVICE = 1 \<\< 1|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum ConflictResolution<br>Differences: enum ConflictResolution|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ConflictResolution;<br>API declaration: OVERWRITE = 0<br>Differences: OVERWRITE = 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ConflictResolution;<br>API declaration: THROW_ERROR = 1<br>Differences: THROW_ERROR = 1|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum ReturnType<br>Differences: enum ReturnType|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ReturnType;<br>API declaration: ALL = 0<br>Differences: ALL = 0|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ReturnType;<br>API declaration: ATTRIBUTES = 1<br>Differences: ATTRIBUTES = 1|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum TagType<br>Differences: enum TagType|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: TagType;<br>API declaration: BOOL = 0x01 \<\< 28<br>Differences: BOOL = 0x01 \<\< 28|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: TagType;<br>API declaration: NUMBER = 0x02 \<\< 28<br>Differences: NUMBER = 0x02 \<\< 28|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: TagType;<br>API declaration: BYTES = 0x03 \<\< 28<br>Differences: BYTES = 0x03 \<\< 28|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum Tag<br>Differences: enum Tag|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: SECRET = TagType.BYTES \| 0x01<br>Differences: SECRET = TagType.BYTES \| 0x01|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: ALIAS = TagType.BYTES \| 0x02<br>Differences: ALIAS = TagType.BYTES \| 0x02|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: ACCESSIBILITY = TagType.NUMBER \| 0x03<br>Differences: ACCESSIBILITY = TagType.NUMBER \| 0x03|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: REQUIRE_PASSWORD_SET = TagType.BOOL \| 0x04<br>Differences: REQUIRE_PASSWORD_SET = TagType.BOOL \| 0x04|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: AUTH_TYPE = TagType.NUMBER \| 0x05<br>Differences: AUTH_TYPE = TagType.NUMBER \| 0x05|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: AUTH_VALIDITY_PERIOD = TagType.NUMBER \| 0x06<br>Differences: AUTH_VALIDITY_PERIOD = TagType.NUMBER \| 0x06|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: AUTH_CHALLENGE = TagType.BYTES \| 0x07<br>Differences: AUTH_CHALLENGE = TagType.BYTES \| 0x07|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: AUTH_TOKEN = TagType.BYTES \| 0x08<br>Differences: AUTH_TOKEN = TagType.BYTES \| 0x08|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: SYNC_TYPE = TagType.NUMBER \| 0x10<br>Differences: SYNC_TYPE = TagType.NUMBER \| 0x10|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: IS_PERSISTENT = TagType.BOOL \| 0x11<br>Differences: IS_PERSISTENT = TagType.BOOL \| 0x11|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_CRITICAL_1 = TagType.BYTES \| 0x20<br>Differences: DATA_LABEL_CRITICAL_1 = TagType.BYTES \| 0x20|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_CRITICAL_2 = TagType.BYTES \| 0x21<br>Differences: DATA_LABEL_CRITICAL_2 = TagType.BYTES \| 0x21|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_CRITICAL_3 = TagType.BYTES \| 0x22<br>Differences: DATA_LABEL_CRITICAL_3 = TagType.BYTES \| 0x22|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_CRITICAL_4 = TagType.BYTES \| 0x23<br>Differences: DATA_LABEL_CRITICAL_4 = TagType.BYTES \| 0x23|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_1 = TagType.BYTES \| 0x30<br>Differences: DATA_LABEL_NORMAL_1 = TagType.BYTES \| 0x30|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_2 = TagType.BYTES \| 0x31<br>Differences: DATA_LABEL_NORMAL_2 = TagType.BYTES \| 0x31|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_3 = TagType.BYTES \| 0x32<br>Differences: DATA_LABEL_NORMAL_3 = TagType.BYTES \| 0x32|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: DATA_LABEL_NORMAL_4 = TagType.BYTES \| 0x33<br>Differences: DATA_LABEL_NORMAL_4 = TagType.BYTES \| 0x33|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: RETURN_TYPE = TagType.NUMBER \| 0x40<br>Differences: RETURN_TYPE = TagType.NUMBER \| 0x40|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: RETURN_LIMIT = TagType.NUMBER \| 0x41<br>Differences: RETURN_LIMIT = TagType.NUMBER \| 0x41|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: RETURN_OFFSET = TagType.NUMBER \| 0x42<br>Differences: RETURN_OFFSET = TagType.NUMBER \| 0x42|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: RETURN_ORDERED_BY = TagType.NUMBER \| 0x43<br>Differences: RETURN_ORDERED_BY = TagType.NUMBER \| 0x43|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: Tag;<br>API declaration: CONFLICT_RESOLUTION = TagType.NUMBER \| 0x44<br>Differences: CONFLICT_RESOLUTION = TagType.NUMBER \| 0x44|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: asset;<br>API declaration: enum ErrorCode<br>Differences: enum ErrorCode|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: PERMISSION_DENIED = 201<br>Differences: PERMISSION_DENIED = 201|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: INVALID_ARGUMENT = 401<br>Differences: INVALID_ARGUMENT = 401|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: SERVICE_UNAVAILABLE = 24000001<br>Differences: SERVICE_UNAVAILABLE = 24000001|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: NOT_FOUND = 24000002<br>Differences: NOT_FOUND = 24000002|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: DUPLICATED = 24000003<br>Differences: DUPLICATED = 24000003|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ACCESS_DENIED = 24000004<br>Differences: ACCESS_DENIED = 24000004|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: STATUS_MISMATCH = 24000005<br>Differences: STATUS_MISMATCH = 24000005|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: OUT_OF_MEMORY = 24000006<br>Differences: OUT_OF_MEMORY = 24000006|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: DATA_CORRUPTED = 24000007<br>Differences: DATA_CORRUPTED = 24000007|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: DATABASE_ERROR = 24000008<br>Differences: DATABASE_ERROR = 24000008|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: CRYPTO_ERROR = 24000009<br>Differences: CRYPTO_ERROR = 24000009|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: IPC_ERROR = 24000010<br>Differences: IPC_ERROR = 24000010|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: BMS_ERROR = 24000011<br>Differences: BMS_ERROR = 24000011|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ACCOUNT_ERROR = 24000012<br>Differences: ACCOUNT_ERROR = 24000012|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: ACCESS_TOKEN_ERROR = 24000013<br>Differences: ACCESS_TOKEN_ERROR = 24000013|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: FILE_OPERATION_ERROR = 24000014<br>Differences: FILE_OPERATION_ERROR = 24000014|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: GET_SYSTEM_TIME_ERROR = 24000015<br>Differences: GET_SYSTEM_TIME_ERROR = 24000015|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: LIMIT_EXCEEDED = 24000016<br>Differences: LIMIT_EXCEEDED = 24000016|api/@ohos.security.asset.d.ts|
|New API|NA|Class name: ErrorCode;<br>API declaration: UNSUPPORTED = 24000017<br>Differences: UNSUPPORTED = 24000017|api/@ohos.security.asset.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.security.asset.d.ts<br>Differences: Asset Store Kit|api/@ohos.security.asset.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.AssetStoreKit.d.ts<br>Differences: Asset Store Kit|kits/@kit.AssetStoreKit.d.ts|
