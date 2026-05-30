| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：unifiedDataChannel；<br>API声明：function convertRecordsToEntries(data: UnifiedData): void;<br>差异内容：function convertRecordsToEntries(data: UnifiedData): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|新增API|NA|类名：preferences；<br>API声明：enum StorageType<br>差异内容：enum StorageType|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StorageType；<br>API声明：XML = 0<br>差异内容：XML = 0|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StorageType；<br>API声明：GSKV<br>差异内容：GSKV|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：Options；<br>API声明：storageType?: StorageType \| null \| undefined;<br>差异内容：storageType?: StorageType \| null \| undefined;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：preferences；<br>API声明：function isStorageTypeSupported(type: StorageType): boolean;<br>差异内容：function isStorageTypeSupported(type: StorageType): boolean;|api/@ohos.data.preferences.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：rootDir?: string;<br>差异内容：rootDir?: string;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：vector?: boolean;<br>差异内容：vector?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：tokenizer?: Tokenizer;<br>差异内容：tokenizer?: Tokenizer;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：StoreConfig；<br>API声明：persist?: boolean;<br>差异内容：persist?: boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：enum Tokenizer<br>差异内容：enum Tokenizer|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：NONE_TOKENIZER = 0<br>差异内容：NONE_TOKENIZER = 0|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：ICU_TOKENIZER<br>差异内容：ICU_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Tokenizer；<br>API声明：CUSTOM_TOKENIZER<br>差异内容：CUSTOM_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
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
|新增API|NA|类名：ResultSet；<br>API声明：getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;<br>差异内容：getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getColumnTypeSync(columnIdentifier: number \| string): ColumnType;<br>差异内容：getColumnTypeSync(columnIdentifier: number \| string): ColumnType;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：ResultSet；<br>API声明：getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;<br>差异内容：getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>差异内容：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：RdbStore；<br>API声明：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>差异内容：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Transaction；<br>API声明：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>差异内容：batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：Transaction；<br>API声明：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>差异内容：batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function isVectorSupported(): boolean;<br>差异内容：function isVectorSupported(): boolean;|api/@ohos.data.relationalStore.d.ts|
|新增API|NA|类名：relationalStore；<br>API声明：function isTokenizerSupported(tokenizer: Tokenizer): boolean;<br>差异内容：function isTokenizerSupported(tokenizer: Tokenizer): boolean;|api/@ohos.data.relationalStore.d.ts|
|起始版本有变化|类名：Intention；<br>API声明：DRAG = 'Drag'<br>差异内容：12|类名：Intention；<br>API声明：DRAG = 'Drag'<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
|起始版本有变化|类名：unifiedDataChannel；<br>API声明：function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>差异内容：12|类名：unifiedDataChannel；<br>API声明：function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
|起始版本有变化|类名：unifiedDataChannel；<br>API声明：function removeAppShareOptions(intention: Intention): void;<br>差异内容：12|类名：unifiedDataChannel；<br>API声明：function removeAppShareOptions(intention: Intention): void;<br>差异内容：14|api/@ohos.data.unifiedDataChannel.d.ts|
