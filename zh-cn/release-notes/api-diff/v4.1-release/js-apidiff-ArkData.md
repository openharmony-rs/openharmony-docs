| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace cloudExtension<br>差异内容：declare namespace cloudExtension|api/@ohos.data.cloudExtension.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace commonType<br>差异内容：declare namespace commonType|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：commonType；<br>API声明：enum AssetStatus<br>差异内容：enum AssetStatus|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_NORMAL<br>差异内容：ASSET_NORMAL|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_INSERT<br>差异内容：ASSET_INSERT|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_UPDATE<br>差异内容：ASSET_UPDATE|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_DELETE<br>差异内容：ASSET_DELETE|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_ABNORMAL<br>差异内容：ASSET_ABNORMAL|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_DOWNLOADING<br>差异内容：ASSET_DOWNLOADING|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：commonType；<br>API声明：interface Asset<br>差异内容：interface Asset|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：createTime: string;<br>差异内容：createTime: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：modifyTime: string;<br>差异内容：modifyTime: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：size: string;<br>差异内容：size: string;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：Asset；<br>API声明：status?: AssetStatus;<br>差异内容：status?: AssetStatus;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：commonType；<br>API声明：type Assets = Array\<Asset>;<br>差异内容：type Assets = Array\<Asset>;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：commonType；<br>API声明：type ValueType = null \| number \| string \| boolean \| Uint8Array \| Asset \| Assets;<br>差异内容：type ValueType = null \| number \| string \| boolean \| Uint8Array \| Asset \| Assets;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：commonType；<br>API声明：type ValuesBucket = Record\<string, ValueType>;<br>差异内容：type ValuesBucket = Record\<string, ValueType>;|api/@ohos.data.commonType.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dataAbility<br>差异内容：declare namespace dataAbility|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：dataAbility；<br>API声明：function createRdbPredicates(name: string, dataAbilityPredicates: DataAbilityPredicates): rdb.RdbPredicates;<br>差异内容：function createRdbPredicates(name: string, dataAbilityPredicates: DataAbilityPredicates): rdb.RdbPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：dataAbility；<br>API声明：class DataAbilityPredicates<br>差异内容：class DataAbilityPredicates|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：equalTo(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：equalTo(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：notEqualTo(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：notEqualTo(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：beginWrap(): DataAbilityPredicates;<br>差异内容：beginWrap(): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：endWrap(): DataAbilityPredicates;<br>差异内容：endWrap(): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：or(): DataAbilityPredicates;<br>差异内容：or(): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：and(): DataAbilityPredicates;<br>差异内容：and(): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：contains(field: string, value: string): DataAbilityPredicates;<br>差异内容：contains(field: string, value: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：beginsWith(field: string, value: string): DataAbilityPredicates;<br>差异内容：beginsWith(field: string, value: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：endsWith(field: string, value: string): DataAbilityPredicates;<br>差异内容：endsWith(field: string, value: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：isNull(field: string): DataAbilityPredicates;<br>差异内容：isNull(field: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：isNotNull(field: string): DataAbilityPredicates;<br>差异内容：isNotNull(field: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：like(field: string, value: string): DataAbilityPredicates;<br>差异内容：like(field: string, value: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：glob(field: string, value: string): DataAbilityPredicates;<br>差异内容：glob(field: string, value: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates;<br>差异内容：between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates;<br>差异内容：notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：greaterThan(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：greaterThan(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：lessThan(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：lessThan(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates;<br>差异内容：lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：orderByAsc(field: string): DataAbilityPredicates;<br>差异内容：orderByAsc(field: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：orderByDesc(field: string): DataAbilityPredicates;<br>差异内容：orderByDesc(field: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：distinct(): DataAbilityPredicates;<br>差异内容：distinct(): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：limitAs(value: number): DataAbilityPredicates;<br>差异内容：limitAs(value: number): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：offsetAs(rowOffset: number): DataAbilityPredicates;<br>差异内容：offsetAs(rowOffset: number): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：groupBy(fields: Array\<string>): DataAbilityPredicates;<br>差异内容：groupBy(fields: Array\<string>): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：indexedBy(field: string): DataAbilityPredicates;<br>差异内容：indexedBy(field: string): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：in(field: string, value: Array\<ValueType>): DataAbilityPredicates;<br>差异内容：in(field: string, value: Array\<ValueType>): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：DataAbilityPredicates；<br>API声明：notIn(field: string, value: Array\<ValueType>): DataAbilityPredicates;<br>差异内容：notIn(field: string, value: Array\<ValueType>): DataAbilityPredicates;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：dataAbility；<br>API声明：type ValueType = number \| string \| boolean;<br>差异内容：type ValueType = number \| string \| boolean;|api/@ohos.data.dataAbility.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dataSharePredicates<br>差异内容：declare namespace dataSharePredicates|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：dataSharePredicates；<br>API声明：class DataSharePredicates<br>差异内容：class DataSharePredicates|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：equalTo(field: string, value: ValueType): DataSharePredicates;<br>差异内容：equalTo(field: string, value: ValueType): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：and(): DataSharePredicates;<br>差异内容：and(): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：orderByAsc(field: string): DataSharePredicates;<br>差异内容：orderByAsc(field: string): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：orderByDesc(field: string): DataSharePredicates;<br>差异内容：orderByDesc(field: string): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：limit(total: number, offset: number): DataSharePredicates;<br>差异内容：limit(total: number, offset: number): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：DataSharePredicates；<br>API声明：in(field: string, value: Array\<ValueType>): DataSharePredicates;<br>差异内容：in(field: string, value: Array\<ValueType>): DataSharePredicates;|api/@ohos.data.dataSharePredicates.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace distributedData<br>差异内容：declare namespace distributedData|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface KVManagerConfig<br>差异内容：interface KVManagerConfig|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManagerConfig；<br>API声明：userInfo: UserInfo;<br>差异内容：userInfo: UserInfo;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManagerConfig；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface UserInfo<br>差异内容：interface UserInfo|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：UserInfo；<br>API声明：userId?: string;<br>差异内容：userId?: string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：UserInfo；<br>API声明：userType?: UserType;<br>差异内容：userType?: UserType;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum UserType<br>差异内容：enum UserType|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：UserType；<br>API声明：SAME_USER_ID = 0<br>差异内容：SAME_USER_ID = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：namespace Constants<br>差异内容：namespace Constants|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_KEY_LENGTH = 1024;<br>差异内容：const MAX_KEY_LENGTH = 1024;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_VALUE_LENGTH = 4194303;<br>差异内容：const MAX_VALUE_LENGTH = 4194303;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_KEY_LENGTH_DEVICE = 896;<br>差异内容：const MAX_KEY_LENGTH_DEVICE = 896;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_STORE_ID_LENGTH = 128;<br>差异内容：const MAX_STORE_ID_LENGTH = 128;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_QUERY_LENGTH = 512000;<br>差异内容：const MAX_QUERY_LENGTH = 512000;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Constants；<br>API声明：const MAX_BATCH_SIZE = 128;<br>差异内容：const MAX_BATCH_SIZE = 128;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum ValueType<br>差异内容：enum ValueType|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：STRING = 0<br>差异内容：STRING = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：INTEGER = 1<br>差异内容：INTEGER = 1|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：FLOAT = 2<br>差异内容：FLOAT = 2|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：BYTE_ARRAY = 3<br>差异内容：BYTE_ARRAY = 3|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：BOOLEAN = 4<br>差异内容：BOOLEAN = 4|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：DOUBLE = 5<br>差异内容：DOUBLE = 5|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface Value<br>差异内容：interface Value|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Value；<br>API声明：type: ValueType;<br>差异内容：type: ValueType;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Value；<br>API声明：value: Uint8Array \| string \| number \| boolean;<br>差异内容：value: Uint8Array \| string \| number \| boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface Entry<br>差异内容：interface Entry|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Entry；<br>API声明：key: string;<br>差异内容：key: string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Entry；<br>API声明：value: Value;<br>差异内容：value: Value;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface ChangeNotification<br>差异内容：interface ChangeNotification|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：insertEntries: Entry[];<br>差异内容：insertEntries: Entry[];|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：updateEntries: Entry[];<br>差异内容：updateEntries: Entry[];|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：deleteEntries: Entry[];<br>差异内容：deleteEntries: Entry[];|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum SyncMode<br>差异内容：enum SyncMode|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PULL_ONLY = 0<br>差异内容：PULL_ONLY = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PUSH_ONLY = 1<br>差异内容：PUSH_ONLY = 1|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PUSH_PULL = 2<br>差异内容：PUSH_PULL = 2|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum SubscribeType<br>差异内容：enum SubscribeType|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_LOCAL = 0<br>差异内容：SUBSCRIBE_TYPE_LOCAL = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_REMOTE = 1<br>差异内容：SUBSCRIBE_TYPE_REMOTE = 1|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_ALL = 2<br>差异内容：SUBSCRIBE_TYPE_ALL = 2|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum KVStoreType<br>差异内容：enum KVStoreType|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStoreType；<br>API声明：DEVICE_COLLABORATION = 0<br>差异内容：DEVICE_COLLABORATION = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStoreType；<br>API声明：SINGLE_VERSION = 1<br>差异内容：SINGLE_VERSION = 1|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStoreType；<br>API声明：MULTI_VERSION = 2<br>差异内容：MULTI_VERSION = 2|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：enum SecurityLevel<br>差异内容：enum SecurityLevel|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：NO_LEVEL = 0<br>差异内容：NO_LEVEL = 0|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S0 = 1<br>差异内容：S0 = 1|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S1 = 2<br>差异内容：S1 = 2|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S2 = 3<br>差异内容：S2 = 3|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S3 = 5<br>差异内容：S3 = 5|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S4 = 6<br>差异内容：S4 = 6|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：createIfMissing?: boolean;<br>差异内容：createIfMissing?: boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：encrypt?: boolean;<br>差异内容：encrypt?: boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：backup?: boolean;<br>差异内容：backup?: boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：autoSync?: boolean;<br>差异内容：autoSync?: boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：kvStoreType?: KVStoreType;<br>差异内容：kvStoreType?: KVStoreType;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：securityLevel?: SecurityLevel;<br>差异内容：securityLevel?: SecurityLevel;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Options；<br>API声明：schema?: Schema;<br>差异内容：schema?: Schema;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：class Schema<br>差异内容：class Schema|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Schema；<br>API声明：root: FieldNode;<br>差异内容：root: FieldNode;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Schema；<br>API声明：indexes: Array\<string>;<br>差异内容：indexes: Array\<string>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Schema；<br>API声明：mode: number;<br>差异内容：mode: number;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Schema；<br>API声明：skip: number;<br>差异内容：skip: number;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：class FieldNode<br>差异内容：class FieldNode|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：appendChild(child: FieldNode): boolean;<br>差异内容：appendChild(child: FieldNode): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：default: string;<br>差异内容：default: string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：nullable: boolean;<br>差异内容：nullable: boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：type: number;<br>差异内容：type: number;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface KvStoreResultSet<br>差异内容：interface KvStoreResultSet|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：getPosition(): number;<br>差异内容：getPosition(): number;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：moveToFirst(): boolean;<br>差异内容：moveToFirst(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：moveToLast(): boolean;<br>差异内容：moveToLast(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：moveToNext(): boolean;<br>差异内容：moveToNext(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：moveToPrevious(): boolean;<br>差异内容：moveToPrevious(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：move(offset: number): boolean;<br>差异内容：move(offset: number): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：moveToPosition(position: number): boolean;<br>差异内容：moveToPosition(position: number): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：isFirst(): boolean;<br>差异内容：isFirst(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：isLast(): boolean;<br>差异内容：isLast(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：isBeforeFirst(): boolean;<br>差异内容：isBeforeFirst(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KvStoreResultSet；<br>API声明：getEntry(): Entry;<br>差异内容：getEntry(): Entry;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：class Query<br>差异内容：class Query|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：reset(): Query;<br>差异内容：reset(): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：equalTo(field: string, value: number \| string \| boolean): Query;<br>差异内容：equalTo(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：notEqualTo(field: string, value: number \| string \| boolean): Query;<br>差异内容：notEqualTo(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：greaterThan(field: string, value: number \| string \| boolean): Query;<br>差异内容：greaterThan(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：lessThan(field: string, value: number \| string): Query;<br>差异内容：lessThan(field: string, value: number \| string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：greaterThanOrEqualTo(field: string, value: number \| string): Query;<br>差异内容：greaterThanOrEqualTo(field: string, value: number \| string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：lessThanOrEqualTo(field: string, value: number \| string): Query;<br>差异内容：lessThanOrEqualTo(field: string, value: number \| string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：isNull(field: string): Query;<br>差异内容：isNull(field: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：inNumber(field: string, valueList: number[]): Query;<br>差异内容：inNumber(field: string, valueList: number[]): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：inString(field: string, valueList: string[]): Query;<br>差异内容：inString(field: string, valueList: string[]): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：notInNumber(field: string, valueList: number[]): Query;<br>差异内容：notInNumber(field: string, valueList: number[]): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：notInString(field: string, valueList: string[]): Query;<br>差异内容：notInString(field: string, valueList: string[]): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：like(field: string, value: string): Query;<br>差异内容：like(field: string, value: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：unlike(field: string, value: string): Query;<br>差异内容：unlike(field: string, value: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：and(): Query;<br>差异内容：and(): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：or(): Query;<br>差异内容：or(): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：orderByAsc(field: string): Query;<br>差异内容：orderByAsc(field: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：orderByDesc(field: string): Query;<br>差异内容：orderByDesc(field: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：limit(total: number, offset: number): Query;<br>差异内容：limit(total: number, offset: number): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：isNotNull(field: string): Query;<br>差异内容：isNotNull(field: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：beginGroup(): Query;<br>差异内容：beginGroup(): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：endGroup(): Query;<br>差异内容：endGroup(): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：prefixKey(prefix: string): Query;<br>差异内容：prefixKey(prefix: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：setSuggestIndex(index: string): Query;<br>差异内容：setSuggestIndex(index: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：deviceId(deviceId: string): Query;<br>差异内容：deviceId(deviceId: string): Query;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：Query；<br>API声明：getSqlLike(): string;<br>差异内容：getSqlLike(): string;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface KVStore<br>差异内容：interface KVStore|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback\<void>): void;<br>差异内容：put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：put(key: string, value: Uint8Array \| string \| number \| boolean): Promise\<void>;<br>差异内容：put(key: string, value: Uint8Array \| string \| number \| boolean): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：delete(key: string, callback: AsyncCallback\<void>): void;<br>差异内容：delete(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：delete(key: string): Promise\<void>;<br>差异内容：delete(key: string): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：putBatch(entries: Entry[], callback: AsyncCallback\<void>): void;<br>差异内容：putBatch(entries: Entry[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：putBatch(entries: Entry[]): Promise\<void>;<br>差异内容：putBatch(entries: Entry[]): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：deleteBatch(keys: string[], callback: AsyncCallback\<void>): void;<br>差异内容：deleteBatch(keys: string[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：deleteBatch(keys: string[]): Promise\<void>;<br>差异内容：deleteBatch(keys: string[]): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：startTransaction(callback: AsyncCallback\<void>): void;<br>差异内容：startTransaction(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：startTransaction(): Promise\<void>;<br>差异内容：startTransaction(): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：commit(callback: AsyncCallback\<void>): void;<br>差异内容：commit(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：commit(): Promise\<void>;<br>差异内容：commit(): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：rollback(callback: AsyncCallback\<void>): void;<br>差异内容：rollback(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：rollback(): Promise\<void>;<br>差异内容：rollback(): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：enableSync(enabled: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：enableSync(enabled: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：enableSync(enabled: boolean): Promise\<void>;<br>差异内容：enableSync(enabled: boolean): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback\<void>): void;<br>差异内容：setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVStore；<br>API声明：setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise\<void>;<br>差异内容：setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface SingleKVStore<br>差异内容：interface SingleKVStore|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<Uint8Array \| string \| boolean \| number>): void;<br>差异内容：get(key: string, callback: AsyncCallback\<Uint8Array \| string \| boolean \| number>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：get(key: string): Promise\<Uint8Array \| string \| boolean \| number>;<br>差异内容：get(key: string): Promise\<Uint8Array \| string \| boolean \| number>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(keyPrefix: string): Promise\<Entry[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KvStoreResultSet>): void;<br>差异内容：getResultSet(keyPrefix: string, callback: AsyncCallback\<KvStoreResultSet>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string): Promise\<KvStoreResultSet>;<br>差异内容：getResultSet(keyPrefix: string): Promise\<KvStoreResultSet>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;<br>差异内容：getResultSet(query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(query: Query): Promise\<KvStoreResultSet>;<br>差异内容：getResultSet(query: Query): Promise\<KvStoreResultSet>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback\<void>): void;<br>差异内容：closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：closeResultSet(resultSet: KvStoreResultSet): Promise\<void>;<br>差异内容：closeResultSet(resultSet: KvStoreResultSet): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSize(query: Query): Promise\<number>;<br>差异内容：getResultSize(query: Query): Promise\<number>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：removeDeviceData(deviceId: string): Promise\<void>;<br>差异内容：removeDeviceData(deviceId: string): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;<br>差异内容：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback\<void>): void;<br>差异内容：setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncParam(defaultAllowedDelayMs: number): Promise\<void>;<br>差异内容：setSyncParam(defaultAllowedDelayMs: number): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getSecurityLevel(callback: AsyncCallback\<SecurityLevel>): void;<br>差异内容：getSecurityLevel(callback: AsyncCallback\<SecurityLevel>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getSecurityLevel(): Promise\<SecurityLevel>;<br>差异内容：getSecurityLevel(): Promise\<SecurityLevel>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface DeviceKVStore<br>差异内容：interface DeviceKVStore|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(deviceId: string, key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：get(deviceId: string, key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(deviceId: string, key: string): Promise\<boolean \| string \| number \| Uint8Array>;<br>差异内容：get(deviceId: string, key: string): Promise\<boolean \| string \| number \| Uint8Array>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(deviceId: string, keyPrefix: string): Promise\<Entry[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(deviceId: string, query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(deviceId: string, query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback\<KvStoreResultSet>): void;<br>差异内容：getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback\<KvStoreResultSet>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, keyPrefix: string): Promise\<KvStoreResultSet>;<br>差异内容：getResultSet(deviceId: string, keyPrefix: string): Promise\<KvStoreResultSet>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;<br>差异内容：getResultSet(query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(query: Query): Promise\<KvStoreResultSet>;<br>差异内容：getResultSet(query: Query): Promise\<KvStoreResultSet>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;<br>差异内容：getResultSet(deviceId: string, query: Query, callback: AsyncCallback\<KvStoreResultSet>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, query: Query): Promise\<KvStoreResultSet>;<br>差异内容：getResultSet(deviceId: string, query: Query): Promise\<KvStoreResultSet>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback\<void>): void;<br>差异内容：closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：closeResultSet(resultSet: KvStoreResultSet): Promise\<void>;<br>差异内容：closeResultSet(resultSet: KvStoreResultSet): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query): Promise\<number>;<br>差异内容：getResultSize(query: Query): Promise\<number>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query): Promise\<number>;<br>差异内容：getResultSize(deviceId: string, query: Query): Promise\<number>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：removeDeviceData(deviceId: string): Promise\<void>;<br>差异内容：removeDeviceData(deviceId: string): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;<br>差异内容：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：function createKVManager(config: KVManagerConfig, callback: AsyncCallback\<KVManager>): void;<br>差异内容：function createKVManager(config: KVManagerConfig, callback: AsyncCallback\<KVManager>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：function createKVManager(config: KVManagerConfig): Promise\<KVManager>;<br>差异内容：function createKVManager(config: KVManagerConfig): Promise\<KVManager>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：distributedData；<br>API声明：interface KVManager<br>差异内容：interface KVManager|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getKVStore\<T extends KVStore>(storeId: string, options: Options): Promise\<T>;<br>差异内容：getKVStore\<T extends KVStore>(storeId: string, options: Options): Promise\<T>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getKVStore\<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback\<T>): void;<br>差异内容：getKVStore\<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback\<T>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback\<void>): void;<br>差异内容：closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise\<void>;<br>差异内容：closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：deleteKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：deleteKVStore(appId: string, storeId: string): Promise\<void>;<br>差异内容：deleteKVStore(appId: string, storeId: string): Promise\<void>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getAllKVStoreId(appId: string, callback: AsyncCallback\<string[]>): void;<br>差异内容：getAllKVStoreId(appId: string, callback: AsyncCallback\<string[]>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getAllKVStoreId(appId: string): Promise\<string[]>;<br>差异内容：getAllKVStoreId(appId: string): Promise\<string[]>;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：on(event: 'distributedDataServiceDie', deathCallback: Callback\<void>): void;<br>差异内容：on(event: 'distributedDataServiceDie', deathCallback: Callback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：off(event: 'distributedDataServiceDie', deathCallback?: Callback\<void>): void;<br>差异内容：off(event: 'distributedDataServiceDie', deathCallback?: Callback\<void>): void;|api/@ohos.data.distributedData.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace distributedDataObject<br>差异内容：declare namespace distributedDataObject|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：interface BindInfo<br>差异内容：interface BindInfo|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：BindInfo；<br>API声明：storeName: string;<br>差异内容：storeName: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：BindInfo；<br>API声明：tableName: string;<br>差异内容：tableName: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：BindInfo；<br>API声明：primaryKey: commonType.ValuesBucket;<br>差异内容：primaryKey: commonType.ValuesBucket;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：BindInfo；<br>API声明：field: string;<br>差异内容：field: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：BindInfo；<br>API声明：assetName: string;<br>差异内容：assetName: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：function createDistributedObject(source: object): DistributedObject;<br>差异内容：function createDistributedObject(source: object): DistributedObject;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：function create(context: Context, source: object): DataObject;<br>差异内容：function create(context: Context, source: object): DataObject;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：function genSessionId(): string;<br>差异内容：function genSessionId(): string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：interface SaveSuccessResponse<br>差异内容：interface SaveSuccessResponse|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：SaveSuccessResponse；<br>API声明：sessionId: string;<br>差异内容：sessionId: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：SaveSuccessResponse；<br>API声明：version: number;<br>差异内容：version: number;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：SaveSuccessResponse；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：interface RevokeSaveSuccessResponse<br>差异内容：interface RevokeSaveSuccessResponse|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：RevokeSaveSuccessResponse；<br>API声明：sessionId: string;<br>差异内容：sessionId: string;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：interface DistributedObject<br>差异内容：interface DistributedObject|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DistributedObject；<br>API声明：setSessionId(sessionId?: string): boolean;<br>差异内容：setSessionId(sessionId?: string): boolean;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DistributedObject；<br>API声明：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DistributedObject；<br>API声明：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DistributedObject；<br>API声明：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DistributedObject；<br>API声明：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：interface DataObject<br>差异内容：interface DataObject|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：setSessionId(sessionId: string, callback: AsyncCallback\<void>): void;<br>差异内容：setSessionId(sessionId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：setSessionId(callback: AsyncCallback\<void>): void;<br>差异内容：setSessionId(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：setSessionId(sessionId?: string): Promise\<void>;<br>差异内容：setSessionId(sessionId?: string): Promise\<void>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：save(deviceId: string, callback: AsyncCallback\<SaveSuccessResponse>): void;<br>差异内容：save(deviceId: string, callback: AsyncCallback\<SaveSuccessResponse>): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：save(deviceId: string): Promise\<SaveSuccessResponse>;<br>差异内容：save(deviceId: string): Promise\<SaveSuccessResponse>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：revokeSave(callback: AsyncCallback\<RevokeSaveSuccessResponse>): void;<br>差异内容：revokeSave(callback: AsyncCallback\<RevokeSaveSuccessResponse>): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：revokeSave(): Promise\<RevokeSaveSuccessResponse>;<br>差异内容：revokeSave(): Promise\<RevokeSaveSuccessResponse>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：bindAssetStore(assetKey: string, bindInfo: BindInfo, callback: AsyncCallback\<void>): void;<br>差异内容：bindAssetStore(assetKey: string, bindInfo: BindInfo, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：bindAssetStore(assetKey: string, bindInfo: BindInfo): Promise\<void>;<br>差异内容：bindAssetStore(assetKey: string, bindInfo: BindInfo): Promise\<void>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace distributedKVStore<br>差异内容：declare namespace distributedKVStore|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface KVManagerConfig<br>差异内容：interface KVManagerConfig|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManagerConfig；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManagerConfig；<br>API声明：context: BaseContext;<br>差异内容：context: BaseContext;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface Constants<br>差异内容：interface Constants|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_KEY_LENGTH: number;<br>差异内容：readonly MAX_KEY_LENGTH: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_VALUE_LENGTH: number;<br>差异内容：readonly MAX_VALUE_LENGTH: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_KEY_LENGTH_DEVICE: number;<br>差异内容：readonly MAX_KEY_LENGTH_DEVICE: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_STORE_ID_LENGTH: number;<br>差异内容：readonly MAX_STORE_ID_LENGTH: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_QUERY_LENGTH: number;<br>差异内容：readonly MAX_QUERY_LENGTH: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Constants；<br>API声明：readonly MAX_BATCH_SIZE: number;<br>差异内容：readonly MAX_BATCH_SIZE: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：enum ValueType<br>差异内容：enum ValueType|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：STRING<br>差异内容：STRING|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：INTEGER<br>差异内容：INTEGER|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：FLOAT<br>差异内容：FLOAT|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：BYTE_ARRAY<br>差异内容：BYTE_ARRAY|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：BOOLEAN<br>差异内容：BOOLEAN|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ValueType；<br>API声明：DOUBLE<br>差异内容：DOUBLE|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface Value<br>差异内容：interface Value|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Value；<br>API声明：type: ValueType;<br>差异内容：type: ValueType;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Value；<br>API声明：value: Uint8Array \| string \| number \| boolean;<br>差异内容：value: Uint8Array \| string \| number \| boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface Entry<br>差异内容：interface Entry|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Entry；<br>API声明：key: string;<br>差异内容：key: string;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Entry；<br>API声明：value: Value;<br>差异内容：value: Value;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface ChangeNotification<br>差异内容：interface ChangeNotification|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：insertEntries: Entry[];<br>差异内容：insertEntries: Entry[];|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：updateEntries: Entry[];<br>差异内容：updateEntries: Entry[];|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：deleteEntries: Entry[];<br>差异内容：deleteEntries: Entry[];|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：ChangeNotification；<br>API声明：deviceId: string;<br>差异内容：deviceId: string;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：enum SyncMode<br>差异内容：enum SyncMode|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PULL_ONLY<br>差异内容：PULL_ONLY|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PUSH_ONLY<br>差异内容：PUSH_ONLY|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：PUSH_PULL<br>差异内容：PUSH_PULL|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：enum SubscribeType<br>差异内容：enum SubscribeType|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_LOCAL<br>差异内容：SUBSCRIBE_TYPE_LOCAL|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_REMOTE<br>差异内容：SUBSCRIBE_TYPE_REMOTE|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_ALL<br>差异内容：SUBSCRIBE_TYPE_ALL|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：enum KVStoreType<br>差异内容：enum KVStoreType|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreType；<br>API声明：DEVICE_COLLABORATION<br>差异内容：DEVICE_COLLABORATION|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreType；<br>API声明：SINGLE_VERSION<br>差异内容：SINGLE_VERSION|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：enum SecurityLevel<br>差异内容：enum SecurityLevel|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S1<br>差异内容：S1|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S2<br>差异内容：S2|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S3<br>差异内容：S3|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S4<br>差异内容：S4|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：createIfMissing?: boolean;<br>差异内容：createIfMissing?: boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：encrypt?: boolean;<br>差异内容：encrypt?: boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：backup?: boolean;<br>差异内容：backup?: boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：autoSync?: boolean;<br>差异内容：autoSync?: boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：kvStoreType?: KVStoreType;<br>差异内容：kvStoreType?: KVStoreType;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：securityLevel: SecurityLevel;<br>差异内容：securityLevel: SecurityLevel;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Options；<br>API声明：schema?: Schema;<br>差异内容：schema?: Schema;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：class Schema<br>差异内容：class Schema|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Schema；<br>API声明：root: FieldNode;<br>差异内容：root: FieldNode;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Schema；<br>API声明：indexes: Array\<string>;<br>差异内容：indexes: Array\<string>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Schema；<br>API声明：mode: number;<br>差异内容：mode: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Schema；<br>API声明：skip: number;<br>差异内容：skip: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：class FieldNode<br>差异内容：class FieldNode|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：appendChild(child: FieldNode): boolean;<br>差异内容：appendChild(child: FieldNode): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：default: string;<br>差异内容：default: string;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：nullable: boolean;<br>差异内容：nullable: boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：FieldNode；<br>API声明：type: number;<br>差异内容：type: number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface KVStoreResultSet<br>差异内容：interface KVStoreResultSet|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：getCount(): number;<br>差异内容：getCount(): number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：getPosition(): number;<br>差异内容：getPosition(): number;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：moveToFirst(): boolean;<br>差异内容：moveToFirst(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：moveToLast(): boolean;<br>差异内容：moveToLast(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：moveToNext(): boolean;<br>差异内容：moveToNext(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：moveToPrevious(): boolean;<br>差异内容：moveToPrevious(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：move(offset: number): boolean;<br>差异内容：move(offset: number): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：moveToPosition(position: number): boolean;<br>差异内容：moveToPosition(position: number): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：isFirst(): boolean;<br>差异内容：isFirst(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：isLast(): boolean;<br>差异内容：isLast(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：isBeforeFirst(): boolean;<br>差异内容：isBeforeFirst(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：isAfterLast(): boolean;<br>差异内容：isAfterLast(): boolean;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVStoreResultSet；<br>API声明：getEntry(): Entry;<br>差异内容：getEntry(): Entry;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：class Query<br>差异内容：class Query|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：reset(): Query;<br>差异内容：reset(): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：equalTo(field: string, value: number \| string \| boolean): Query;<br>差异内容：equalTo(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：notEqualTo(field: string, value: number \| string \| boolean): Query;<br>差异内容：notEqualTo(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：greaterThan(field: string, value: number \| string \| boolean): Query;<br>差异内容：greaterThan(field: string, value: number \| string \| boolean): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：lessThan(field: string, value: number \| string): Query;<br>差异内容：lessThan(field: string, value: number \| string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：greaterThanOrEqualTo(field: string, value: number \| string): Query;<br>差异内容：greaterThanOrEqualTo(field: string, value: number \| string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：lessThanOrEqualTo(field: string, value: number \| string): Query;<br>差异内容：lessThanOrEqualTo(field: string, value: number \| string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：isNull(field: string): Query;<br>差异内容：isNull(field: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：inNumber(field: string, valueList: number[]): Query;<br>差异内容：inNumber(field: string, valueList: number[]): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：inString(field: string, valueList: string[]): Query;<br>差异内容：inString(field: string, valueList: string[]): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：notInNumber(field: string, valueList: number[]): Query;<br>差异内容：notInNumber(field: string, valueList: number[]): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：notInString(field: string, valueList: string[]): Query;<br>差异内容：notInString(field: string, valueList: string[]): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：like(field: string, value: string): Query;<br>差异内容：like(field: string, value: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：unlike(field: string, value: string): Query;<br>差异内容：unlike(field: string, value: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：and(): Query;<br>差异内容：and(): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：or(): Query;<br>差异内容：or(): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：orderByAsc(field: string): Query;<br>差异内容：orderByAsc(field: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：orderByDesc(field: string): Query;<br>差异内容：orderByDesc(field: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：limit(total: number, offset: number): Query;<br>差异内容：limit(total: number, offset: number): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：isNotNull(field: string): Query;<br>差异内容：isNotNull(field: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：beginGroup(): Query;<br>差异内容：beginGroup(): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：endGroup(): Query;<br>差异内容：endGroup(): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：prefixKey(prefix: string): Query;<br>差异内容：prefixKey(prefix: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：setSuggestIndex(index: string): Query;<br>差异内容：setSuggestIndex(index: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：deviceId(deviceId: string): Query;<br>差异内容：deviceId(deviceId: string): Query;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：Query；<br>API声明：getSqlLike(): string;<br>差异内容：getSqlLike(): string;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface SingleKVStore<br>差异内容：interface SingleKVStore|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback\<void>): void;<br>差异内容：put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：put(key: string, value: Uint8Array \| string \| number \| boolean): Promise\<void>;<br>差异内容：put(key: string, value: Uint8Array \| string \| number \| boolean): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：putBatch(entries: Entry[], callback: AsyncCallback\<void>): void;<br>差异内容：putBatch(entries: Entry[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：putBatch(entries: Entry[]): Promise\<void>;<br>差异内容：putBatch(entries: Entry[]): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：delete(key: string, callback: AsyncCallback\<void>): void;<br>差异内容：delete(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：delete(key: string): Promise\<void>;<br>差异内容：delete(key: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：deleteBatch(keys: string[], callback: AsyncCallback\<void>): void;<br>差异内容：deleteBatch(keys: string[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：deleteBatch(keys: string[]): Promise\<void>;<br>差异内容：deleteBatch(keys: string[]): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;<br>差异内容：removeDeviceData(deviceId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：removeDeviceData(deviceId: string): Promise\<void>;<br>差异内容：removeDeviceData(deviceId: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;<br>差异内容：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(keyPrefix: string): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getEntries(query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSet(query: Query): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(query: Query): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback\<void>): void;<br>差异内容：closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：closeResultSet(resultSet: KVStoreResultSet): Promise\<void>;<br>差异内容：closeResultSet(resultSet: KVStoreResultSet): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getResultSize(query: Query): Promise\<number>;<br>差异内容：getResultSize(query: Query): Promise\<number>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：backup(file: string, callback: AsyncCallback\<void>): void;<br>差异内容：backup(file: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：backup(file: string): Promise\<void>;<br>差异内容：backup(file: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：restore(file: string, callback: AsyncCallback\<void>): void;<br>差异内容：restore(file: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：restore(file: string): Promise\<void>;<br>差异内容：restore(file: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：deleteBackup(files: Array\<string>, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：deleteBackup(files: Array\<string>, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：deleteBackup(files: Array\<string>): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;<br>差异内容：deleteBackup(files: Array\<string>): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：startTransaction(callback: AsyncCallback\<void>): void;<br>差异内容：startTransaction(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：startTransaction(): Promise\<void>;<br>差异内容：startTransaction(): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：commit(callback: AsyncCallback\<void>): void;<br>差异内容：commit(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：commit(): Promise\<void>;<br>差异内容：commit(): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：rollback(callback: AsyncCallback\<void>): void;<br>差异内容：rollback(callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：rollback(): Promise\<void>;<br>差异内容：rollback(): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：enableSync(enabled: boolean, callback: AsyncCallback\<void>): void;<br>差异内容：enableSync(enabled: boolean, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：enableSync(enabled: boolean): Promise\<void>;<br>差异内容：enableSync(enabled: boolean): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback\<void>): void;<br>差异内容：setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise\<void>;<br>差异内容：setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback\<void>): void;<br>差异内容：setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：setSyncParam(defaultAllowedDelayMs: number): Promise\<void>;<br>差异内容：setSyncParam(defaultAllowedDelayMs: number): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;<br>差异内容：sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: number): void;<br>差异内容：sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: number): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getSecurityLevel(callback: AsyncCallback\<SecurityLevel>): void;<br>差异内容：getSecurityLevel(callback: AsyncCallback\<SecurityLevel>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：SingleKVStore；<br>API声明：getSecurityLevel(): Promise\<SecurityLevel>;<br>差异内容：getSecurityLevel(): Promise\<SecurityLevel>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface DeviceKVStore<br>差异内容：interface DeviceKVStore|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;<br>差异内容：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(deviceId: string, key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：get(deviceId: string, key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：get(deviceId: string, key: string): Promise\<boolean \| string \| number \| Uint8Array>;<br>差异内容：get(deviceId: string, key: string): Promise\<boolean \| string \| number \| Uint8Array>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(keyPrefix: string): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(deviceId: string, keyPrefix: string): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(deviceId: string, query: Query, callback: AsyncCallback\<Entry[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getEntries(deviceId: string, query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(deviceId: string, query: Query): Promise\<Entry[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, keyPrefix: string): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(deviceId: string, keyPrefix: string): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(query: Query): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(query: Query): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(deviceId: string, query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSet(deviceId: string, query: Query): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(deviceId: string, query: Query): Promise\<KVStoreResultSet>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query): Promise\<number>;<br>差异内容：getResultSize(query: Query): Promise\<number>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query): Promise\<number>;<br>差异内容：getResultSize(deviceId: string, query: Query): Promise\<number>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：function createKVManager(config: KVManagerConfig): KVManager;<br>差异内容：function createKVManager(config: KVManagerConfig): KVManager;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：distributedKVStore；<br>API声明：interface KVManager<br>差异内容：interface KVManager|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getKVStore\<T>(storeId: string, options: Options, callback: AsyncCallback\<T>): void;<br>差异内容：getKVStore\<T>(storeId: string, options: Options, callback: AsyncCallback\<T>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getKVStore\<T>(storeId: string, options: Options): Promise\<T>;<br>差异内容：getKVStore\<T>(storeId: string, options: Options): Promise\<T>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：closeKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;<br>差异内容：closeKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：closeKVStore(appId: string, storeId: string): Promise\<void>;<br>差异内容：closeKVStore(appId: string, storeId: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：deleteKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;<br>差异内容：deleteKVStore(appId: string, storeId: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：deleteKVStore(appId: string, storeId: string): Promise\<void>;<br>差异内容：deleteKVStore(appId: string, storeId: string): Promise\<void>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getAllKVStoreId(appId: string, callback: AsyncCallback\<string[]>): void;<br>差异内容：getAllKVStoreId(appId: string, callback: AsyncCallback\<string[]>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：getAllKVStoreId(appId: string): Promise\<string[]>;<br>差异内容：getAllKVStoreId(appId: string): Promise\<string[]>;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：on(event: 'distributedDataServiceDie', deathCallback: Callback\<void>): void;<br>差异内容：on(event: 'distributedDataServiceDie', deathCallback: Callback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：KVManager；<br>API声明：off(event: 'distributedDataServiceDie', deathCallback?: Callback\<void>): void;<br>差异内容：off(event: 'distributedDataServiceDie', deathCallback?: Callback\<void>): void;|api/@ohos.data.distributedKVStore.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace preferences<br>差异内容：declare namespace preferences|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：type ValueType = number \| string \| boolean \| Array\<number> \| Array\<string> \| Array\<boolean> \| Uint8Array;<br>差异内容：type ValueType = number \| string \| boolean \| Array\<number> \| Array\<string> \| Array\<boolean> \| Uint8Array;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：const MAX_KEY_LENGTH: 80;<br>差异内容：const MAX_KEY_LENGTH: 80;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：const MAX_VALUE_LENGTH: 8192;<br>差异内容：const MAX_VALUE_LENGTH: 8192;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Options；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Options；<br>API声明：dataGroupId?: string \| null \| undefined;<br>差异内容：dataGroupId?: string \| null \| undefined;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function getPreferences(context: Context, name: string, callback: AsyncCallback\<Preferences>): void;<br>差异内容：function getPreferences(context: Context, name: string, callback: AsyncCallback\<Preferences>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function getPreferences(context: Context, options: Options, callback: AsyncCallback\<Preferences>): void;<br>差异内容：function getPreferences(context: Context, options: Options, callback: AsyncCallback\<Preferences>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function getPreferences(context: Context, name: string): Promise\<Preferences>;<br>差异内容：function getPreferences(context: Context, name: string): Promise\<Preferences>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function getPreferences(context: Context, options: Options): Promise\<Preferences>;<br>差异内容：function getPreferences(context: Context, options: Options): Promise\<Preferences>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function getPreferencesSync(context: Context, options: Options): Preferences;<br>差异内容：function getPreferencesSync(context: Context, options: Options): Preferences;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function deletePreferences(context: Context, name: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deletePreferences(context: Context, name: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function deletePreferences(context: Context, options: Options, callback: AsyncCallback\<void>): void;<br>差异内容：function deletePreferences(context: Context, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function deletePreferences(context: Context, name: string): Promise\<void>;<br>差异内容：function deletePreferences(context: Context, name: string): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function deletePreferences(context: Context, options: Options): Promise\<void>;<br>差异内容：function deletePreferences(context: Context, options: Options): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCache(context: Context, name: string, callback: AsyncCallback\<void>): void;<br>差异内容：function removePreferencesFromCache(context: Context, name: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCache(context: Context, options: Options, callback: AsyncCallback\<void>): void;<br>差异内容：function removePreferencesFromCache(context: Context, options: Options, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCache(context: Context, name: string): Promise\<void>;<br>差异内容：function removePreferencesFromCache(context: Context, name: string): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCache(context: Context, options: Options): Promise\<void>;<br>差异内容：function removePreferencesFromCache(context: Context, options: Options): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCacheSync(context: Context, name: string): void;<br>差异内容：function removePreferencesFromCacheSync(context: Context, name: string): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function removePreferencesFromCacheSync(context: Context, options: Options): void;<br>差异内容：function removePreferencesFromCacheSync(context: Context, options: Options): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：interface Preferences<br>差异内容：interface Preferences|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：get(key: string, defValue: ValueType, callback: AsyncCallback\<ValueType>): void;<br>差异内容：get(key: string, defValue: ValueType, callback: AsyncCallback\<ValueType>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：get(key: string, defValue: ValueType): Promise\<ValueType>;<br>差异内容：get(key: string, defValue: ValueType): Promise\<ValueType>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：getSync(key: string, defValue: ValueType): ValueType;<br>差异内容：getSync(key: string, defValue: ValueType): ValueType;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：getAll(callback: AsyncCallback\<Object>): void;<br>差异内容：getAll(callback: AsyncCallback\<Object>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：getAll(): Promise\<Object>;<br>差异内容：getAll(): Promise\<Object>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：getAllSync(): Object;<br>差异内容：getAllSync(): Object;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：has(key: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：has(key: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：has(key: string): Promise\<boolean>;<br>差异内容：has(key: string): Promise\<boolean>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：hasSync(key: string): boolean;<br>差异内容：hasSync(key: string): boolean;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：put(key: string, value: ValueType, callback: AsyncCallback\<void>): void;<br>差异内容：put(key: string, value: ValueType, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：put(key: string, value: ValueType): Promise\<void>;<br>差异内容：put(key: string, value: ValueType): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：putSync(key: string, value: ValueType): void;<br>差异内容：putSync(key: string, value: ValueType): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：delete(key: string, callback: AsyncCallback\<void>): void;<br>差异内容：delete(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：delete(key: string): Promise\<void>;<br>差异内容：delete(key: string): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：deleteSync(key: string): void;<br>差异内容：deleteSync(key: string): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：clear(callback: AsyncCallback\<void>): void;<br>差异内容：clear(callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：clear(): Promise\<void>;<br>差异内容：clear(): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：clearSync(): void;<br>差异内容：clearSync(): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：flush(callback: AsyncCallback\<void>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：flush(): Promise\<void>;<br>差异内容：flush(): Promise\<void>;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：on(type: 'change', callback: Callback\<string>): void;<br>差异内容：on(type: 'change', callback: Callback\<string>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：on(type: 'multiProcessChange', callback: Callback\<string>): void;<br>差异内容：on(type: 'multiProcessChange', callback: Callback\<string>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：off(type: 'change', callback?: Callback\<string>): void;<br>差异内容：off(type: 'change', callback?: Callback\<string>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Preferences；<br>API声明：off(type: 'multiProcessChange', callback?: Callback\<string>): void;<br>差异内容：off(type: 'multiProcessChange', callback?: Callback\<string>): void;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace rdb<br>差异内容：declare namespace rdb|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback\<RdbStore>): void;<br>差异内容：function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback\<RdbStore>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：function getRdbStore(context: Context, config: StoreConfig, version: number): Promise\<RdbStore>;<br>差异内容：function getRdbStore(context: Context, config: StoreConfig, version: number): Promise\<RdbStore>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：function deleteRdbStore(context: Context, name: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteRdbStore(context: Context, name: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：function deleteRdbStore(context: Context, name: string): Promise\<void>;<br>差异内容：function deleteRdbStore(context: Context, name: string): Promise\<void>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：enum SyncMode<br>差异内容：enum SyncMode|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_PUSH = 0<br>差异内容：SYNC_MODE_PUSH = 0|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_PULL = 1<br>差异内容：SYNC_MODE_PULL = 1|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：enum SubscribeType<br>差异内容：enum SubscribeType|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_REMOTE = 0<br>差异内容：SUBSCRIBE_TYPE_REMOTE = 0|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：interface RdbStore<br>差异内容：interface RdbStore|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket, callback: AsyncCallback\<number>): void;<br>差异内容：insert(table: string, values: ValuesBucket, callback: AsyncCallback\<number>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket): Promise\<number>;<br>差异内容：insert(table: string, values: ValuesBucket): Promise\<number>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsert(table: string, values: Array\<ValuesBucket>, callback: AsyncCallback\<number>): void;<br>差异内容：batchInsert(table: string, values: Array\<ValuesBucket>, callback: AsyncCallback\<number>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsert(table: string, values: Array\<ValuesBucket>): Promise\<number>;<br>差异内容：batchInsert(table: string, values: Array\<ValuesBucket>): Promise\<number>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback\<number>): void;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback\<number>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates): Promise\<number>;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates): Promise\<number>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：delete(predicates: RdbPredicates, callback: AsyncCallback\<number>): void;<br>差异内容：delete(predicates: RdbPredicates, callback: AsyncCallback\<number>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：delete(predicates: RdbPredicates): Promise\<number>;<br>差异内容：delete(predicates: RdbPredicates): Promise\<number>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：query(predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：query(predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：query(predicates: RdbPredicates, columns?: Array\<string>): Promise\<ResultSet>;<br>差异内容：query(predicates: RdbPredicates, columns?: Array\<string>): Promise\<ResultSet>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：querySql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：querySql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：querySql(sql: string, bindArgs?: Array\<ValueType>): Promise\<ResultSet>;<br>差异内容：querySql(sql: string, bindArgs?: Array\<ValueType>): Promise\<ResultSet>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：executeSql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<void>): void;<br>差异内容：executeSql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<void>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：executeSql(sql: string, bindArgs?: Array\<ValueType>): Promise\<void>;<br>差异内容：executeSql(sql: string, bindArgs?: Array\<ValueType>): Promise\<void>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：beginTransaction(): void;<br>差异内容：beginTransaction(): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：commit(): void;<br>差异内容：commit(): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：rollBack(): void;<br>差异内容：rollBack(): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：setDistributedTables(tables: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>): Promise\<void>;<br>差异内容：setDistributedTables(tables: Array\<string>): Promise\<void>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：obtainDistributedTableName(device: string, table: string, callback: AsyncCallback\<string>): void;<br>差异内容：obtainDistributedTableName(device: string, table: string, callback: AsyncCallback\<string>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：obtainDistributedTableName(device: string, table: string): Promise\<string>;<br>差异内容：obtainDistributedTableName(device: string, table: string): Promise\<string>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：sync(mode: SyncMode, predicates: RdbPredicates): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;<br>差异内容：sync(mode: SyncMode, predicates: RdbPredicates): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;<br>差异内容：off(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：type ValueType = number \| string \| boolean;<br>差异内容：type ValueType = number \| string \| boolean;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：type ValuesBucket = {<br>        [key: string]: ValueType \| Uint8Array \| null;<br>    };<br>差异内容：type ValuesBucket = {<br>        [key: string]: ValueType \| Uint8Array \| null;<br>    };|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：interface StoreConfig<br>差异内容：interface StoreConfig|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：class RdbPredicates<br>差异内容：class RdbPredicates|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：inDevices(devices: Array\<string>): RdbPredicates;<br>差异内容：inDevices(devices: Array\<string>): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：inAllDevices(): RdbPredicates;<br>差异内容：inAllDevices(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：equalTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：equalTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：notEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：beginWrap(): RdbPredicates;<br>差异内容：beginWrap(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：endWrap(): RdbPredicates;<br>差异内容：endWrap(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：or(): RdbPredicates;<br>差异内容：or(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：and(): RdbPredicates;<br>差异内容：and(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：contains(field: string, value: string): RdbPredicates;<br>差异内容：contains(field: string, value: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：beginsWith(field: string, value: string): RdbPredicates;<br>差异内容：beginsWith(field: string, value: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：endsWith(field: string, value: string): RdbPredicates;<br>差异内容：endsWith(field: string, value: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：isNull(field: string): RdbPredicates;<br>差异内容：isNull(field: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：isNotNull(field: string): RdbPredicates;<br>差异内容：isNotNull(field: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：like(field: string, value: string): RdbPredicates;<br>差异内容：like(field: string, value: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：glob(field: string, value: string): RdbPredicates;<br>差异内容：glob(field: string, value: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：between(field: string, low: ValueType, high: ValueType): RdbPredicates;<br>差异内容：between(field: string, low: ValueType, high: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates;<br>差异内容：notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：greaterThan(field: string, value: ValueType): RdbPredicates;<br>差异内容：greaterThan(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：lessThan(field: string, value: ValueType): RdbPredicates;<br>差异内容：lessThan(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：orderByAsc(field: string): RdbPredicates;<br>差异内容：orderByAsc(field: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：orderByDesc(field: string): RdbPredicates;<br>差异内容：orderByDesc(field: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：distinct(): RdbPredicates;<br>差异内容：distinct(): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：limitAs(value: number): RdbPredicates;<br>差异内容：limitAs(value: number): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：offsetAs(rowOffset: number): RdbPredicates;<br>差异内容：offsetAs(rowOffset: number): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：groupBy(fields: Array\<string>): RdbPredicates;<br>差异内容：groupBy(fields: Array\<string>): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：indexedBy(field: string): RdbPredicates;<br>差异内容：indexedBy(field: string): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：in(field: string, value: Array\<ValueType>): RdbPredicates;<br>差异内容：in(field: string, value: Array\<ValueType>): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notIn(field: string, value: Array\<ValueType>): RdbPredicates;<br>差异内容：notIn(field: string, value: Array\<ValueType>): RdbPredicates;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：rdb；<br>API声明：export type ResultSet = _ResultSet;<br>差异内容：export type ResultSet = _ResultSet;|api/@ohos.data.rdb.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace relationalStore<br>差异内容：declare namespace relationalStore|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum AssetStatus<br>差异内容：enum AssetStatus|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_NORMAL<br>差异内容：ASSET_NORMAL|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_INSERT<br>差异内容：ASSET_INSERT|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_UPDATE<br>差异内容：ASSET_UPDATE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_DELETE<br>差异内容：ASSET_DELETE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_ABNORMAL<br>差异内容：ASSET_ABNORMAL|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：AssetStatus；<br>API声明：ASSET_DOWNLOADING<br>差异内容：ASSET_DOWNLOADING|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface Asset<br>差异内容：interface Asset|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：path: string;<br>差异内容：path: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：createTime: string;<br>差异内容：createTime: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：modifyTime: string;<br>差异内容：modifyTime: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：size: string;<br>差异内容：size: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Asset；<br>API声明：status?: AssetStatus;<br>差异内容：status?: AssetStatus;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type Assets = Asset[];<br>差异内容：type Assets = Asset[];|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type ValueType = null \| number \| string \| boolean \| Uint8Array \| Asset \| Assets;<br>差异内容：type ValueType = null \| number \| string \| boolean \| Uint8Array \| Asset \| Assets;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type ValuesBucket = Record\<string, ValueType>;<br>差异内容：type ValuesBucket = Record\<string, ValueType>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type PRIKeyType = number \| string;<br>差异内容：type PRIKeyType = number \| string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type UTCTime = Date;<br>差异内容：type UTCTime = Date;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：type ModifyTime = Map\<PRIKeyType, UTCTime>;<br>差异内容：type ModifyTime = Map\<PRIKeyType, UTCTime>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface StoreConfig<br>差异内容：interface StoreConfig|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：name: string;<br>差异内容：name: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：securityLevel: SecurityLevel;<br>差异内容：securityLevel: SecurityLevel;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：encrypt?: boolean;<br>差异内容：encrypt?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：dataGroupId?: string;<br>差异内容：dataGroupId?: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：customDir?: string;<br>差异内容：customDir?: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：autoCleanDirtyData?: boolean;<br>差异内容：autoCleanDirtyData?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum Progress<br>差异内容：enum Progress|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Progress；<br>API声明：SYNC_BEGIN<br>差异内容：SYNC_BEGIN|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Progress；<br>API声明：SYNC_IN_PROGRESS<br>差异内容：SYNC_IN_PROGRESS|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Progress；<br>API声明：SYNC_FINISH<br>差异内容：SYNC_FINISH|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface Statistic<br>差异内容：interface Statistic|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Statistic；<br>API声明：total: number;<br>差异内容：total: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Statistic；<br>API声明：successful: number;<br>差异内容：successful: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Statistic；<br>API声明：failed: number;<br>差异内容：failed: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Statistic；<br>API声明：remained: number;<br>差异内容：remained: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface TableDetails<br>差异内容：interface TableDetails|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：TableDetails；<br>API声明：upload: Statistic;<br>差异内容：upload: Statistic;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：TableDetails；<br>API声明：download: Statistic;<br>差异内容：download: Statistic;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum ProgressCode<br>差异内容：enum ProgressCode|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：SUCCESS<br>差异内容：SUCCESS|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：UNKNOWN_ERROR<br>差异内容：UNKNOWN_ERROR|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：NETWORK_ERROR<br>差异内容：NETWORK_ERROR|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：CLOUD_DISABLED<br>差异内容：CLOUD_DISABLED|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：LOCKED_BY_OTHERS<br>差异内容：LOCKED_BY_OTHERS|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：RECORD_LIMIT_EXCEEDED<br>差异内容：RECORD_LIMIT_EXCEEDED|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressCode；<br>API声明：NO_SPACE_FOR_ASSET<br>差异内容：NO_SPACE_FOR_ASSET|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface ProgressDetails<br>差异内容：interface ProgressDetails|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressDetails；<br>API声明：schedule: Progress;<br>差异内容：schedule: Progress;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressDetails；<br>API声明：code: ProgressCode;<br>差异内容：code: ProgressCode;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ProgressDetails；<br>API声明：details: Record\<string, TableDetails>;<br>差异内容：details: Record\<string, TableDetails>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum SecurityLevel<br>差异内容：enum SecurityLevel|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S1 = 1<br>差异内容：S1 = 1|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S2 = 2<br>差异内容：S2 = 2|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S3 = 3<br>差异内容：S3 = 3|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SecurityLevel；<br>API声明：S4 = 4<br>差异内容：S4 = 4|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum SyncMode<br>差异内容：enum SyncMode|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_PUSH = 0<br>差异内容：SYNC_MODE_PUSH = 0|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_PULL = 1<br>差异内容：SYNC_MODE_PULL = 1|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_TIME_FIRST<br>差异内容：SYNC_MODE_TIME_FIRST|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_NATIVE_FIRST<br>差异内容：SYNC_MODE_NATIVE_FIRST|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SyncMode；<br>API声明：SYNC_MODE_CLOUD_FIRST<br>差异内容：SYNC_MODE_CLOUD_FIRST|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum SubscribeType<br>差异内容：enum SubscribeType|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_REMOTE = 0<br>差异内容：SUBSCRIBE_TYPE_REMOTE = 0|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_CLOUD<br>差异内容：SUBSCRIBE_TYPE_CLOUD|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SubscribeType；<br>API声明：SUBSCRIBE_TYPE_CLOUD_DETAILS<br>差异内容：SUBSCRIBE_TYPE_CLOUD_DETAILS|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum ChangeType<br>差异内容：enum ChangeType|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeType；<br>API声明：DATA_CHANGE<br>差异内容：DATA_CHANGE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeType；<br>API声明：ASSET_CHANGE<br>差异内容：ASSET_CHANGE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface ChangeInfo<br>差异内容：interface ChangeInfo|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeInfo；<br>API声明：table: string;<br>差异内容：table: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeInfo；<br>API声明：type: ChangeType;<br>差异内容：type: ChangeType;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeInfo；<br>API声明：inserted: Array\<string> \| Array\<number>;<br>差异内容：inserted: Array\<string> \| Array\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeInfo；<br>API声明：updated: Array\<string> \| Array\<number>;<br>差异内容：updated: Array\<string> \| Array\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ChangeInfo；<br>API声明：deleted: Array\<string> \| Array\<number>;<br>差异内容：deleted: Array\<string> \| Array\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum DistributedType<br>差异内容：enum DistributedType|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：DistributedType；<br>API声明：DISTRIBUTED_DEVICE<br>差异内容：DISTRIBUTED_DEVICE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：DistributedType；<br>API声明：DISTRIBUTED_CLOUD<br>差异内容：DISTRIBUTED_CLOUD|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface DistributedConfig<br>差异内容：interface DistributedConfig|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：DistributedConfig；<br>API声明：autoSync: boolean;<br>差异内容：autoSync: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum ConflictResolution<br>差异内容：enum ConflictResolution|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_NONE = 0<br>差异内容：ON_CONFLICT_NONE = 0|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_ROLLBACK = 1<br>差异内容：ON_CONFLICT_ROLLBACK = 1|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_ABORT = 2<br>差异内容：ON_CONFLICT_ABORT = 2|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_FAIL = 3<br>差异内容：ON_CONFLICT_FAIL = 3|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_IGNORE = 4<br>差异内容：ON_CONFLICT_IGNORE = 4|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ConflictResolution；<br>API声明：ON_CONFLICT_REPLACE = 5<br>差异内容：ON_CONFLICT_REPLACE = 5|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum Origin<br>差异内容：enum Origin|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Origin；<br>API声明：LOCAL<br>差异内容：LOCAL|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Origin；<br>API声明：CLOUD<br>差异内容：CLOUD|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Origin；<br>API声明：REMOTE<br>差异内容：REMOTE|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum Field<br>差异内容：enum Field|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：CURSOR_FIELD = '#_cursor'<br>差异内容：CURSOR_FIELD = '#_cursor'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：ORIGIN_FIELD = '#_origin'<br>差异内容：ORIGIN_FIELD = '#_origin'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：DELETED_FLAG_FIELD = '#_deleted_flag'<br>差异内容：DELETED_FLAG_FIELD = '#_deleted_flag'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：OWNER_FIELD = '#_cloud_owner'<br>差异内容：OWNER_FIELD = '#_cloud_owner'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：PRIVILEGE_FIELD = '#_cloud_privilege'<br>差异内容：PRIVILEGE_FIELD = '#_cloud_privilege'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Field；<br>API声明：SHARING_RESOURCE_FIELD = '#_sharing_resource_field'<br>差异内容：SHARING_RESOURCE_FIELD = '#_sharing_resource_field'|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：class RdbPredicates<br>差异内容：class RdbPredicates|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：inDevices(devices: Array\<string>): RdbPredicates;<br>差异内容：inDevices(devices: Array\<string>): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：inAllDevices(): RdbPredicates;<br>差异内容：inAllDevices(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：equalTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：equalTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：notEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：beginWrap(): RdbPredicates;<br>差异内容：beginWrap(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：endWrap(): RdbPredicates;<br>差异内容：endWrap(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：or(): RdbPredicates;<br>差异内容：or(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：and(): RdbPredicates;<br>差异内容：and(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：contains(field: string, value: string): RdbPredicates;<br>差异内容：contains(field: string, value: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：beginsWith(field: string, value: string): RdbPredicates;<br>差异内容：beginsWith(field: string, value: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：endsWith(field: string, value: string): RdbPredicates;<br>差异内容：endsWith(field: string, value: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：isNull(field: string): RdbPredicates;<br>差异内容：isNull(field: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：isNotNull(field: string): RdbPredicates;<br>差异内容：isNotNull(field: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：like(field: string, value: string): RdbPredicates;<br>差异内容：like(field: string, value: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：glob(field: string, value: string): RdbPredicates;<br>差异内容：glob(field: string, value: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：between(field: string, low: ValueType, high: ValueType): RdbPredicates;<br>差异内容：between(field: string, low: ValueType, high: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates;<br>差异内容：notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：greaterThan(field: string, value: ValueType): RdbPredicates;<br>差异内容：greaterThan(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：lessThan(field: string, value: ValueType): RdbPredicates;<br>差异内容：lessThan(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates;<br>差异内容：lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：orderByAsc(field: string): RdbPredicates;<br>差异内容：orderByAsc(field: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：orderByDesc(field: string): RdbPredicates;<br>差异内容：orderByDesc(field: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：distinct(): RdbPredicates;<br>差异内容：distinct(): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：limitAs(value: number): RdbPredicates;<br>差异内容：limitAs(value: number): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：offsetAs(rowOffset: number): RdbPredicates;<br>差异内容：offsetAs(rowOffset: number): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：groupBy(fields: Array\<string>): RdbPredicates;<br>差异内容：groupBy(fields: Array\<string>): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：indexedBy(field: string): RdbPredicates;<br>差异内容：indexedBy(field: string): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：in(field: string, value: Array\<ValueType>): RdbPredicates;<br>差异内容：in(field: string, value: Array\<ValueType>): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：notIn(field: string, value: Array\<ValueType>): RdbPredicates;<br>差异内容：notIn(field: string, value: Array\<ValueType>): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface ResultSet<br>差异内容：interface ResultSet|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：columnNames: Array\<string>;<br>差异内容：columnNames: Array\<string>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：columnCount: number;<br>差异内容：columnCount: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：rowCount: number;<br>差异内容：rowCount: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：rowIndex: number;<br>差异内容：rowIndex: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isAtFirstRow: boolean;<br>差异内容：isAtFirstRow: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isAtLastRow: boolean;<br>差异内容：isAtLastRow: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isEnded: boolean;<br>差异内容：isEnded: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isStarted: boolean;<br>差异内容：isStarted: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isClosed: boolean;<br>差异内容：isClosed: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getColumnIndex(columnName: string): number;<br>差异内容：getColumnIndex(columnName: string): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getColumnName(columnIndex: number): string;<br>差异内容：getColumnName(columnIndex: number): string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goTo(offset: number): boolean;<br>差异内容：goTo(offset: number): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goToRow(position: number): boolean;<br>差异内容：goToRow(position: number): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goToFirstRow(): boolean;<br>差异内容：goToFirstRow(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goToLastRow(): boolean;<br>差异内容：goToLastRow(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goToNextRow(): boolean;<br>差异内容：goToNextRow(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：goToPreviousRow(): boolean;<br>差异内容：goToPreviousRow(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getBlob(columnIndex: number): Uint8Array;<br>差异内容：getBlob(columnIndex: number): Uint8Array;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getString(columnIndex: number): string;<br>差异内容：getString(columnIndex: number): string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getLong(columnIndex: number): number;<br>差异内容：getLong(columnIndex: number): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getDouble(columnIndex: number): number;<br>差异内容：getDouble(columnIndex: number): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getAsset(columnIndex: number): Asset;<br>差异内容：getAsset(columnIndex: number): Asset;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getAssets(columnIndex: number): Assets;<br>差异内容：getAssets(columnIndex: number): Assets;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getRow(): ValuesBucket;<br>差异内容：getRow(): ValuesBucket;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：isColumnNull(columnIndex: number): boolean;<br>差异内容：isColumnNull(columnIndex: number): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：close(): void;<br>差异内容：close(): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface RdbStore<br>差异内容：interface RdbStore|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：version: number;<br>差异内容：version: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket, callback: AsyncCallback\<number>): void;<br>差异内容：insert(table: string, values: ValuesBucket, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket, conflict: ConflictResolution, callback: AsyncCallback\<number>): void;<br>差异内容：insert(table: string, values: ValuesBucket, conflict: ConflictResolution, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket): Promise\<number>;<br>差异内容：insert(table: string, values: ValuesBucket): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：insert(table: string, values: ValuesBucket, conflict: ConflictResolution): Promise\<number>;<br>差异内容：insert(table: string, values: ValuesBucket, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsert(table: string, values: Array\<ValuesBucket>, callback: AsyncCallback\<number>): void;<br>差异内容：batchInsert(table: string, values: Array\<ValuesBucket>, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsert(table: string, values: Array\<ValuesBucket>): Promise\<number>;<br>差异内容：batchInsert(table: string, values: Array\<ValuesBucket>): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback\<number>): void;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution, callback: AsyncCallback\<number>): void;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates): Promise\<number>;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution): Promise\<number>;<br>差异内容：update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：delete(predicates: RdbPredicates, callback: AsyncCallback\<number>): void;<br>差异内容：delete(predicates: RdbPredicates, callback: AsyncCallback\<number>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：delete(predicates: RdbPredicates): Promise\<number>;<br>差异内容：delete(predicates: RdbPredicates): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：query(predicates: RdbPredicates, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：query(predicates: RdbPredicates, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：query(predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：query(predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：query(predicates: RdbPredicates, columns?: Array\<string>): Promise\<ResultSet>;<br>差异内容：query(predicates: RdbPredicates, columns?: Array\<string>): Promise\<ResultSet>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：querySql(sql: string, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：querySql(sql: string, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：querySql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：querySql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：querySql(sql: string, bindArgs?: Array\<ValueType>): Promise\<ResultSet>;<br>差异内容：querySql(sql: string, bindArgs?: Array\<ValueType>): Promise\<ResultSet>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[]): Promise\<ModifyTime>;<br>差异内容：getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[]): Promise\<ModifyTime>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[], callback: AsyncCallback\<ModifyTime>): void;<br>差异内容：getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[], callback: AsyncCallback\<ModifyTime>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cleanDirtyData(table: string, cursor: number, callback: AsyncCallback\<void>): void;<br>差异内容：cleanDirtyData(table: string, cursor: number, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cleanDirtyData(table: string, callback: AsyncCallback\<void>): void;<br>差异内容：cleanDirtyData(table: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cleanDirtyData(table: string, cursor?: number): Promise\<void>;<br>差异内容：cleanDirtyData(table: string, cursor?: number): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：executeSql(sql: string, callback: AsyncCallback\<void>): void;<br>差异内容：executeSql(sql: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：executeSql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<void>): void;<br>差异内容：executeSql(sql: string, bindArgs: Array\<ValueType>, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：executeSql(sql: string, bindArgs?: Array\<ValueType>): Promise\<void>;<br>差异内容：executeSql(sql: string, bindArgs?: Array\<ValueType>): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：beginTransaction(): void;<br>差异内容：beginTransaction(): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：commit(): void;<br>差异内容：commit(): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：rollBack(): void;<br>差异内容：rollBack(): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：backup(destName: string, callback: AsyncCallback\<void>): void;<br>差异内容：backup(destName: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：backup(destName: string): Promise\<void>;<br>差异内容：backup(destName: string): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：restore(srcName: string, callback: AsyncCallback\<void>): void;<br>差异内容：restore(srcName: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：restore(srcName: string): Promise\<void>;<br>差异内容：restore(srcName: string): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>, callback: AsyncCallback\<void>): void;<br>差异内容：setDistributedTables(tables: Array\<string>, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>): Promise\<void>;<br>差异内容：setDistributedTables(tables: Array\<string>): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>, type: DistributedType, callback: AsyncCallback\<void>): void;<br>差异内容：setDistributedTables(tables: Array\<string>, type: DistributedType, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>, type: DistributedType, config: DistributedConfig, callback: AsyncCallback\<void>): void;<br>差异内容：setDistributedTables(tables: Array\<string>, type: DistributedType, config: DistributedConfig, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setDistributedTables(tables: Array\<string>, type?: DistributedType, config?: DistributedConfig): Promise\<void>;<br>差异内容：setDistributedTables(tables: Array\<string>, type?: DistributedType, config?: DistributedConfig): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：obtainDistributedTableName(device: string, table: string, callback: AsyncCallback\<string>): void;<br>差异内容：obtainDistributedTableName(device: string, table: string, callback: AsyncCallback\<string>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：obtainDistributedTableName(device: string, table: string): Promise\<string>;<br>差异内容：obtainDistributedTableName(device: string, table: string): Promise\<string>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：sync(mode: SyncMode, predicates: RdbPredicates): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;<br>差异内容：sync(mode: SyncMode, predicates: RdbPredicates): Promise\<Array\<[<br>            string,<br>            number<br>        ]>>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cloudSync(mode: SyncMode, progress: Callback\<ProgressDetails>, callback: AsyncCallback\<void>): void;<br>差异内容：cloudSync(mode: SyncMode, progress: Callback\<ProgressDetails>, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cloudSync(mode: SyncMode, progress: Callback\<ProgressDetails>): Promise\<void>;<br>差异内容：cloudSync(mode: SyncMode, progress: Callback\<ProgressDetails>): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cloudSync(mode: SyncMode, tables: string[], progress: Callback\<ProgressDetails>, callback: AsyncCallback\<void>): void;<br>差异内容：cloudSync(mode: SyncMode, tables: string[], progress: Callback\<ProgressDetails>, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：cloudSync(mode: SyncMode, tables: string[], progress: Callback\<ProgressDetails>): Promise\<void>;<br>差异内容：cloudSync(mode: SyncMode, tables: string[], progress: Callback\<ProgressDetails>): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;<br>差异内容：remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array\<string>): Promise\<ResultSet>;<br>差异内容：remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array\<string>): Promise\<ResultSet>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>> \| Callback\<Array\<ChangeInfo>>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>> \| Callback\<Array\<ChangeInfo>>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: string, interProcess: boolean, observer: Callback\<void>): void;<br>差异内容：on(event: string, interProcess: boolean, observer: Callback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'autoSyncProgress', progress: Callback\<ProgressDetails>): void;<br>差异内容：on(event: 'autoSyncProgress', progress: Callback\<ProgressDetails>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;<br>差异内容：off(event: 'dataChange', type: SubscribeType, observer: Callback\<Array\<string>>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'dataChange', type: SubscribeType, observer?: Callback\<Array\<string>> \| Callback\<Array\<ChangeInfo>>): void;<br>差异内容：off(event: 'dataChange', type: SubscribeType, observer?: Callback\<Array\<string>> \| Callback\<Array\<ChangeInfo>>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: string, interProcess: boolean, observer?: Callback\<void>): void;<br>差异内容：off(event: string, interProcess: boolean, observer?: Callback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'autoSyncProgress', progress?: Callback\<ProgressDetails>): void;<br>差异内容：off(event: 'autoSyncProgress', progress?: Callback\<ProgressDetails>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：emit(event: string): void;<br>差异内容：emit(event: string): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback\<RdbStore>): void;<br>差异内容：function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback\<RdbStore>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getRdbStore(context: Context, config: StoreConfig): Promise\<RdbStore>;<br>差异内容：function getRdbStore(context: Context, config: StoreConfig): Promise\<RdbStore>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function deleteRdbStore(context: Context, name: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteRdbStore(context: Context, name: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function deleteRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback\<void>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function deleteRdbStore(context: Context, name: string): Promise\<void>;<br>差异内容：function deleteRdbStore(context: Context, name: string): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function deleteRdbStore(context: Context, config: StoreConfig): Promise\<void>;<br>差异内容：function deleteRdbStore(context: Context, config: StoreConfig): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace storage<br>差异内容：declare namespace storage|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function getStorageSync(path: string): Storage;<br>差异内容：function getStorageSync(path: string): Storage;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function getStorage(path: string, callback: AsyncCallback\<Storage>): void;<br>差异内容：function getStorage(path: string, callback: AsyncCallback\<Storage>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function getStorage(path: string): Promise\<Storage>;<br>差异内容：function getStorage(path: string): Promise\<Storage>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function deleteStorageSync(path: string): void;<br>差异内容：function deleteStorageSync(path: string): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function deleteStorage(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：function deleteStorage(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function deleteStorage(path: string): Promise\<void>;<br>差异内容：function deleteStorage(path: string): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function removeStorageFromCacheSync(path: string): void;<br>差异内容：function removeStorageFromCacheSync(path: string): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function removeStorageFromCache(path: string, callback: AsyncCallback\<void>): void;<br>差异内容：function removeStorageFromCache(path: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：function removeStorageFromCache(path: string): Promise\<void>;<br>差异内容：function removeStorageFromCache(path: string): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：interface Storage<br>差异内容：interface Storage|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：getSync(key: string, defValue: ValueType): ValueType;<br>差异内容：getSync(key: string, defValue: ValueType): ValueType;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：get(key: string, defValue: ValueType, callback: AsyncCallback\<ValueType>): void;<br>差异内容：get(key: string, defValue: ValueType, callback: AsyncCallback\<ValueType>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：get(key: string, defValue: ValueType): Promise\<ValueType>;<br>差异内容：get(key: string, defValue: ValueType): Promise\<ValueType>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：hasSync(key: string): boolean;<br>差异内容：hasSync(key: string): boolean;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：has(key: string, callback: AsyncCallback\<boolean>): boolean;<br>差异内容：has(key: string, callback: AsyncCallback\<boolean>): boolean;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：has(key: string): Promise\<boolean>;<br>差异内容：has(key: string): Promise\<boolean>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：putSync(key: string, value: ValueType): void;<br>差异内容：putSync(key: string, value: ValueType): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：put(key: string, value: ValueType, callback: AsyncCallback\<void>): void;<br>差异内容：put(key: string, value: ValueType, callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：put(key: string, value: ValueType): Promise\<void>;<br>差异内容：put(key: string, value: ValueType): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：deleteSync(key: string): void;<br>差异内容：deleteSync(key: string): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：delete(key: string, callback: AsyncCallback\<void>): void;<br>差异内容：delete(key: string, callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：delete(key: string): Promise\<void>;<br>差异内容：delete(key: string): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：clearSync(): void;<br>差异内容：clearSync(): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：clear(callback: AsyncCallback\<void>): void;<br>差异内容：clear(callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：clear(): Promise\<void>;<br>差异内容：clear(): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：flushSync(): void;<br>差异内容：flushSync(): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：flush(callback: AsyncCallback\<void>): void;<br>差异内容：flush(callback: AsyncCallback\<void>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：flush(): Promise\<void>;<br>差异内容：flush(): Promise\<void>;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：on(type: 'change', callback: Callback\<StorageObserver>): void;<br>差异内容：on(type: 'change', callback: Callback\<StorageObserver>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：off(type: 'change', callback: Callback\<StorageObserver>): void;<br>差异内容：off(type: 'change', callback: Callback\<StorageObserver>): void;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：type ValueType = number \| string \| boolean;<br>差异内容：type ValueType = number \| string \| boolean;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：interface StorageObserver<br>差异内容：interface StorageObserver|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：StorageObserver；<br>API声明：key: string;<br>差异内容：key: string;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：const MAX_KEY_LENGTH: 80;<br>差异内容：const MAX_KEY_LENGTH: 80;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：storage；<br>API声明：const MAX_VALUE_LENGTH: 8192;<br>差异内容：const MAX_VALUE_LENGTH: 8192;|api/@ohos.data.storage.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace unifiedDataChannel<br>差异内容：declare namespace unifiedDataChannel|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class UnifiedData<br>差异内容：class UnifiedData|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedData；<br>API声明：addRecord(record: UnifiedRecord): void;<br>差异内容：addRecord(record: UnifiedRecord): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedData；<br>API声明：getRecords(): Array\<UnifiedRecord>;<br>差异内容：getRecords(): Array\<UnifiedRecord>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Summary<br>差异内容：class Summary|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Summary；<br>API声明：summary: Record\<string, number>;<br>差异内容：summary: Record\<string, number>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Summary；<br>API声明：totalSize: number;<br>差异内容：totalSize: number;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class UnifiedRecord<br>差异内容：class UnifiedRecord|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedRecord；<br>API声明：getType(): string;<br>差异内容：getType(): string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Text<br>差异内容：class Text|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Text；<br>API声明：details?: Record\<string, string>;<br>差异内容：details?: Record\<string, string>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class PlainText<br>差异内容：class PlainText|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：PlainText；<br>API声明：textContent: string;<br>差异内容：textContent: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：PlainText；<br>API声明：abstract?: string;<br>差异内容：abstract?: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Hyperlink<br>差异内容：class Hyperlink|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Hyperlink；<br>API声明：url: string;<br>差异内容：url: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Hyperlink；<br>API声明：description?: string;<br>差异内容：description?: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class HTML<br>差异内容：class HTML|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：HTML；<br>API声明：htmlContent: string;<br>差异内容：htmlContent: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：HTML；<br>API声明：plainContent?: string;<br>差异内容：plainContent?: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class File<br>差异内容：class File|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：File；<br>API声明：details?: Record\<string, string>;<br>差异内容：details?: Record\<string, string>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：File；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Image<br>差异内容：class Image|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Image；<br>API声明：imageUri: string;<br>差异内容：imageUri: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Video<br>差异内容：class Video|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Video；<br>API声明：videoUri: string;<br>差异内容：videoUri: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Audio<br>差异内容：class Audio|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Audio；<br>API声明：audioUri: string;<br>差异内容：audioUri: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class Folder<br>差异内容：class Folder|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Folder；<br>API声明：folderUri: string;<br>差异内容：folderUri: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class SystemDefinedRecord<br>差异内容：class SystemDefinedRecord|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedRecord；<br>API声明：details?: Record\<string, number \| string \| Uint8Array>;<br>差异内容：details?: Record\<string, number \| string \| Uint8Array>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class SystemDefinedForm<br>差异内容：class SystemDefinedForm|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedForm；<br>API声明：formId: number;<br>差异内容：formId: number;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedForm；<br>API声明：formName: string;<br>差异内容：formName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedForm；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedForm；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedForm；<br>API声明：module: string;<br>差异内容：module: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class SystemDefinedAppItem<br>差异内容：class SystemDefinedAppItem|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：appId: string;<br>差异内容：appId: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：appName: string;<br>差异内容：appName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：appIconId: string;<br>差异内容：appIconId: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：appLabelId: string;<br>差异内容：appLabelId: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedAppItem；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class SystemDefinedPixelMap<br>差异内容：class SystemDefinedPixelMap|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：SystemDefinedPixelMap；<br>API声明：rawData: Uint8Array;<br>差异内容：rawData: Uint8Array;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：class ApplicationDefinedRecord<br>差异内容：class ApplicationDefinedRecord|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ApplicationDefinedRecord；<br>API声明：applicationDefinedType: string;<br>差异内容：applicationDefinedType: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ApplicationDefinedRecord；<br>API声明：rawData: Uint8Array;<br>差异内容：rawData: Uint8Array;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：enum Intention<br>差异内容：enum Intention|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Intention；<br>API声明：DATA_HUB = 'DataHub'<br>差异内容：DATA_HUB = 'DataHub'|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：type Options = {<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        intention?: Intention;<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        key?: string;<br>    };<br>差异内容：type Options = {<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        intention?: Intention;<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        key?: string;<br>    };|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function insertData(options: Options, data: UnifiedData, callback: AsyncCallback\<string>): void;<br>差异内容：function insertData(options: Options, data: UnifiedData, callback: AsyncCallback\<string>): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function insertData(options: Options, data: UnifiedData): Promise\<string>;<br>差异内容：function insertData(options: Options, data: UnifiedData): Promise\<string>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function updateData(options: Options, data: UnifiedData, callback: AsyncCallback\<void>): void;<br>差异内容：function updateData(options: Options, data: UnifiedData, callback: AsyncCallback\<void>): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function updateData(options: Options, data: UnifiedData): Promise\<void>;<br>差异内容：function updateData(options: Options, data: UnifiedData): Promise\<void>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function queryData(options: Options, callback: AsyncCallback\<Array\<UnifiedData>>): void;<br>差异内容：function queryData(options: Options, callback: AsyncCallback\<Array\<UnifiedData>>): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function queryData(options: Options): Promise\<Array\<UnifiedData>>;<br>差异内容：function queryData(options: Options): Promise\<Array\<UnifiedData>>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function deleteData(options: Options, callback: AsyncCallback\<Array\<UnifiedData>>): void;<br>差异内容：function deleteData(options: Options, callback: AsyncCallback\<Array\<UnifiedData>>): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function deleteData(options: Options): Promise\<Array\<UnifiedData>>;<br>差异内容：function deleteData(options: Options): Promise\<Array\<UnifiedData>>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace uniformTypeDescriptor<br>差异内容：declare namespace uniformTypeDescriptor|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：uniformTypeDescriptor；<br>API声明：enum UniformDataType<br>差异内容：enum UniformDataType|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ENTITY = 'general.entity'<br>差异内容：ENTITY = 'general.entity'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OBJECT = 'general.object'<br>差异内容：OBJECT = 'general.object'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：COMPOSITE_OBJECT = 'general.composite-object'<br>差异内容：COMPOSITE_OBJECT = 'general.composite-object'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：TEXT = 'general.text'<br>差异内容：TEXT = 'general.text'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PLAIN_TEXT = 'general.plain-text'<br>差异内容：PLAIN_TEXT = 'general.plain-text'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：HTML = 'general.html'<br>差异内容：HTML = 'general.html'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：HYPERLINK = 'general.hyperlink'<br>差异内容：HYPERLINK = 'general.hyperlink'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：XML = 'general.xml'<br>差异内容：XML = 'general.xml'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：SOURCE_CODE = 'general.source-code'<br>差异内容：SOURCE_CODE = 'general.source-code'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：SCRIPT = 'general.script'<br>差异内容：SCRIPT = 'general.script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：SHELL_SCRIPT = 'general.shell-script'<br>差异内容：SHELL_SCRIPT = 'general.shell-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：CSH_SCRIPT = 'general.csh-script'<br>差异内容：CSH_SCRIPT = 'general.csh-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PERL_SCRIPT = 'general.perl-script'<br>差异内容：PERL_SCRIPT = 'general.perl-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PHP_SCRIPT = 'general.php-script'<br>差异内容：PHP_SCRIPT = 'general.php-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PYTHON_SCRIPT = 'general.python-script'<br>差异内容：PYTHON_SCRIPT = 'general.python-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：RUBY_SCRIPT = 'general.ruby-script'<br>差异内容：RUBY_SCRIPT = 'general.ruby-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：TYPE_SCRIPT = 'general.type-script'<br>差异内容：TYPE_SCRIPT = 'general.type-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：JAVA_SCRIPT = 'general.java-script'<br>差异内容：JAVA_SCRIPT = 'general.java-script'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：C_HEADER = 'general.c-header'<br>差异内容：C_HEADER = 'general.c-header'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：C_SOURCE = 'general.c-source'<br>差异内容：C_SOURCE = 'general.c-source'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'<br>差异内容：C_PLUS_PLUS_HEADER = 'general.c-plus-plus-header'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'<br>差异内容：C_PLUS_PLUS_SOURCE = 'general.c-plus-plus-source'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：JAVA_SOURCE = 'general.java-source'<br>差异内容：JAVA_SOURCE = 'general.java-source'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：EBOOK = 'general.ebook'<br>差异内容：EBOOK = 'general.ebook'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：EPUB = 'general.epub'<br>差异内容：EPUB = 'general.epub'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AZW = 'com.amazon.azw'<br>差异内容：AZW = 'com.amazon.azw'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AZW3 = 'com.amazon.azw3'<br>差异内容：AZW3 = 'com.amazon.azw3'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：KFX = 'com.amazon.kfx'<br>差异内容：KFX = 'com.amazon.kfx'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MOBI = 'com.amazon.mobi'<br>差异内容：MOBI = 'com.amazon.mobi'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MEDIA = 'general.media'<br>差异内容：MEDIA = 'general.media'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：IMAGE = 'general.image'<br>差异内容：IMAGE = 'general.image'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：JPEG = 'general.jpeg'<br>差异内容：JPEG = 'general.jpeg'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PNG = 'general.png'<br>差异内容：PNG = 'general.png'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：RAW_IMAGE = 'general.raw-image'<br>差异内容：RAW_IMAGE = 'general.raw-image'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：TIFF = 'general.tiff'<br>差异内容：TIFF = 'general.tiff'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：BMP = 'com.microsoft.bmp'<br>差异内容：BMP = 'com.microsoft.bmp'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ICO = 'com.microsoft.ico'<br>差异内容：ICO = 'com.microsoft.ico'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'<br>差异内容：PHOTOSHOP_IMAGE = 'com.adobe.photoshop-image'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AI_IMAGE = 'com.adobe.illustrator.ai-image'<br>差异内容：AI_IMAGE = 'com.adobe.illustrator.ai-image'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WORD_DOC = 'com.microsoft.word.doc'<br>差异内容：WORD_DOC = 'com.microsoft.word.doc'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：EXCEL = 'com.microsoft.excel.xls'<br>差异内容：EXCEL = 'com.microsoft.excel.xls'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PPT = 'com.microsoft.powerpoint.ppt'<br>差异内容：PPT = 'com.microsoft.powerpoint.ppt'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PDF = 'com.adobe.pdf'<br>差异内容：PDF = 'com.adobe.pdf'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：POSTSCRIPT = 'com.adobe.postscript'<br>差异内容：POSTSCRIPT = 'com.adobe.postscript'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'<br>差异内容：ENCAPSULATED_POSTSCRIPT = 'com.adobe.encapsulated-postscript'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：VIDEO = 'general.video'<br>差异内容：VIDEO = 'general.video'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AVI = 'general.avi'<br>差异内容：AVI = 'general.avi'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MPEG = 'general.mpeg'<br>差异内容：MPEG = 'general.mpeg'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MPEG4 = 'general.mpeg-4'<br>差异内容：MPEG4 = 'general.mpeg-4'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：VIDEO_3GPP = 'general.3gpp'<br>差异内容：VIDEO_3GPP = 'general.3gpp'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：VIDEO_3GPP2 = 'general.3gpp2'<br>差异内容：VIDEO_3GPP2 = 'general.3gpp2'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'<br>差异内容：WINDOWS_MEDIA_WM = 'com.microsoft.windows-media-wm'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'<br>差异内容：WINDOWS_MEDIA_WMV = 'com.microsoft.windows-media-wmv'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'<br>差异内容：WINDOWS_MEDIA_WMP = 'com.microsoft.windows-media-wmp'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AUDIO = 'general.audio'<br>差异内容：AUDIO = 'general.audio'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AAC = 'general.aac'<br>差异内容：AAC = 'general.aac'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：AIFF = 'general.aiff'<br>差异内容：AIFF = 'general.aiff'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ALAC = 'general.alac'<br>差异内容：ALAC = 'general.alac'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：FLAC = 'general.flac'<br>差异内容：FLAC = 'general.flac'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MP3 = 'general.mp3'<br>差异内容：MP3 = 'general.mp3'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OGG = 'general.ogg'<br>差异内容：OGG = 'general.ogg'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：PCM = 'general.pcm'<br>差异内容：PCM = 'general.pcm'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'<br>差异内容：WINDOWS_MEDIA_WMA = 'com.microsoft.windows-media-wma'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'<br>差异内容：WAVEFORM_AUDIO = 'com.microsoft.waveform-audio'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'<br>差异内容：WINDOWS_MEDIA_WMX = 'com.microsoft.windows-media-wmx'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'<br>差异内容：WINDOWS_MEDIA_WVX = 'com.microsoft.windows-media-wvx'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'<br>差异内容：WINDOWS_MEDIA_WAX = 'com.microsoft.windows-media-wax'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：FILE = 'general.file'<br>差异内容：FILE = 'general.file'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：DIRECTORY = 'general.directory'<br>差异内容：DIRECTORY = 'general.directory'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：FOLDER = 'general.folder'<br>差异内容：FOLDER = 'general.folder'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：SYMLINK = 'general.symlink'<br>差异内容：SYMLINK = 'general.symlink'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ARCHIVE = 'general.archive'<br>差异内容：ARCHIVE = 'general.archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：BZ2_ARCHIVE = 'general.bz2-archive'<br>差异内容：BZ2_ARCHIVE = 'general.bz2-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：DISK_IMAGE = 'general.disk-image'<br>差异内容：DISK_IMAGE = 'general.disk-image'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：TAR_ARCHIVE = 'general.tar-archive'<br>差异内容：TAR_ARCHIVE = 'general.tar-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：ZIP_ARCHIVE = 'general.zip-archive'<br>差异内容：ZIP_ARCHIVE = 'general.zip-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：JAVA_ARCHIVE = 'com.sun.java-archive'<br>差异内容：JAVA_ARCHIVE = 'com.sun.java-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'<br>差异内容：GNU_TAR_ARCHIVE = 'org.gnu.gnu-tar-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'<br>差异内容：GNU_ZIP_ARCHIVE = 'org.gnu.gnu-zip-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'<br>差异内容：GNU_ZIP_TAR_ARCHIVE = 'org.gnu.gnu-zip-tar-archive'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：CALENDAR = 'general.calendar'<br>差异内容：CALENDAR = 'general.calendar'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：CONTACT = 'general.contact'<br>差异内容：CONTACT = 'general.contact'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：DATABASE = 'general.database'<br>差异内容：DATABASE = 'general.database'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：MESSAGE = 'general.message'<br>差异内容：MESSAGE = 'general.message'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：VCARD = 'general.vcard'<br>差异内容：VCARD = 'general.vcard'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：NAVIGATION = 'general.navigation'<br>差异内容：NAVIGATION = 'general.navigation'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：LOCATION = 'general.location'<br>差异内容：LOCATION = 'general.location'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_FORM = 'openharmony.form'<br>差异内容：OPENHARMONY_FORM = 'openharmony.form'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_APP_ITEM = 'openharmony.app-item'<br>差异内容：OPENHARMONY_APP_ITEM = 'openharmony.app-item'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'<br>差异内容：OPENHARMONY_PIXEL_MAP = 'openharmony.pixel-map'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'<br>差异内容：OPENHARMONY_ATOMIC_SERVICE = 'openharmony.atomic-service'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_PACKAGE = 'openharmony.package'<br>差异内容：OPENHARMONY_PACKAGE = 'openharmony.package'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：OPENHARMONY_HAP = 'openharmony.hap'<br>差异内容：OPENHARMONY_HAP = 'openharmony.hap'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：uniformTypeDescriptor；<br>API声明：class TypeDescriptor<br>差异内容：class TypeDescriptor|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：readonly typeId: string;<br>差异内容：readonly typeId: string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：readonly belongingToTypes: Array\<string>;<br>差异内容：readonly belongingToTypes: Array\<string>;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：readonly description: string;<br>差异内容：readonly description: string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：readonly referenceURL: string;<br>差异内容：readonly referenceURL: string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：readonly iconFile: string;<br>差异内容：readonly iconFile: string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：belongsTo(type: string): boolean;<br>差异内容：belongsTo(type: string): boolean;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：isLowerLevelType(type: string): boolean;<br>差异内容：isLowerLevelType(type: string): boolean;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：isHigherLevelType(type: string): boolean;<br>差异内容：isHigherLevelType(type: string): boolean;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：TypeDescriptor；<br>API声明：equals(typeDescriptor: TypeDescriptor): boolean;<br>差异内容：equals(typeDescriptor: TypeDescriptor): boolean;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：uniformTypeDescriptor；<br>API声明：function getTypeDescriptor(typeId: string): TypeDescriptor;<br>差异内容：function getTypeDescriptor(typeId: string): TypeDescriptor;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string;<br>差异内容：function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string;<br>差异内容：function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string;|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：global；<br>API声明：export type ValueType = number \| string \| boolean;<br>差异内容：export type ValueType = number \| string \| boolean;|api/@ohos.data.ValuesBucket.d.ts|
|新增API|NA|类名：global；<br>API声明：export type ValuesBucket = Record\<string, ValueType \| Uint8Array \| null>;<br>差异内容：export type ValuesBucket = Record\<string, ValueType \| Uint8Array \| null>;|api/@ohos.data.ValuesBucket.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface GetStorageOptions<br>差异内容：export interface GetStorageOptions|api/@system.storage.d.ts|
|新增API|NA|类名：GetStorageOptions；<br>API声明：key: string;<br>差异内容：key: string;|api/@system.storage.d.ts|
|新增API|NA|类名：GetStorageOptions；<br>API声明：default?: string;<br>差异内容：default?: string;|api/@system.storage.d.ts|
|新增API|NA|类名：GetStorageOptions；<br>API声明：success?: (data: any) => void;<br>差异内容：success?: (data: any) => void;|api/@system.storage.d.ts|
|新增API|NA|类名：GetStorageOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.storage.d.ts|
|新增API|NA|类名：GetStorageOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface SetStorageOptions<br>差异内容：export interface SetStorageOptions|api/@system.storage.d.ts|
|新增API|NA|类名：SetStorageOptions；<br>API声明：key: string;<br>差异内容：key: string;|api/@system.storage.d.ts|
|新增API|NA|类名：SetStorageOptions；<br>API声明：value: string;<br>差异内容：value: string;|api/@system.storage.d.ts|
|新增API|NA|类名：SetStorageOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：SetStorageOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.storage.d.ts|
|新增API|NA|类名：SetStorageOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ClearStorageOptions<br>差异内容：export interface ClearStorageOptions|api/@system.storage.d.ts|
|新增API|NA|类名：ClearStorageOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：ClearStorageOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.storage.d.ts|
|新增API|NA|类名：ClearStorageOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface DeleteStorageOptions<br>差异内容：export interface DeleteStorageOptions|api/@system.storage.d.ts|
|新增API|NA|类名：DeleteStorageOptions；<br>API声明：key: string;<br>差异内容：key: string;|api/@system.storage.d.ts|
|新增API|NA|类名：DeleteStorageOptions；<br>API声明：success?: () => void;<br>差异内容：success?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：DeleteStorageOptions；<br>API声明：fail?: (data: string, code: number) => void;<br>差异内容：fail?: (data: string, code: number) => void;|api/@system.storage.d.ts|
|新增API|NA|类名：DeleteStorageOptions；<br>API声明：complete?: () => void;<br>差异内容：complete?: () => void;|api/@system.storage.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Storage<br>差异内容：export default class Storage|api/@system.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：static get(options: GetStorageOptions): void;<br>差异内容：static get(options: GetStorageOptions): void;|api/@system.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：static set(options: SetStorageOptions): void;<br>差异内容：static set(options: SetStorageOptions): void;|api/@system.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：static clear(options?: ClearStorageOptions): void;<br>差异内容：static clear(options?: ClearStorageOptions): void;|api/@system.storage.d.ts|
|新增API|NA|类名：Storage；<br>API声明：static delete(options: DeleteStorageOptions): void;<br>差异内容：static delete(options: DeleteStorageOptions): void;|api/@system.storage.d.ts|
|成员由父类迁移至子类|类名：KVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;|类名：SingleKVStore；<br>API声明：on(event: 'dataChange', type: SubscribeType, listener: Callback\<ChangeNotification>): void;<br>差异内容：NA|api/@ohos.data.distributedData.d.ts|
|成员由父类迁移至子类|类名：KVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|类名：SingleKVStore；<br>API声明：on(event: 'syncComplete', syncCallback: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：NA|api/@ohos.data.distributedData.d.ts|
|成员由父类迁移至子类|类名：KVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;|类名：SingleKVStore；<br>API声明：off(event: 'dataChange', listener?: Callback\<ChangeNotification>): void;<br>差异内容：NA|api/@ohos.data.distributedData.d.ts|
|成员由父类迁移至子类|类名：KVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;|类名：SingleKVStore；<br>API声明：off(event: 'syncComplete', syncCallback?: Callback\<Array\<[<br>            string,<br>            number<br>        ]>>): void;<br>差异内容：NA|api/@ohos.data.distributedData.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;|类名：DeviceKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;<br>差异内容：get(key: string): Promise\<boolean \| string \| number \| Uint8Array>;|类名：DeviceKVStore；<br>API声明：get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getEntries(keyPrefix: string): Promise\<Entry[]>;<br>差异内容：getEntries(keyPrefix: string): Promise\<Entry[]>;|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：getEntries(query: Query, callback: AsyncCallback\<Entry[]>): void;|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getEntries(query: Query): Promise\<Entry[]>;<br>差异内容：getEntries(query: Query): Promise\<Entry[]>;|类名：DeviceKVStore；<br>API声明：getEntries(keyPrefix: string, callback: AsyncCallback\<Entry[]>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(keyPrefix: string): Promise\<KVStoreResultSet>;|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：getResultSet(query: Query, callback: AsyncCallback\<KVStoreResultSet>): void;|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSet(query: Query): Promise\<KVStoreResultSet>;<br>差异内容：getResultSet(query: Query): Promise\<KVStoreResultSet>;|类名：DeviceKVStore；<br>API声明：getResultSet(keyPrefix: string, callback: AsyncCallback\<KVStoreResultSet>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：getResultSize(query: Query, callback: AsyncCallback\<number>): void;|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|成员由父类迁移至子类|类名：SingleKVStore；<br>API声明：getResultSize(query: Query): Promise\<number>;<br>差异内容：getResultSize(query: Query): Promise\<number>;|类名：DeviceKVStore；<br>API声明：getResultSize(query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：NA|api/@ohos.data.distributedKVStore.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.cloudExtension.d.ts<br>差异内容：ArkData|api/@ohos.data.cloudExtension.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.commonType.d.ts<br>差异内容：ArkData|api/@ohos.data.commonType.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.dataAbility.d.ts<br>差异内容：ArkData|api/@ohos.data.dataAbility.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.dataSharePredicates.d.ts<br>差异内容：ArkData|api/@ohos.data.dataSharePredicates.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.distributedData.d.ts<br>差异内容：ArkData|api/@ohos.data.distributedData.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.distributedDataObject.d.ts<br>差异内容：ArkData|api/@ohos.data.distributedDataObject.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.distributedKVStore.d.ts<br>差异内容：ArkData|api/@ohos.data.distributedKVStore.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.preferences.d.ts<br>差异内容：ArkData|api/@ohos.data.preferences.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.rdb.d.ts<br>差异内容：ArkData|api/@ohos.data.rdb.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.relationalStore.d.ts<br>差异内容：ArkData|api/@ohos.data.relationalStore.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.storage.d.ts<br>差异内容：ArkData|api/@ohos.data.storage.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.unifiedDataChannel.d.ts<br>差异内容：ArkData|api/@ohos.data.unifiedDataChannel.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.uniformTypeDescriptor.d.ts<br>差异内容：ArkData|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.ValuesBucket.d.ts<br>差异内容：ArkData|api/@ohos.data.ValuesBucket.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.storage.d.ts<br>差异内容：ArkData|api/@system.storage.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.ArkData.d.ts<br>差异内容：ArkData|kits/@kit.ArkData.d.ts|
