| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: unifiedDataChannel;<br>API declaration: function convertRecordsToEntries(data: UnifiedData): void;<br>DIfferences: function convertRecordsToEntries(data: UnifiedData): void;|api/@ohos.data.unifiedDataChannel.d.ts|
|New API |NA|Class name: preferences;<br>API declaration: enum StorageType<br>DIfferences: enum StorageType|api/@ohos.data.preferences.d.ts|
|New API |NA|Class name: StorageType;<br>API declaration: XML = 0<br>DIfferences: XML = 0|api/@ohos.data.preferences.d.ts|
|New API |NA|Class name: StorageType;<br>API declaration: GSKV<br>DIfferences: GSKV|api/@ohos.data.preferences.d.ts|
|New API |NA|Class name: Options;<br>API declaration: storageType?: StorageType \| null \| undefined;<br>DIfferences: storageType?: StorageType \| null \| undefined;|api/@ohos.data.preferences.d.ts|
|New API |NA|Class name: preferences;<br>API declaration: function isStorageTypeSupported(type: StorageType): boolean;<br>DIfferences: function isStorageTypeSupported(type: StorageType): boolean;|api/@ohos.data.preferences.d.ts|
|New API |NA|Class name: StoreConfig;<br>API declaration: rootDir?: string;<br>DIfferences: rootDir?: string;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: StoreConfig;<br>API declaration: vector?: boolean;<br>DIfferences: vector?: boolean;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: StoreConfig;<br>API declaration: tokenizer?: Tokenizer;<br>DIfferences: tokenizer?: Tokenizer;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: StoreConfig;<br>API declaration: persist?: boolean;<br>DIfferences: persist?: boolean;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: relationalStore;<br>API declaration: enum Tokenizer<br>DIfferences: enum Tokenizer|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: Tokenizer;<br>API declaration: NONE_TOKENIZER = 0<br>DIfferences: NONE_TOKENIZER = 0|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: Tokenizer;<br>API declaration: ICU_TOKENIZER<br>DIfferences: ICU_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: Tokenizer;<br>API declaration: CUSTOM_TOKENIZER<br>DIfferences: CUSTOM_TOKENIZER|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: DistributedConfig;<br>API declaration: asyncDownloadAsset?: boolean;<br>DIfferences: asyncDownloadAsset?: boolean;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: DistributedConfig;<br>API declaration: enableCloud?: boolean;<br>DIfferences: enableCloud?: boolean;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: relationalStore;<br>API declaration: enum ColumnType<br>DIfferences: enum ColumnType|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: NULL<br>DIfferences: NULL|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: INTEGER<br>DIfferences: INTEGER|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: REAL<br>DIfferences: REAL|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: TEXT<br>DIfferences: TEXT|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: BLOB<br>DIfferences: BLOB|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: ASSET<br>DIfferences: ASSET|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: ASSETS<br>DIfferences: ASSETS|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: FLOAT_VECTOR<br>DIfferences: FLOAT_VECTOR|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ColumnType;<br>API declaration: UNLIMITED_INT<br>DIfferences: UNLIMITED_INT|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ResultSet;<br>API declaration: getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;<br>DIfferences: getColumnType(columnIdentifier: number \| string): Promise\<ColumnType>;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ResultSet;<br>API declaration: getColumnTypeSync(columnIdentifier: number \| string): ColumnType;<br>DIfferences: getColumnTypeSync(columnIdentifier: number \| string): ColumnType;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: ResultSet;<br>API declaration: getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;<br>DIfferences: getRows(maxCount: number, position?: number): Promise\<Array\<ValuesBucket>>;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: RdbStore;<br>API declaration: batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>DIfferences: batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: RdbStore;<br>API declaration: batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>DIfferences: batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: Transaction;<br>API declaration: batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;<br>DIfferences: batchInsertWithConflictResolution(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): Promise\<number>;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: Transaction;<br>API declaration: batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;<br>DIfferences: batchInsertWithConflictResolutionSync(table: string, values: Array\<ValuesBucket>, conflict: ConflictResolution): number;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: relationalStore;<br>API declaration: function isVectorSupported(): boolean;<br>DIfferences: function isVectorSupported(): boolean;|api/@ohos.data.relationalStore.d.ts|
|New API |NA|Class name: relationalStore;<br>API declaration: function isTokenizerSupported(tokenizer: Tokenizer): boolean;<br>DIfferences: function isTokenizerSupported(tokenizer: Tokenizer): boolean;|api/@ohos.data.relationalStore.d.ts|
|Initial version change|Class name: Intention;<br>API declaration: DRAG = 'Drag'<br>DIfferences: 12|Class name: Intention;<br>API declaration: DRAG = 'Drag'<br>DIfferences: 14|api/@ohos.data.unifiedDataChannel.d.ts|
|Initial version change|Class name: unifiedDataChannel;<br>API declaration: function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>DIfferences: 12|Class name: unifiedDataChannel;<br>API declaration: function setAppShareOptions(intention: Intention, shareOptions: ShareOptions): void;<br>DIfferences: 14|api/@ohos.data.unifiedDataChannel.d.ts|
|Initial version change|Class name: unifiedDataChannel;<br>API declaration: function removeAppShareOptions(intention: Intention): void;<br>DIfferences: 12|Class name: unifiedDataChannel;<br>API declaration: function removeAppShareOptions(intention: Intention): void;<br>DIfferences: 14|api/@ohos.data.unifiedDataChannel.d.ts|
