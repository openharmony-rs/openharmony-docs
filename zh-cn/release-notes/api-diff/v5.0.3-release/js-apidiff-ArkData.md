| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|API跨平台权限变更|类名：Preferences；<br>API声明：on(type: 'dataChange', keys: Array\<string>, callback: Callback\<Record\<string, ValueType>>): void;<br>差异内容：NA|类名：Preferences；<br>API声明：on(type: 'dataChange', keys: Array\<string>, callback: Callback\<Record\<string, ValueType>>): void;<br>差异内容：crossplatform|api/@ohos.data.preferences.d.ts|
|API跨平台权限变更|类名：Preferences；<br>API声明：off(type: 'dataChange', keys: Array\<string>, callback?: Callback\<Record\<string, ValueType>>): void;<br>差异内容：NA|类名：Preferences；<br>API声明：off(type: 'dataChange', keys: Array\<string>, callback?: Callback\<Record\<string, ValueType>>): void;<br>差异内容：crossplatform|api/@ohos.data.preferences.d.ts|
|API跨平台权限变更|类名：StoreConfig；<br>API声明：isReadOnly?: boolean;<br>差异内容：NA|类名：StoreConfig；<br>API声明：isReadOnly?: boolean;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：StoreConfig；<br>API声明：cryptoParam?: CryptoParam;<br>差异内容：NA|类名：StoreConfig；<br>API声明：cryptoParam?: CryptoParam;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：interface CryptoParam<br>差异内容：NA|类名：relationalStore；<br>API声明：interface CryptoParam<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：encryptionKey: Uint8Array;<br>差异内容：NA|类名：CryptoParam；<br>API声明：encryptionKey: Uint8Array;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：iterationCount?: number;<br>差异内容：NA|类名：CryptoParam；<br>API声明：iterationCount?: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：encryptionAlgo?: EncryptionAlgo;<br>差异内容：NA|类名：CryptoParam；<br>API声明：encryptionAlgo?: EncryptionAlgo;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：hmacAlgo?: HmacAlgo;<br>差异内容：NA|类名：CryptoParam；<br>API声明：hmacAlgo?: HmacAlgo;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：kdfAlgo?: KdfAlgo;<br>差异内容：NA|类名：CryptoParam；<br>API声明：kdfAlgo?: KdfAlgo;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：CryptoParam；<br>API声明：cryptoPageSize?: number;<br>差异内容：NA|类名：CryptoParam；<br>API声明：cryptoPageSize?: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：enum EncryptionAlgo<br>差异内容：NA|类名：relationalStore；<br>API声明：enum EncryptionAlgo<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：EncryptionAlgo；<br>API声明：AES_256_GCM = 0<br>差异内容：NA|类名：EncryptionAlgo；<br>API声明：AES_256_GCM = 0<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：EncryptionAlgo；<br>API声明：AES_256_CBC<br>差异内容：NA|类名：EncryptionAlgo；<br>API声明：AES_256_CBC<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：enum HmacAlgo<br>差异内容：NA|类名：relationalStore；<br>API声明：enum HmacAlgo<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：HmacAlgo；<br>API声明：SHA1 = 0<br>差异内容：NA|类名：HmacAlgo；<br>API声明：SHA1 = 0<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：HmacAlgo；<br>API声明：SHA256<br>差异内容：NA|类名：HmacAlgo；<br>API声明：SHA256<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：HmacAlgo；<br>API声明：SHA512<br>差异内容：NA|类名：HmacAlgo；<br>API声明：SHA512<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：enum KdfAlgo<br>差异内容：NA|类名：relationalStore；<br>API声明：enum KdfAlgo<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：KdfAlgo；<br>API声明：KDF_SHA1 = 0<br>差异内容：NA|类名：KdfAlgo；<br>API声明：KDF_SHA1 = 0<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：KdfAlgo；<br>API声明：KDF_SHA256<br>差异内容：NA|类名：KdfAlgo；<br>API声明：KDF_SHA256<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：KdfAlgo；<br>API声明：KDF_SHA512<br>差异内容：NA|类名：KdfAlgo；<br>API声明：KDF_SHA512<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：interface SqlExecutionInfo<br>差异内容：NA|类名：relationalStore；<br>API声明：interface SqlExecutionInfo<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：SqlExecutionInfo；<br>API声明：sql: Array\<string>;<br>差异内容：NA|类名：SqlExecutionInfo；<br>API声明：sql: Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：SqlExecutionInfo；<br>API声明：totalTime: number;<br>差异内容：NA|类名：SqlExecutionInfo；<br>API声明：totalTime: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：SqlExecutionInfo；<br>API声明：waitTime: number;<br>差异内容：NA|类名：SqlExecutionInfo；<br>API声明：waitTime: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：SqlExecutionInfo；<br>API声明：prepareTime: number;<br>差异内容：NA|类名：SqlExecutionInfo；<br>API声明：prepareTime: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：SqlExecutionInfo；<br>API声明：executeTime: number;<br>差异内容：NA|类名：SqlExecutionInfo；<br>API声明：executeTime: number;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：enum Field<br>差异内容：NA|类名：relationalStore；<br>API声明：enum Field<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：CURSOR_FIELD = '#_cursor'<br>差异内容：NA|类名：Field；<br>API声明：CURSOR_FIELD = '#_cursor'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：ORIGIN_FIELD = '#_origin'<br>差异内容：NA|类名：Field；<br>API声明：ORIGIN_FIELD = '#_origin'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：DELETED_FLAG_FIELD = '#_deleted_flag'<br>差异内容：NA|类名：Field；<br>API声明：DELETED_FLAG_FIELD = '#_deleted_flag'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：DATA_STATUS_FIELD = '#_data_status'<br>差异内容：NA|类名：Field；<br>API声明：DATA_STATUS_FIELD = '#_data_status'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：OWNER_FIELD = '#_cloud_owner'<br>差异内容：NA|类名：Field；<br>API声明：OWNER_FIELD = '#_cloud_owner'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：PRIVILEGE_FIELD = '#_cloud_privilege'<br>差异内容：NA|类名：Field；<br>API声明：PRIVILEGE_FIELD = '#_cloud_privilege'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Field；<br>API声明：SHARING_RESOURCE_FIELD = '#_sharing_resource_field'<br>差异内容：NA|类名：Field；<br>API声明：SHARING_RESOURCE_FIELD = '#_sharing_resource_field'<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：enum TransactionType<br>差异内容：NA|类名：relationalStore；<br>API声明：enum TransactionType<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：TransactionType；<br>API声明：DEFERRED<br>差异内容：NA|类名：TransactionType；<br>API声明：DEFERRED<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：TransactionType；<br>API声明：IMMEDIATE<br>差异内容：NA|类名：TransactionType；<br>API声明：IMMEDIATE<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：TransactionType；<br>API声明：EXCLUSIVE<br>差异内容：NA|类名：TransactionType；<br>API声明：EXCLUSIVE<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：relationalStore；<br>API声明：interface TransactionOptions<br>差异内容：NA|类名：relationalStore；<br>API声明：interface TransactionOptions<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：TransactionOptions；<br>API声明：transactionType?: TransactionType;<br>差异内容：NA|类名：TransactionOptions；<br>API声明：transactionType?: TransactionType;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：RdbPredicates；<br>API声明：notContains(field: string, value: string): RdbPredicates;<br>差异内容：NA|类名：RdbPredicates；<br>API声明：notContains(field: string, value: string): RdbPredicates;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：RdbPredicates；<br>API声明：notLike(field: string, value: string): RdbPredicates;<br>差异内容：NA|类名：RdbPredicates；<br>API声明：notLike(field: string, value: string): RdbPredicates;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：ResultSet；<br>API声明：getValue(columnIndex: number): ValueType;<br>差异内容：NA|类名：ResultSet；<br>API声明：getValue(columnIndex: number): ValueType;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：RdbStore；<br>API声明：on(event: 'statistics', observer: Callback\<SqlExecutionInfo>): void;<br>差异内容：NA|类名：RdbStore；<br>API声明：on(event: 'statistics', observer: Callback\<SqlExecutionInfo>): void;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：RdbStore；<br>API声明：off(event: 'statistics', observer?: Callback\<SqlExecutionInfo>): void;<br>差异内容：NA|类名：RdbStore；<br>API声明：off(event: 'statistics', observer?: Callback\<SqlExecutionInfo>): void;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：RdbStore；<br>API声明：close(): Promise\<void>;<br>差异内容：NA|类名：RdbStore；<br>API声明：close(): Promise\<void>;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：Transaction；<br>API声明：execute(sql: string, args?: Array\<ValueType>): Promise\<ValueType>;<br>差异内容：NA|类名：Transaction；<br>API声明：execute(sql: string, args?: Array\<ValueType>): Promise\<ValueType>;<br>差异内容：crossplatform|api/@ohos.data.relationalStore.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：class TypeDescriptor<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：class TypeDescriptor<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly typeId: string;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly typeId: string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly belongingToTypes: Array\<string>;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly belongingToTypes: Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly description: string;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly description: string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly referenceURL: string;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly referenceURL: string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly iconFile: string;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly iconFile: string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly filenameExtensions: Array\<string>;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly filenameExtensions: Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：readonly mimeTypes: Array\<string>;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：readonly mimeTypes: Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：belongsTo(type: string): boolean;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：belongsTo(type: string): boolean;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：isLowerLevelType(type: string): boolean;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：isLowerLevelType(type: string): boolean;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：isHigherLevelType(type: string): boolean;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：isHigherLevelType(type: string): boolean;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：TypeDescriptor；<br>API声明：equals(typeDescriptor: TypeDescriptor): boolean;<br>差异内容：NA|类名：TypeDescriptor；<br>API声明：equals(typeDescriptor: TypeDescriptor): boolean;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：function getTypeDescriptor(typeId: string): TypeDescriptor;<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：function getTypeDescriptor(typeId: string): TypeDescriptor;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string;<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByFilenameExtension(filenameExtension: string, belongsTo?: string): string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string;<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypeByMIMEType(mimeType: string, belongsTo?: string): string;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypesByFilenameExtension(filenameExtension: string, belongsTo?: string): Array\<string>;<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypesByFilenameExtension(filenameExtension: string, belongsTo?: string): Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|API跨平台权限变更|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypesByMIMEType(mimeType: string, belongsTo?: string): Array\<string>;<br>差异内容：NA|类名：uniformTypeDescriptor；<br>API声明：function getUniformDataTypesByMIMEType(mimeType: string, belongsTo?: string): Array\<string>;<br>差异内容：crossplatform|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增错误码|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query, callback: AsyncCallback\<number>): void;<br>差异内容：15100004|api/@ohos.data.distributedKVStore.d.ts|
|新增错误码|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query): Promise\<number>;<br>差异内容：NA|类名：DeviceKVStore；<br>API声明：getResultSize(deviceId: string, query: Query): Promise\<number>;<br>差异内容：15100004|api/@ohos.data.distributedKVStore.d.ts|
|删除错误码|类名：DataObject；<br>API声明：setSessionId(callback: AsyncCallback\<void>): void;<br>差异内容：201|类名：DataObject；<br>API声明：setSessionId(callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.data.distributedDataObject.d.ts|
|权限变更|类名：DataObject；<br>API声明：setSessionId(callback: AsyncCallback\<void>): void;<br>差异内容：ohos.permission.DISTRIBUTED_DATASYNC|类名：DataObject；<br>API声明：setSessionId(callback: AsyncCallback\<void>): void;<br>差异内容：NA|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace dataShare<br>差异内容：declare namespace dataShare|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：enum ChangeType<br>差异内容：enum ChangeType|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ChangeType；<br>API声明：INSERT = 0<br>差异内容：INSERT = 0|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ChangeType；<br>API声明：DELETE<br>差异内容：DELETE|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ChangeType；<br>API声明：UPDATE<br>差异内容：UPDATE|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：function createDataProxyHandle(): Promise\<DataProxyHandle>;<br>差异内容：function createDataProxyHandle(): Promise\<DataProxyHandle>;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface ProxyData<br>差异内容：interface ProxyData|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ProxyData；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ProxyData；<br>API声明：value?: ValueType;<br>差异内容：value?: ValueType;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：ProxyData；<br>API声明：allowList?: string[];<br>差异内容：allowList?: string[];|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface DataProxyChangeInfo<br>差异内容：interface DataProxyChangeInfo|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyChangeInfo；<br>API声明：type: ChangeType;<br>差异内容：type: ChangeType;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyChangeInfo；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyChangeInfo；<br>API声明：value: ValueType;<br>差异内容：value: ValueType;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：enum DataProxyErrorCode<br>差异内容：enum DataProxyErrorCode|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyErrorCode；<br>API声明：SUCCESS = 0<br>差异内容：SUCCESS = 0|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyErrorCode；<br>API声明：URI_NOT_EXIST = 1<br>差异内容：URI_NOT_EXIST = 1|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyErrorCode；<br>API声明：NO_PERMISSION = 2<br>差异内容：NO_PERMISSION = 2|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyErrorCode；<br>API声明：OVER_LIMIT = 3<br>差异内容：OVER_LIMIT = 3|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface DataProxyResult<br>差异内容：interface DataProxyResult|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyResult；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyResult；<br>API声明：result: DataProxyErrorCode;<br>差异内容：result: DataProxyErrorCode;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface DataProxyGetResult<br>差异内容：interface DataProxyGetResult|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyGetResult；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyGetResult；<br>API声明：result: DataProxyErrorCode;<br>差异内容：result: DataProxyErrorCode;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyGetResult；<br>API声明：value: ValueType \| undefined;<br>差异内容：value: ValueType \| undefined;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyGetResult；<br>API声明：allowList: string[] \| undefined;<br>差异内容：allowList: string[] \| undefined;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：enum DataProxyType<br>差异内容：enum DataProxyType|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyType；<br>API声明：SHARED_CONFIG = 0<br>差异内容：SHARED_CONFIG = 0|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface DataProxyConfig<br>差异内容：interface DataProxyConfig|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyConfig；<br>API声明：type: DataProxyType;<br>差异内容：type: DataProxyType;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：dataShare；<br>API声明：interface DataProxyHandle<br>差异内容：interface DataProxyHandle|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyHandle；<br>API声明：on(event: 'dataChange', uris: string[], config: DataProxyConfig, callback: AsyncCallback\<DataProxyChangeInfo[]>): DataProxyResult[];<br>差异内容：on(event: 'dataChange', uris: string[], config: DataProxyConfig, callback: AsyncCallback\<DataProxyChangeInfo[]>): DataProxyResult[];|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyHandle；<br>API声明：off(event: 'dataChange', uris: string[], config: DataProxyConfig, callback?: AsyncCallback\<DataProxyChangeInfo[]>): DataProxyResult[];<br>差异内容：off(event: 'dataChange', uris: string[], config: DataProxyConfig, callback?: AsyncCallback\<DataProxyChangeInfo[]>): DataProxyResult[];|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyHandle；<br>API声明：publish(data: ProxyData[], config: DataProxyConfig): Promise\<DataProxyResult[]>;<br>差异内容：publish(data: ProxyData[], config: DataProxyConfig): Promise\<DataProxyResult[]>;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyHandle；<br>API声明：delete(uris: string[], config: DataProxyConfig): Promise\<DataProxyResult[]>;<br>差异内容：delete(uris: string[], config: DataProxyConfig): Promise\<DataProxyResult[]>;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：DataProxyHandle；<br>API声明：get(uris: string[], config: DataProxyConfig): Promise\<DataProxyGetResult[]>;<br>差异内容：get(uris: string[], config: DataProxyConfig): Promise\<DataProxyGetResult[]>;|api/@ohos.data.dataShare.d.ts|
|新增API|NA|类名：global；<br>API声明：declare namespace intelligence<br>差异内容：declare namespace intelligence|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：function getTextEmbeddingModel(config: ModelConfig): Promise\<TextEmbedding>;<br>差异内容：function getTextEmbeddingModel(config: ModelConfig): Promise\<TextEmbedding>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：function getImageEmbeddingModel(config: ModelConfig): Promise\<ImageEmbedding>;<br>差异内容：function getImageEmbeddingModel(config: ModelConfig): Promise\<ImageEmbedding>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：interface ModelConfig<br>差异内容：interface ModelConfig|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ModelConfig；<br>API声明：version: ModelVersion;<br>差异内容：version: ModelVersion;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ModelConfig；<br>API声明：isNpuAvailable: boolean;<br>差异内容：isNpuAvailable: boolean;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ModelConfig；<br>API声明：cachePath?: string;<br>差异内容：cachePath?: string;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：enum ModelVersion<br>差异内容：enum ModelVersion|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ModelVersion；<br>API声明：BASIC_MODEL = 0<br>差异内容：BASIC_MODEL = 0|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：interface TextEmbedding<br>差异内容：interface TextEmbedding|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：TextEmbedding；<br>API声明：loadModel(): Promise\<void>;<br>差异内容：loadModel(): Promise\<void>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：TextEmbedding；<br>API声明：releaseModel(): Promise\<void>;<br>差异内容：releaseModel(): Promise\<void>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：TextEmbedding；<br>API声明：getEmbedding(text: string): Promise\<Array\<number>>;<br>差异内容：getEmbedding(text: string): Promise\<Array\<number>>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：TextEmbedding；<br>API声明：getEmbedding(batchTexts: Array\<string>): Promise\<Array\<Array\<number>>>;<br>差异内容：getEmbedding(batchTexts: Array\<string>): Promise\<Array\<Array\<number>>>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：interface ImageEmbedding<br>差异内容：interface ImageEmbedding|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ImageEmbedding；<br>API声明：loadModel(): Promise\<void>;<br>差异内容：loadModel(): Promise\<void>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ImageEmbedding；<br>API声明：releaseModel(): Promise\<void>;<br>差异内容：releaseModel(): Promise\<void>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：ImageEmbedding；<br>API声明：getEmbedding(image: Image): Promise\<Array\<number>>;<br>差异内容：getEmbedding(image: Image): Promise\<Array\<number>>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：type Image = string;<br>差异内容：type Image = string;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：function splitText(text: string, config: SplitConfig): Promise\<Array\<string>>;<br>差异内容：function splitText(text: string, config: SplitConfig): Promise\<Array\<string>>;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：intelligence；<br>API声明：interface SplitConfig<br>差异内容：interface SplitConfig|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：SplitConfig；<br>API声明：size: number;<br>差异内容：size: number;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：SplitConfig；<br>API声明：overlapRatio: number;<br>差异内容：overlapRatio: number;|api/@ohos.data.intelligence.d.ts|
|新增API|NA|类名：global；<br>API声明：declare enum FormType<br>差异内容：declare enum FormType|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：FormType；<br>API声明：TYPE_BIG = 0<br>差异内容：TYPE_BIG = 0|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：FormType；<br>API声明：TYPE_MID = 1<br>差异内容：TYPE_MID = 1|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：FormType；<br>API声明：TYPE_SMALL = 2<br>差异内容：TYPE_SMALL = 2|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：global；<br>API声明：declare struct ContentFormCard<br>差异内容：declare struct ContentFormCard|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：ContentFormCard；<br>API声明：contentFormData: uniformDataStruct.ContentForm;<br>差异内容：contentFormData: uniformDataStruct.ContentForm;|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：ContentFormCard；<br>API声明：@Prop<br>    formType: FormType;<br>差异内容：@Prop<br>    formType: FormType;|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：ContentFormCard；<br>API声明：@Prop<br>    formWidth?: number;<br>差异内容：@Prop<br>    formWidth?: number;|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：ContentFormCard；<br>API声明：@Prop<br>    formHeight?: number;<br>差异内容：@Prop<br>    formHeight?: number;|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：ContentFormCard；<br>API声明：handleOnClick?: Function;<br>差异内容：handleOnClick?: Function;|api/@ohos.data.UdmfComponents.d.ets|
|新增API|NA|类名：UnifiedRecord；<br>API声明：getTypes(): Array\<string>;<br>差异内容：getTypes(): Array\<string>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedRecord；<br>API声明：addEntry(type: string, value: ValueType): void;<br>差异内容：addEntry(type: string, value: ValueType): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedRecord；<br>API声明：getEntry(type: string): ValueType;<br>差异内容：getEntry(type: string): ValueType;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：UnifiedRecord；<br>API声明：getEntries(): Record\<string, ValueType>;<br>差异内容：getEntries(): Record\<string, ValueType>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Intention；<br>API声明：SYSTEM_SHARE = 'SystemShare'<br>差异内容：SYSTEM_SHARE = 'SystemShare'|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Intention；<br>API声明：PICKER = 'Picker'<br>差异内容：PICKER = 'Picker'|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Intention；<br>API声明：MENU = 'Menu'<br>差异内容：MENU = 'Menu'|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：enum Visibility<br>差异内容：enum Visibility|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Visibility；<br>API声明：ALL<br>差异内容：ALL|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：Visibility；<br>API声明：OWN_PROCESS<br>差异内容：OWN_PROCESS|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：enum FileConflictOptions<br>差异内容：enum FileConflictOptions|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：FileConflictOptions；<br>API声明：OVERWRITE<br>差异内容：OVERWRITE|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：FileConflictOptions；<br>API声明：SKIP<br>差异内容：SKIP|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：enum ProgressIndicator<br>差异内容：enum ProgressIndicator|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ProgressIndicator；<br>API声明：NONE<br>差异内容：NONE|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ProgressIndicator；<br>API声明：DEFAULT<br>差异内容：DEFAULT|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：enum ListenerStatus<br>差异内容：enum ListenerStatus|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：FINISHED = 0<br>差异内容：FINISHED = 0|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：PROCESSING<br>差异内容：PROCESSING|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：CANCELED<br>差异内容：CANCELED|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：INNER_ERROR = 200<br>差异内容：INNER_ERROR = 200|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：INVALID_PARAMETERS<br>差异内容：INVALID_PARAMETERS|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：DATA_NOT_FOUND<br>差异内容：DATA_NOT_FOUND|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：SYNC_FAILED<br>差异内容：SYNC_FAILED|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ListenerStatus；<br>API声明：COPY_FILE_FAILED<br>差异内容：COPY_FILE_FAILED|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：interface ProgressInfo<br>差异内容：interface ProgressInfo|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ProgressInfo；<br>API声明：progress: number;<br>差异内容：progress: number;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：ProgressInfo；<br>API声明：status: ListenerStatus;<br>差异内容：status: ListenerStatus;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData \| null) => void;<br>差异内容：type DataProgressListener = (progressInfo: ProgressInfo, data: UnifiedData \| null) => void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：interface GetDataParams<br>差异内容：interface GetDataParams|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：GetDataParams；<br>API声明：progressIndicator: ProgressIndicator;<br>差异内容：progressIndicator: ProgressIndicator;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：GetDataParams；<br>API声明：dataProgressListener: DataProgressListener;<br>差异内容：dataProgressListener: DataProgressListener;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：GetDataParams；<br>API声明：destUri?: string;<br>差异内容：destUri?: string;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：GetDataParams；<br>API声明：fileConflictOptions?: FileConflictOptions;<br>差异内容：fileConflictOptions?: FileConflictOptions;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：GetDataParams；<br>API声明：acceptableInfo?: DataLoadInfo;<br>差异内容：acceptableInfo?: DataLoadInfo;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：interface DataLoadInfo<br>差异内容：interface DataLoadInfo|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：DataLoadInfo；<br>API声明：types?: Set\<string>;<br>差异内容：types?: Set\<string>;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：DataLoadInfo；<br>API声明：recordCount?: number;<br>差异内容：recordCount?: number;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData \| null;<br>差异内容：type DataLoadHandler = (acceptableInfo?: DataLoadInfo) => UnifiedData \| null;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：interface DataLoadParams<br>差异内容：interface DataLoadParams|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：DataLoadParams；<br>API声明：loadHandler: DataLoadHandler;<br>差异内容：loadHandler: DataLoadHandler;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：DataLoadParams；<br>API声明：dataLoadInfo: DataLoadInfo;<br>差异内容：dataLoadInfo: DataLoadInfo;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function convertRecordsToEntries(data: UnifiedData): void;<br>差异内容：function convertRecordsToEntries(data: UnifiedData): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：type DataObserver = (sessionId: string, fields: Array\<string>) => void;<br>差异内容：type DataObserver = (sessionId: string, fields: Array\<string>) => void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：type StatusObserver = (sessionId: string, networkId: string, status: string) => void;<br>差异内容：type StatusObserver = (sessionId: string, networkId: string, status: string) => void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：distributedDataObject；<br>API声明：type ProgressObserver = (sessionId: string, progress: number) => void;<br>差异内容：type ProgressObserver = (sessionId: string, progress: number) => void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：on(type: 'progressChanged', callback: ProgressObserver): void;<br>差异内容：on(type: 'progressChanged', callback: ProgressObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：off(type: 'progressChanged', callback?: ProgressObserver): void;<br>差异内容：off(type: 'progressChanged', callback?: ProgressObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：setAsset(assetKey: string, uri: string): Promise\<void>;<br>差异内容：setAsset(assetKey: string, uri: string): Promise\<void>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：DataObject；<br>API声明：setAssets(assetsKey: string, uris: Array\<string>): Promise\<void>;<br>差异内容：setAssets(assetsKey: string, uris: Array\<string>): Promise\<void>;|api/@ohos.data.distributedDataObject.d.ts|
|新增API|NA|类名：preferences；<br>API声明：enum StorageType<br>差异内容：enum StorageType|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StorageType；<br>API声明：XML = 0<br>差异内容：XML = 0|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StorageType；<br>API声明：GSKV<br>差异内容：GSKV|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Options；<br>API声明：storageType?: StorageType \| null \| undefined;<br>差异内容：storageType?: StorageType \| null \| undefined;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function isStorageTypeSupported(type: StorageType): boolean;<br>差异内容：function isStorageTypeSupported(type: StorageType): boolean;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：rootDir?: string;<br>差异内容：rootDir?: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：vector?: boolean;<br>差异内容：vector?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：tokenizer?: Tokenizer;<br>差异内容：tokenizer?: Tokenizer;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：persist?: boolean;<br>差异内容：persist?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：enableSemanticIndex?: boolean;<br>差异内容：enableSemanticIndex?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum Tokenizer<br>差异内容：enum Tokenizer|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：NONE_TOKENIZER = 0<br>差异内容：NONE_TOKENIZER = 0|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：ICU_TOKENIZER<br>差异内容：ICU_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：CUSTOM_TOKENIZER<br>差异内容：CUSTOM_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface ExceptionMessage<br>差异内容：interface ExceptionMessage|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ExceptionMessage；<br>API声明：code: number;<br>差异内容：code: number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ExceptionMessage；<br>API声明：message: string;<br>差异内容：message: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ExceptionMessage；<br>API声明：sql: string;<br>差异内容：sql: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：interface SqlInfo<br>差异内容：interface SqlInfo|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SqlInfo；<br>API声明：sql: string;<br>差异内容：sql: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：SqlInfo；<br>API声明：args: Array\<ValueType>;<br>差异内容：args: Array\<ValueType>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：DistributedConfig；<br>API声明：asyncDownloadAsset?: boolean;<br>差异内容：asyncDownloadAsset?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：DistributedConfig；<br>API声明：enableCloud?: boolean;<br>差异内容：enableCloud?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum ColumnType<br>差异内容：enum ColumnType|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：NULL<br>差异内容：NULL|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：INTEGER<br>差异内容：INTEGER|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：REAL<br>差异内容：REAL|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：TEXT<br>差异内容：TEXT|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：BLOB<br>差异内容：BLOB|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：ASSET<br>差异内容：ASSET|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：ASSETS<br>差异内容：ASSETS|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：FLOAT_VECTOR<br>差异内容：FLOAT_VECTOR|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ColumnType；<br>API声明：UNLIMITED_INT<br>差异内容：UNLIMITED_INT|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbPredicates；<br>API声明：having(conditions: string, args?: Array\<ValueType>): RdbPredicates;<br>差异内容：having(conditions: string, args?: Array\<ValueType>): RdbPredicates;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;<br>差异内容：getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getColumnTypeSync(columnIdentifier: number \| string): ColumnType;<br>差异内容：getColumnTypeSync(columnIdentifier: number \| string): ColumnType;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;<br>差异内容：getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>差异内容：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>差异内容：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'sqliteErrorOccurred', observer: Callback\<ExceptionMessage>): void;<br>差异内容：on(event: 'sqliteErrorOccurred', observer: Callback\<ExceptionMessage>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：on(event: 'perfStat', observer: Callback\<SqlExecutionInfo>): void;<br>差异内容：on(event: 'perfStat', observer: Callback\<SqlExecutionInfo>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'sqliteErrorOccurred', observer?: Callback\<ExceptionMessage>): void;<br>差异内容：off(event: 'sqliteErrorOccurred', observer?: Callback\<ExceptionMessage>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：off(event: 'perfStat', observer?: Callback\<SqlExecutionInfo>): void;<br>差异内容：off(event: 'perfStat', observer?: Callback\<SqlExecutionInfo>): void;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：rekey(cryptoParam?: CryptoParam): Promise\<void>;<br>差异内容：rekey(cryptoParam?: CryptoParam): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：setLocale(locale: string): Promise\<void>;<br>差异内容：setLocale(locale: string): Promise\<void>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Transaction；<br>API声明：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>差异内容：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Transaction；<br>API声明：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>差异内容：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function isVectorSupported(): boolean;<br>差异内容：function isVectorSupported(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function isTokenizerSupported(tokenizer: Tokenizer): boolean;<br>差异内容：function isTokenizerSupported(tokenizer: Tokenizer): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getInsertSqlInfo(table: string, values: ValuesBucket, conflict?: ConflictResolution): SqlInfo;<br>差异内容：function getInsertSqlInfo(table: string, values: ValuesBucket, conflict?: ConflictResolution): SqlInfo;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getUpdateSqlInfo(predicates: RdbPredicates, values: ValuesBucket, conflict?: ConflictResolution): SqlInfo;<br>差异内容：function getUpdateSqlInfo(predicates: RdbPredicates, values: ValuesBucket, conflict?: ConflictResolution): SqlInfo;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getDeleteSqlInfo(predicates: RdbPredicates): SqlInfo;<br>差异内容：function getDeleteSqlInfo(predicates: RdbPredicates): SqlInfo;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function getQuerySqlInfo(predicates: RdbPredicates, columns?: Array\<string>): SqlInfo;<br>差异内容：function getQuerySqlInfo(predicates: RdbPredicates, columns?: Array\<string>): SqlInfo;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：FILE_URI = 'general.file-uri'<br>差异内容：FILE_URI = 'general.file-uri'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：UniformDataType；<br>API声明：CONTENT_FORM = 'general.content-form'<br>差异内容：CONTENT_FORM = 'general.content-form'|api/@ohos.data.uniformTypeDescriptor.d.ts|
|新增API|NA|类名：sendableRelationalStore；<br>API声明：type NonSendableValues = Array\<relationalStore.ValueType>;<br>差异内容：type NonSendableValues = Array\<relationalStore.ValueType>;|api/@ohos.data.sendableRelationalStore.d.ets|
|新增API|NA|类名：sendableRelationalStore；<br>API声明：function fromSendableValues(values: collections.Array\<ValueType>): NonSendableValues;<br>差异内容：function fromSendableValues(values: collections.Array\<ValueType>): NonSendableValues;|api/@ohos.data.sendableRelationalStore.d.ets|
|新增API|NA|类名：sendableRelationalStore；<br>API声明：function toSendableValues(values: NonSendableValues): collections.Array\<ValueType>;<br>差异内容：function toSendableValues(values: NonSendableValues): collections.Array\<ValueType>;|api/@ohos.data.sendableRelationalStore.d.ets|
|新增API|NA|类名：uniformDataStruct；<br>API声明：interface Form<br>差异内容：interface Form|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：readonly uniformDataType: 'openharmony.form';<br>差异内容：readonly uniformDataType: 'openharmony.form';|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：formId: number;<br>差异内容：formId: number;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：formName: string;<br>差异内容：formName: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：module: string;<br>差异内容：module: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：Form；<br>API声明：details?: Record\<string, number \| string \| Uint8Array>;<br>差异内容：details?: Record\<string, number \| string \| Uint8Array>;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：uniformDataStruct；<br>API声明：interface FileUri<br>差异内容：interface FileUri|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：readonly uniformDataType: 'general.file-uri';<br>差异内容：readonly uniformDataType: 'general.file-uri';|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：oriUri: string;<br>差异内容：oriUri: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：fileType: string;<br>差异内容：fileType: string;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：FileUri；<br>API声明：details?: Record\<string, number \| string \| Uint8Array>;<br>差异内容：details?: Record\<string, number \| string \| Uint8Array>;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：uniformDataStruct；<br>API声明：interface PixelMap<br>差异内容：interface PixelMap|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：readonly uniformDataType: 'openharmony.pixel-map';<br>差异内容：readonly uniformDataType: 'openharmony.pixel-map';|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：pixelMap: image.PixelMap;<br>差异内容：pixelMap: image.PixelMap;|api/@ohos.data.uniformDataStruct.d.ts|
|新增API|NA|类名：PixelMap；<br>API声明：details?: Record\<string, number \| string \| Uint8Array>;<br>差异内容：details?: Record\<string, number \| string \| Uint8Array>;|api/@ohos.data.uniformDataStruct.d.ts|
|起始版本有变化|类名：Intention；<br>API声明：DRAG = 'Drag'<br>差异内容：12|类名：Intention；<br>API声明：DRAG = 'Drag'<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
|起始版本有变化|类名：unifiedDataChannel；<br>API声明：function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>差异内容：12|类名：unifiedDataChannel；<br>API声明：function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
|起始版本有变化|类名：unifiedDataChannel；<br>API声明：function removeAppShareOptions(intention: Intention): void;<br>差异内容：12|类名：unifiedDataChannel；<br>API声明：function removeAppShareOptions(intention: Intention): void;<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.dataShare.d.ts<br>差异内容：ArkData|api/@ohos.data.dataShare.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.intelligence.d.ts<br>差异内容：ArkData|api/@ohos.data.intelligence.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.data.UdmfComponents.d.ets<br>差异内容：ArkData|api/@ohos.data.UdmfComponents.d.ets|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：declare namespace dataSharePredicates<br>差异内容：NA|类名：global；<br>API声明：declare namespace dataSharePredicates<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：dataSharePredicates；<br>API声明：class DataSharePredicates<br>差异内容：NA|类名：dataSharePredicates；<br>API声明：class DataSharePredicates<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：equalTo(field: string, value: ValueType): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：equalTo(field: string, value: ValueType): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：and(): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：and(): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：orderByAsc(field: string): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：orderByAsc(field: string): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：orderByDesc(field: string): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：orderByDesc(field: string): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：limit(total: number, offset: number): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：limit(total: number, offset: number): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：DataSharePredicates；<br>API声明：in(field: string, value: Array\<ValueType>): DataSharePredicates;<br>差异内容：NA|类名：DataSharePredicates；<br>API声明：in(field: string, value: Array\<ValueType>): DataSharePredicates;<br>差异内容：atomicservice|api/@ohos.data.dataSharePredicates.d.ts|
|API从不支持元服务到支持元服务|类名：global；<br>API声明：export type ValueType = number \| string \| boolean;<br>差异内容：NA|类名：global；<br>API声明：export type ValueType = number \| string \| boolean;<br>差异内容：atomicservice|api/@ohos.data.ValuesBucket.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：DataObject；<br>API声明：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：on(type: 'change', callback: (sessionId: string, fields: Array\<string>) => void): void;|类名：DataObject；<br>API声明：on(type: 'change', callback: DataObserver): void;<br>差异内容：on(type: 'change', callback: DataObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：DataObject；<br>API声明：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;<br>差异内容：off(type: 'change', callback?: (sessionId: string, fields: Array\<string>) => void): void;|类名：DataObject；<br>API声明：off(type: 'change', callback?: DataObserver): void;<br>差异内容：off(type: 'change', callback?: DataObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：DataObject；<br>API声明：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：on(type: 'status', callback: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|类名：DataObject；<br>API声明：on(type: 'status', callback: StatusObserver): void;<br>差异内容：on(type: 'status', callback: StatusObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|接口新增同名方法且参数类型与已有的参数类型范围是包含关系|类名：DataObject；<br>API声明：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;<br>差异内容：off(type: 'status', callback?: (sessionId: string, networkId: string, status: 'online' \| 'offline') => void): void;|类名：DataObject；<br>API声明：off(type: 'status', callback?: StatusObserver): void;<br>差异内容：off(type: 'status', callback?: StatusObserver): void;|api/@ohos.data.distributedDataObject.d.ts|
|自定义类型变为接口兼容|类名：unifiedDataChannel；<br>API声明：type Options = {<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        intention?: Intention;<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        key?: string;<br>    };<br>差异内容：type Options = {<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the target Intention<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        intention?: Intention;<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @since 10<br>         */<br>        /**<br>         * Indicates the unique identifier of target UnifiedData<br>         *<br>         * @syscap SystemCapability.DistributedDataManager.UDMF.Core<br>         * @atomicservice<br>         * @since 11<br>         */<br>        key?: string;<br>    };|类名：unifiedDataChannel；<br>API声明：interface Options<br>差异内容：interface Options|api/@ohos.data.unifiedDataChannel.d.ts|
