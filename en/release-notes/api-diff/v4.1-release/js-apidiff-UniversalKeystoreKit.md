| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API |NA|Class name: global;<br>API declaration: declare namespace huks<br>Differences: declare namespace huks|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function generateKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function generateKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function generateKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;<br>Differences: function generateKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function generateKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;<br>Differences: function generateKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function deleteKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function deleteKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function deleteKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function deleteKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;<br>Differences: function deleteKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function deleteKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;<br>Differences: function deleteKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function importKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function importKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;<br>Differences: function importKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;<br>Differences: function importKeyItem(keyAlias: string, options: HuksOptions): Promise\<void>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;<br>Differences: function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, options: HuksOptions, callback: AsyncCallback\<void>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, options: HuksOptions): Promise\<void>;<br>Differences: function importWrappedKeyItem(keyAlias: string, wrappingKeyAlias: string, options: HuksOptions): Promise\<void>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function exportKey(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function exportKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function exportKey(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function exportKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function exportKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function exportKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;<br>Differences: function exportKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function getKeyProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function getKeyProperties(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function getKeyProperties(keyAlias: string, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function getKeyItemProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function getKeyItemProperties(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function getKeyItemProperties(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;<br>Differences: function getKeyItemProperties(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: function isKeyExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function isKeyExist(keyAlias: string, options: HuksOptions): Promise\<boolean>;<br>Differences: function isKeyExist(keyAlias: string, options: HuksOptions): Promise\<boolean>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: function isKeyItemExist(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function isKeyItemExist(keyAlias: string, options: HuksOptions): Promise\<boolean>;<br>Differences: function isKeyItemExist(keyAlias: string, options: HuksOptions): Promise\<boolean>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function hasKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;<br>Differences: function hasKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function hasKeyItem(keyAlias: string, options: HuksOptions): Promise\<boolean>;<br>Differences: function hasKeyItem(keyAlias: string, options: HuksOptions): Promise\<boolean>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksHandle>): void;<br>Differences: function init(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksHandle>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function init(keyAlias: string, options: HuksOptions): Promise\<HuksHandle>;<br>Differences: function init(keyAlias: string, options: HuksOptions): Promise\<HuksHandle>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksSessionHandle>): void;<br>Differences: function initSession(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksSessionHandle>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function initSession(keyAlias: string, options: HuksOptions): Promise\<HuksSessionHandle>;<br>Differences: function initSession(keyAlias: string, options: HuksOptions): Promise\<HuksSessionHandle>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function update(handle: number, token?: Uint8Array, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function update(handle: number, token?: Uint8Array, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function updateSession(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function updateSession(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function updateSession(handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function updateSession(handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function updateSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise\<HuksReturnResult>;<br>Differences: function updateSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function finish(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function finish(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function finish(handle: number, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function finish(handle: number, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function finishSession(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function finishSession(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function finishSession(handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function finishSession(handle: number, options: HuksOptions, token: Uint8Array, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function finishSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise\<HuksReturnResult>;<br>Differences: function finishSession(handle: number, options: HuksOptions, token?: Uint8Array): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function abort(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;<br>Differences: function abort(handle: number, options: HuksOptions, callback: AsyncCallback\<HuksResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function abort(handle: number, options: HuksOptions): Promise\<HuksResult>;<br>Differences: function abort(handle: number, options: HuksOptions): Promise\<HuksResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function abortSession(handle: number, options: HuksOptions, callback: AsyncCallback\<void>): void;<br>Differences: function abortSession(handle: number, options: HuksOptions, callback: AsyncCallback\<void>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function abortSession(handle: number, options: HuksOptions): Promise\<void>;<br>Differences: function abortSession(handle: number, options: HuksOptions): Promise\<void>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function attestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function attestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function attestKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;<br>Differences: function attestKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function anonAttestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;<br>Differences: function anonAttestKeyItem(keyAlias: string, options: HuksOptions, callback: AsyncCallback\<HuksReturnResult>): void;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function anonAttestKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;<br>Differences: function anonAttestKeyItem(keyAlias: string, options: HuksOptions): Promise\<HuksReturnResult>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: function getSdkVersion(options: HuksOptions): string;<br>Differences: function getSdkVersion(options: HuksOptions): string;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksParam<br>Differences: export interface HuksParam|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksParam;<br>API declaration: tag: HuksTag;<br>Differences: tag: HuksTag;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksParam;<br>API declaration: value: boolean \| number \| bigint \| Uint8Array;<br>Differences: value: boolean \| number \| bigint \| Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksHandle<br>Differences: export interface HuksHandle|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksHandle;<br>API declaration: errorCode: number;<br>Differences: errorCode: number;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksHandle;<br>API declaration: handle: number;<br>Differences: handle: number;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksHandle;<br>API declaration: token?: Uint8Array;<br>Differences: token?: Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksSessionHandle<br>Differences: export interface HuksSessionHandle|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksSessionHandle;<br>API declaration: handle: number;<br>Differences: handle: number;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksSessionHandle;<br>API declaration: challenge?: Uint8Array;<br>Differences: challenge?: Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksOptions<br>Differences: export interface HuksOptions|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksOptions;<br>API declaration: properties?: Array\<HuksParam>;<br>Differences: properties?: Array\<HuksParam>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksOptions;<br>API declaration: inData?: Uint8Array;<br>Differences: inData?: Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksResult<br>Differences: export interface HuksResult|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksResult;<br>API declaration: errorCode: number;<br>Differences: errorCode: number;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksResult;<br>API declaration: outData?: Uint8Array;<br>Differences: outData?: Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksResult;<br>API declaration: properties?: Array\<HuksParam>;<br>Differences: properties?: Array\<HuksParam>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksResult;<br>API declaration: certChains?: Array\<string>;<br>Differences: certChains?: Array\<string>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export interface HuksReturnResult<br>Differences: export interface HuksReturnResult|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksReturnResult;<br>API declaration: outData?: Uint8Array;<br>Differences: outData?: Uint8Array;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksReturnResult;<br>API declaration: properties?: Array\<HuksParam>;<br>Differences: properties?: Array\<HuksParam>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksReturnResult;<br>API declaration: certChains?: Array\<string>;<br>Differences: certChains?: Array\<string>;|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksErrorCode<br>Differences: export enum HuksErrorCode|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_SUCCESS = 0<br>Differences: HUKS_SUCCESS = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_FAILURE = -1<br>Differences: HUKS_FAILURE = -1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_BAD_STATE = -2<br>Differences: HUKS_ERROR_BAD_STATE = -2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_ARGUMENT = -3<br>Differences: HUKS_ERROR_INVALID_ARGUMENT = -3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_NOT_SUPPORTED = -4<br>Differences: HUKS_ERROR_NOT_SUPPORTED = -4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_NO_PERMISSION = -5<br>Differences: HUKS_ERROR_NO_PERMISSION = -5|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INSUFFICIENT_DATA = -6<br>Differences: HUKS_ERROR_INSUFFICIENT_DATA = -6|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_BUFFER_TOO_SMALL = -7<br>Differences: HUKS_ERROR_BUFFER_TOO_SMALL = -7|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INSUFFICIENT_MEMORY = -8<br>Differences: HUKS_ERROR_INSUFFICIENT_MEMORY = -8|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_COMMUNICATION_FAILURE = -9<br>Differences: HUKS_ERROR_COMMUNICATION_FAILURE = -9|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_STORAGE_FAILURE = -10<br>Differences: HUKS_ERROR_STORAGE_FAILURE = -10|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_HARDWARE_FAILURE = -11<br>Differences: HUKS_ERROR_HARDWARE_FAILURE = -11|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_ALREADY_EXISTS = -12<br>Differences: HUKS_ERROR_ALREADY_EXISTS = -12|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_NOT_EXIST = -13<br>Differences: HUKS_ERROR_NOT_EXIST = -13|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_NULL_POINTER = -14<br>Differences: HUKS_ERROR_NULL_POINTER = -14|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_FILE_SIZE_FAIL = -15<br>Differences: HUKS_ERROR_FILE_SIZE_FAIL = -15|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_READ_FILE_FAIL = -16<br>Differences: HUKS_ERROR_READ_FILE_FAIL = -16|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_PUBLIC_KEY = -17<br>Differences: HUKS_ERROR_INVALID_PUBLIC_KEY = -17|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_PRIVATE_KEY = -18<br>Differences: HUKS_ERROR_INVALID_PRIVATE_KEY = -18|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_KEY_INFO = -19<br>Differences: HUKS_ERROR_INVALID_KEY_INFO = -19|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_HASH_NOT_EQUAL = -20<br>Differences: HUKS_ERROR_HASH_NOT_EQUAL = -20|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_MALLOC_FAIL = -21<br>Differences: HUKS_ERROR_MALLOC_FAIL = -21|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_WRITE_FILE_FAIL = -22<br>Differences: HUKS_ERROR_WRITE_FILE_FAIL = -22|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_REMOVE_FILE_FAIL = -23<br>Differences: HUKS_ERROR_REMOVE_FILE_FAIL = -23|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_OPEN_FILE_FAIL = -24<br>Differences: HUKS_ERROR_OPEN_FILE_FAIL = -24|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CLOSE_FILE_FAIL = -25<br>Differences: HUKS_ERROR_CLOSE_FILE_FAIL = -25|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_MAKE_DIR_FAIL = -26<br>Differences: HUKS_ERROR_MAKE_DIR_FAIL = -26|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_KEY_FILE = -27<br>Differences: HUKS_ERROR_INVALID_KEY_FILE = -27|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_IPC_MSG_FAIL = -28<br>Differences: HUKS_ERROR_IPC_MSG_FAIL = -28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_REQUEST_OVERFLOWS = -29<br>Differences: HUKS_ERROR_REQUEST_OVERFLOWS = -29|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_PARAM_NOT_EXIST = -30<br>Differences: HUKS_ERROR_PARAM_NOT_EXIST = -30|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CRYPTO_ENGINE_ERROR = -31<br>Differences: HUKS_ERROR_CRYPTO_ENGINE_ERROR = -31|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_COMMUNICATION_TIMEOUT = -32<br>Differences: HUKS_ERROR_COMMUNICATION_TIMEOUT = -32|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_IPC_INIT_FAIL = -33<br>Differences: HUKS_ERROR_IPC_INIT_FAIL = -33|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_IPC_DLOPEN_FAIL = -34<br>Differences: HUKS_ERROR_IPC_DLOPEN_FAIL = -34|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_EFUSE_READ_FAIL = -35<br>Differences: HUKS_ERROR_EFUSE_READ_FAIL = -35|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_NEW_ROOT_KEY_MATERIAL_EXIST = -36<br>Differences: HUKS_ERROR_NEW_ROOT_KEY_MATERIAL_EXIST = -36|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_UPDATE_ROOT_KEY_MATERIAL_FAIL = -37<br>Differences: HUKS_ERROR_UPDATE_ROOT_KEY_MATERIAL_FAIL = -37|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_VERIFICATION_FAILED = -38<br>Differences: HUKS_ERROR_VERIFICATION_FAILED = -38|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_ALG_FAIL = -100<br>Differences: HUKS_ERROR_CHECK_GET_ALG_FAIL = -100|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_KEY_SIZE_FAIL = -101<br>Differences: HUKS_ERROR_CHECK_GET_KEY_SIZE_FAIL = -101|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_PADDING_FAIL = -102<br>Differences: HUKS_ERROR_CHECK_GET_PADDING_FAIL = -102|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_PURPOSE_FAIL = -103<br>Differences: HUKS_ERROR_CHECK_GET_PURPOSE_FAIL = -103|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_DIGEST_FAIL = -104<br>Differences: HUKS_ERROR_CHECK_GET_DIGEST_FAIL = -104|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_MODE_FAIL = -105<br>Differences: HUKS_ERROR_CHECK_GET_MODE_FAIL = -105|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_NONCE_FAIL = -106<br>Differences: HUKS_ERROR_CHECK_GET_NONCE_FAIL = -106|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_AAD_FAIL = -107<br>Differences: HUKS_ERROR_CHECK_GET_AAD_FAIL = -107|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_IV_FAIL = -108<br>Differences: HUKS_ERROR_CHECK_GET_IV_FAIL = -108|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_AE_TAG_FAIL = -109<br>Differences: HUKS_ERROR_CHECK_GET_AE_TAG_FAIL = -109|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_SALT_FAIL = -110<br>Differences: HUKS_ERROR_CHECK_GET_SALT_FAIL = -110|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_CHECK_GET_ITERATION_FAIL = -111<br>Differences: HUKS_ERROR_CHECK_GET_ITERATION_FAIL = -111|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_ALGORITHM = -112<br>Differences: HUKS_ERROR_INVALID_ALGORITHM = -112|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_KEY_SIZE = -113<br>Differences: HUKS_ERROR_INVALID_KEY_SIZE = -113|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_PADDING = -114<br>Differences: HUKS_ERROR_INVALID_PADDING = -114|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_PURPOSE = -115<br>Differences: HUKS_ERROR_INVALID_PURPOSE = -115|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_MODE = -116<br>Differences: HUKS_ERROR_INVALID_MODE = -116|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_DIGEST = -117<br>Differences: HUKS_ERROR_INVALID_DIGEST = -117|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_SIGNATURE_SIZE = -118<br>Differences: HUKS_ERROR_INVALID_SIGNATURE_SIZE = -118|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_IV = -119<br>Differences: HUKS_ERROR_INVALID_IV = -119|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_AAD = -120<br>Differences: HUKS_ERROR_INVALID_AAD = -120|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_NONCE = -121<br>Differences: HUKS_ERROR_INVALID_NONCE = -121|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_AE_TAG = -122<br>Differences: HUKS_ERROR_INVALID_AE_TAG = -122|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_SALT = -123<br>Differences: HUKS_ERROR_INVALID_SALT = -123|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_ITERATION = -124<br>Differences: HUKS_ERROR_INVALID_ITERATION = -124|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INVALID_OPERATION = -125<br>Differences: HUKS_ERROR_INVALID_OPERATION = -125|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_INTERNAL_ERROR = -999<br>Differences: HUKS_ERROR_INTERNAL_ERROR = -999|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksErrorCode;<br>API declaration: HUKS_ERROR_UNKNOWN_ERROR = -1000<br>Differences: HUKS_ERROR_UNKNOWN_ERROR = -1000|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksExceptionErrCode<br>Differences: export enum HuksExceptionErrCode|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_PERMISSION_FAIL = 201<br>Differences: HUKS_ERR_CODE_PERMISSION_FAIL = 201|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401<br>Differences: HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_NOT_SUPPORTED_API = 801<br>Differences: HUKS_ERR_CODE_NOT_SUPPORTED_API = 801|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001<br>Differences: HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002<br>Differences: HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003<br>Differences: HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004<br>Differences: HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005<br>Differences: HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_CRYPTO_FAIL = 12000006<br>Differences: HUKS_ERR_CODE_CRYPTO_FAIL = 12000006|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007<br>Differences: HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008<br>Differences: HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009<br>Differences: HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_SESSION_LIMIT = 12000010<br>Differences: HUKS_ERR_CODE_SESSION_LIMIT = 12000010|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011<br>Differences: HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012<br>Differences: HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013<br>Differences: HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014<br>Differences: HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015<br>Differences: HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksExceptionErrCode;<br>API declaration: HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016<br>Differences: HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyPurpose<br>Differences: export enum HuksKeyPurpose|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_ENCRYPT = 1<br>Differences: HUKS_KEY_PURPOSE_ENCRYPT = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_DECRYPT = 2<br>Differences: HUKS_KEY_PURPOSE_DECRYPT = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_SIGN = 4<br>Differences: HUKS_KEY_PURPOSE_SIGN = 4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_VERIFY = 8<br>Differences: HUKS_KEY_PURPOSE_VERIFY = 8|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_DERIVE = 16<br>Differences: HUKS_KEY_PURPOSE_DERIVE = 16|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_WRAP = 32<br>Differences: HUKS_KEY_PURPOSE_WRAP = 32|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_UNWRAP = 64<br>Differences: HUKS_KEY_PURPOSE_UNWRAP = 64|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_MAC = 128<br>Differences: HUKS_KEY_PURPOSE_MAC = 128|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPurpose;<br>API declaration: HUKS_KEY_PURPOSE_AGREE = 256<br>Differences: HUKS_KEY_PURPOSE_AGREE = 256|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyDigest<br>Differences: export enum HuksKeyDigest|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_NONE = 0<br>Differences: HUKS_DIGEST_NONE = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_MD5 = 1<br>Differences: HUKS_DIGEST_MD5 = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SM3 = 2<br>Differences: HUKS_DIGEST_SM3 = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SHA1 = 10<br>Differences: HUKS_DIGEST_SHA1 = 10|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SHA224 = 11<br>Differences: HUKS_DIGEST_SHA224 = 11|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SHA256 = 12<br>Differences: HUKS_DIGEST_SHA256 = 12|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SHA384 = 13<br>Differences: HUKS_DIGEST_SHA384 = 13|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyDigest;<br>API declaration: HUKS_DIGEST_SHA512 = 14<br>Differences: HUKS_DIGEST_SHA512 = 14|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyPadding<br>Differences: export enum HuksKeyPadding|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_NONE = 0<br>Differences: HUKS_PADDING_NONE = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_OAEP = 1<br>Differences: HUKS_PADDING_OAEP = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_PSS = 2<br>Differences: HUKS_PADDING_PSS = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_PKCS1_V1_5 = 3<br>Differences: HUKS_PADDING_PKCS1_V1_5 = 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_PKCS5 = 4<br>Differences: HUKS_PADDING_PKCS5 = 4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyPadding;<br>API declaration: HUKS_PADDING_PKCS7 = 5<br>Differences: HUKS_PADDING_PKCS7 = 5|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksCipherMode<br>Differences: export enum HuksCipherMode|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_ECB = 1<br>Differences: HUKS_MODE_ECB = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_CBC = 2<br>Differences: HUKS_MODE_CBC = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_CTR = 3<br>Differences: HUKS_MODE_CTR = 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_OFB = 4<br>Differences: HUKS_MODE_OFB = 4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_CCM = 31<br>Differences: HUKS_MODE_CCM = 31|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksCipherMode;<br>API declaration: HUKS_MODE_GCM = 32<br>Differences: HUKS_MODE_GCM = 32|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeySize<br>Differences: export enum HuksKeySize|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_512 = 512<br>Differences: HUKS_RSA_KEY_SIZE_512 = 512|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_768 = 768<br>Differences: HUKS_RSA_KEY_SIZE_768 = 768|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_1024 = 1024<br>Differences: HUKS_RSA_KEY_SIZE_1024 = 1024|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_2048 = 2048<br>Differences: HUKS_RSA_KEY_SIZE_2048 = 2048|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_3072 = 3072<br>Differences: HUKS_RSA_KEY_SIZE_3072 = 3072|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_RSA_KEY_SIZE_4096 = 4096<br>Differences: HUKS_RSA_KEY_SIZE_4096 = 4096|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_ECC_KEY_SIZE_224 = 224<br>Differences: HUKS_ECC_KEY_SIZE_224 = 224|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_ECC_KEY_SIZE_256 = 256<br>Differences: HUKS_ECC_KEY_SIZE_256 = 256|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_ECC_KEY_SIZE_384 = 384<br>Differences: HUKS_ECC_KEY_SIZE_384 = 384|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_ECC_KEY_SIZE_521 = 521<br>Differences: HUKS_ECC_KEY_SIZE_521 = 521|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_AES_KEY_SIZE_128 = 128<br>Differences: HUKS_AES_KEY_SIZE_128 = 128|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_AES_KEY_SIZE_192 = 192<br>Differences: HUKS_AES_KEY_SIZE_192 = 192|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_AES_KEY_SIZE_256 = 256<br>Differences: HUKS_AES_KEY_SIZE_256 = 256|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_AES_KEY_SIZE_512 = 512<br>Differences: HUKS_AES_KEY_SIZE_512 = 512|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_CURVE25519_KEY_SIZE_256 = 256<br>Differences: HUKS_CURVE25519_KEY_SIZE_256 = 256|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_DH_KEY_SIZE_2048 = 2048<br>Differences: HUKS_DH_KEY_SIZE_2048 = 2048|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_DH_KEY_SIZE_3072 = 3072<br>Differences: HUKS_DH_KEY_SIZE_3072 = 3072|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_DH_KEY_SIZE_4096 = 4096<br>Differences: HUKS_DH_KEY_SIZE_4096 = 4096|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_SM2_KEY_SIZE_256 = 256<br>Differences: HUKS_SM2_KEY_SIZE_256 = 256|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeySize;<br>API declaration: HUKS_SM4_KEY_SIZE_128 = 128<br>Differences: HUKS_SM4_KEY_SIZE_128 = 128|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyAlg<br>Differences: export enum HuksKeyAlg|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_RSA = 1<br>Differences: HUKS_ALG_RSA = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_ECC = 2<br>Differences: HUKS_ALG_ECC = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_DSA = 3<br>Differences: HUKS_ALG_DSA = 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_AES = 20<br>Differences: HUKS_ALG_AES = 20|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_HMAC = 50<br>Differences: HUKS_ALG_HMAC = 50|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_HKDF = 51<br>Differences: HUKS_ALG_HKDF = 51|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_PBKDF2 = 52<br>Differences: HUKS_ALG_PBKDF2 = 52|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_ECDH = 100<br>Differences: HUKS_ALG_ECDH = 100|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_X25519 = 101<br>Differences: HUKS_ALG_X25519 = 101|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_ED25519 = 102<br>Differences: HUKS_ALG_ED25519 = 102|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_DH = 103<br>Differences: HUKS_ALG_DH = 103|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_SM2 = 150<br>Differences: HUKS_ALG_SM2 = 150|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_SM3 = 151<br>Differences: HUKS_ALG_SM3 = 151|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyAlg;<br>API declaration: HUKS_ALG_SM4 = 152<br>Differences: HUKS_ALG_SM4 = 152|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksUnwrapSuite<br>Differences: export enum HuksUnwrapSuite|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksUnwrapSuite;<br>API declaration: HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1<br>Differences: HUKS_UNWRAP_SUITE_X25519_AES_256_GCM_NOPADDING = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksUnwrapSuite;<br>API declaration: HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2<br>Differences: HUKS_UNWRAP_SUITE_ECDH_AES_256_GCM_NOPADDING = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyGenerateType<br>Differences: export enum HuksKeyGenerateType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyGenerateType;<br>API declaration: HUKS_KEY_GENERATE_TYPE_DEFAULT = 0<br>Differences: HUKS_KEY_GENERATE_TYPE_DEFAULT = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyGenerateType;<br>API declaration: HUKS_KEY_GENERATE_TYPE_DERIVE = 1<br>Differences: HUKS_KEY_GENERATE_TYPE_DERIVE = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyGenerateType;<br>API declaration: HUKS_KEY_GENERATE_TYPE_AGREE = 2<br>Differences: HUKS_KEY_GENERATE_TYPE_AGREE = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyFlag<br>Differences: export enum HuksKeyFlag|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyFlag;<br>API declaration: HUKS_KEY_FLAG_IMPORT_KEY = 1<br>Differences: HUKS_KEY_FLAG_IMPORT_KEY = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyFlag;<br>API declaration: HUKS_KEY_FLAG_GENERATE_KEY = 2<br>Differences: HUKS_KEY_FLAG_GENERATE_KEY = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyFlag;<br>API declaration: HUKS_KEY_FLAG_AGREE_KEY = 3<br>Differences: HUKS_KEY_FLAG_AGREE_KEY = 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyFlag;<br>API declaration: HUKS_KEY_FLAG_DERIVE_KEY = 4<br>Differences: HUKS_KEY_FLAG_DERIVE_KEY = 4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksKeyStorageType<br>Differences: export enum HuksKeyStorageType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyStorageType;<br>API declaration: HUKS_STORAGE_TEMP = 0<br>Differences: HUKS_STORAGE_TEMP = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyStorageType;<br>API declaration: HUKS_STORAGE_PERSISTENT = 1<br>Differences: HUKS_STORAGE_PERSISTENT = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyStorageType;<br>API declaration: HUKS_STORAGE_ONLY_USED_IN_HUKS = 2<br>Differences: HUKS_STORAGE_ONLY_USED_IN_HUKS = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksKeyStorageType;<br>API declaration: HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3<br>Differences: HUKS_STORAGE_KEY_EXPORT_ALLOWED = 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksImportKeyType<br>Differences: export enum HuksImportKeyType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksImportKeyType;<br>API declaration: HUKS_KEY_TYPE_PUBLIC_KEY = 0<br>Differences: HUKS_KEY_TYPE_PUBLIC_KEY = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksImportKeyType;<br>API declaration: HUKS_KEY_TYPE_PRIVATE_KEY = 1<br>Differences: HUKS_KEY_TYPE_PRIVATE_KEY = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksImportKeyType;<br>API declaration: HUKS_KEY_TYPE_KEY_PAIR = 2<br>Differences: HUKS_KEY_TYPE_KEY_PAIR = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksRsaPssSaltLenType<br>Differences: export enum HuksRsaPssSaltLenType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksRsaPssSaltLenType;<br>API declaration: HUKS_RSA_PSS_SALT_LEN_DIGEST = 0<br>Differences: HUKS_RSA_PSS_SALT_LEN_DIGEST = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksRsaPssSaltLenType;<br>API declaration: HUKS_RSA_PSS_SALT_LEN_MAX = 1<br>Differences: HUKS_RSA_PSS_SALT_LEN_MAX = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksUserAuthType<br>Differences: export enum HuksUserAuthType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksUserAuthType;<br>API declaration: HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 \<\< 0<br>Differences: HUKS_USER_AUTH_TYPE_FINGERPRINT = 1 \<\< 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksUserAuthType;<br>API declaration: HUKS_USER_AUTH_TYPE_FACE = 1 \<\< 1<br>Differences: HUKS_USER_AUTH_TYPE_FACE = 1 \<\< 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksUserAuthType;<br>API declaration: HUKS_USER_AUTH_TYPE_PIN = 1 \<\< 2<br>Differences: HUKS_USER_AUTH_TYPE_PIN = 1 \<\< 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksAuthAccessType<br>Differences: export enum HuksAuthAccessType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthAccessType;<br>API declaration: HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 \<\< 0<br>Differences: HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD = 1 \<\< 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthAccessType;<br>API declaration: HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 \<\< 1<br>Differences: HUKS_AUTH_ACCESS_INVALID_NEW_BIO_ENROLL = 1 \<\< 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthAccessType;<br>API declaration: HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 \<\< 2<br>Differences: HUKS_AUTH_ACCESS_ALWAYS_VALID = 1 \<\< 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksAuthStorageLevel<br>Differences: export enum HuksAuthStorageLevel|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthStorageLevel;<br>API declaration: HUKS_AUTH_STORAGE_LEVEL_DE = 0<br>Differences: HUKS_AUTH_STORAGE_LEVEL_DE = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthStorageLevel;<br>API declaration: HUKS_AUTH_STORAGE_LEVEL_CE = 1<br>Differences: HUKS_AUTH_STORAGE_LEVEL_CE = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksAuthStorageLevel;<br>API declaration: HUKS_AUTH_STORAGE_LEVEL_ECE = 2<br>Differences: HUKS_AUTH_STORAGE_LEVEL_ECE = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksChallengeType<br>Differences: export enum HuksChallengeType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengeType;<br>API declaration: HUKS_CHALLENGE_TYPE_NORMAL = 0<br>Differences: HUKS_CHALLENGE_TYPE_NORMAL = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengeType;<br>API declaration: HUKS_CHALLENGE_TYPE_CUSTOM = 1<br>Differences: HUKS_CHALLENGE_TYPE_CUSTOM = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengeType;<br>API declaration: HUKS_CHALLENGE_TYPE_NONE = 2<br>Differences: HUKS_CHALLENGE_TYPE_NONE = 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksChallengePosition<br>Differences: export enum HuksChallengePosition|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengePosition;<br>API declaration: HUKS_CHALLENGE_POS_0 = 0<br>Differences: HUKS_CHALLENGE_POS_0 = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengePosition;<br>API declaration: HUKS_CHALLENGE_POS_1<br>Differences: HUKS_CHALLENGE_POS_1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengePosition;<br>API declaration: HUKS_CHALLENGE_POS_2<br>Differences: HUKS_CHALLENGE_POS_2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksChallengePosition;<br>API declaration: HUKS_CHALLENGE_POS_3<br>Differences: HUKS_CHALLENGE_POS_3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksSecureSignType<br>Differences: export enum HuksSecureSignType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksSecureSignType;<br>API declaration: HUKS_SECURE_SIGN_WITH_AUTHINFO = 1<br>Differences: HUKS_SECURE_SIGN_WITH_AUTHINFO = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksSendType<br>Differences: export enum HuksSendType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksSendType;<br>API declaration: HUKS_SEND_TYPE_ASYNC = 0<br>Differences: HUKS_SEND_TYPE_ASYNC = 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksSendType;<br>API declaration: HUKS_SEND_TYPE_SYNC = 1<br>Differences: HUKS_SEND_TYPE_SYNC = 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksTagType<br>Differences: export enum HuksTagType|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_INVALID = 0 \<\< 28<br>Differences: HUKS_TAG_TYPE_INVALID = 0 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_INT = 1 \<\< 28<br>Differences: HUKS_TAG_TYPE_INT = 1 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_UINT = 2 \<\< 28<br>Differences: HUKS_TAG_TYPE_UINT = 2 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_ULONG = 3 \<\< 28<br>Differences: HUKS_TAG_TYPE_ULONG = 3 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_BOOL = 4 \<\< 28<br>Differences: HUKS_TAG_TYPE_BOOL = 4 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTagType;<br>API declaration: HUKS_TAG_TYPE_BYTES = 5 \<\< 28<br>Differences: HUKS_TAG_TYPE_BYTES = 5 \<\< 28|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: huks;<br>API declaration: export enum HuksTag<br>Differences: export enum HuksTag|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_INVALID = HuksTagType.HUKS_TAG_TYPE_INVALID \| 0<br>Differences: HUKS_TAG_INVALID = HuksTagType.HUKS_TAG_TYPE_INVALID \| 0|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ALGORITHM = HuksTagType.HUKS_TAG_TYPE_UINT \| 1<br>Differences: HUKS_TAG_ALGORITHM = HuksTagType.HUKS_TAG_TYPE_UINT \| 1|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT \| 2<br>Differences: HUKS_TAG_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT \| 2|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT \| 3<br>Differences: HUKS_TAG_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT \| 3|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DIGEST = HuksTagType.HUKS_TAG_TYPE_UINT \| 4<br>Differences: HUKS_TAG_DIGEST = HuksTagType.HUKS_TAG_TYPE_UINT \| 4|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PADDING = HuksTagType.HUKS_TAG_TYPE_UINT \| 5<br>Differences: HUKS_TAG_PADDING = HuksTagType.HUKS_TAG_TYPE_UINT \| 5|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_BLOCK_MODE = HuksTagType.HUKS_TAG_TYPE_UINT \| 6<br>Differences: HUKS_TAG_BLOCK_MODE = HuksTagType.HUKS_TAG_TYPE_UINT \| 6|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 7<br>Differences: HUKS_TAG_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 7|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ASSOCIATED_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 8<br>Differences: HUKS_TAG_ASSOCIATED_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 8|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_NONCE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 9<br>Differences: HUKS_TAG_NONCE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 9|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IV = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10<br>Differences: HUKS_TAG_IV = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 11<br>Differences: HUKS_TAG_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 11|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_SALT = HuksTagType.HUKS_TAG_TYPE_BYTES \| 12<br>Differences: HUKS_TAG_SALT = HuksTagType.HUKS_TAG_TYPE_BYTES \| 12|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PWD = HuksTagType.HUKS_TAG_TYPE_BYTES \| 13<br>Differences: HUKS_TAG_PWD = HuksTagType.HUKS_TAG_TYPE_BYTES \| 13|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ITERATION = HuksTagType.HUKS_TAG_TYPE_UINT \| 14<br>Differences: HUKS_TAG_ITERATION = HuksTagType.HUKS_TAG_TYPE_UINT \| 14|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_GENERATE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 15<br>Differences: HUKS_TAG_KEY_GENERATE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 15|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DERIVE_MAIN_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 16<br>Differences: HUKS_TAG_DERIVE_MAIN_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 16|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DERIVE_FACTOR = HuksTagType.HUKS_TAG_TYPE_BYTES \| 17<br>Differences: HUKS_TAG_DERIVE_FACTOR = HuksTagType.HUKS_TAG_TYPE_BYTES \| 17|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DERIVE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT \| 18<br>Differences: HUKS_TAG_DERIVE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT \| 18|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AGREE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT \| 19<br>Differences: HUKS_TAG_AGREE_ALG = HuksTagType.HUKS_TAG_TYPE_UINT \| 19|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 20<br>Differences: HUKS_TAG_AGREE_PUBLIC_KEY_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 20|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 21<br>Differences: HUKS_TAG_AGREE_PRIVATE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 21|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AGREE_PUBLIC_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 22<br>Differences: HUKS_TAG_AGREE_PUBLIC_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 22|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 23<br>Differences: HUKS_TAG_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 23|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DERIVE_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT \| 24<br>Differences: HUKS_TAG_DERIVE_KEY_SIZE = HuksTagType.HUKS_TAG_TYPE_UINT \| 24|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IMPORT_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 25<br>Differences: HUKS_TAG_IMPORT_KEY_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 25|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_UNWRAP_ALGORITHM_SUITE = HuksTagType.HUKS_TAG_TYPE_UINT \| 26<br>Differences: HUKS_TAG_UNWRAP_ALGORITHM_SUITE = HuksTagType.HUKS_TAG_TYPE_UINT \| 26|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 29<br>Differences: HUKS_TAG_DERIVED_AGREED_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 29|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 30<br>Differences: HUKS_TAG_RSA_PSS_SALT_LEN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 30|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ACTIVE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 201<br>Differences: HUKS_TAG_ACTIVE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 201|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ORIGINATION_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 202<br>Differences: HUKS_TAG_ORIGINATION_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 202|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_USAGE_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 203<br>Differences: HUKS_TAG_USAGE_EXPIRE_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 203|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_CREATION_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 204<br>Differences: HUKS_TAG_CREATION_DATETIME = HuksTagType.HUKS_TAG_TYPE_ULONG \| 204|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ALL_USERS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 301<br>Differences: HUKS_TAG_ALL_USERS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 301|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_USER_ID = HuksTagType.HUKS_TAG_TYPE_UINT \| 302<br>Differences: HUKS_TAG_USER_ID = HuksTagType.HUKS_TAG_TYPE_UINT \| 302|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_NO_AUTH_REQUIRED = HuksTagType.HUKS_TAG_TYPE_BOOL \| 303<br>Differences: HUKS_TAG_NO_AUTH_REQUIRED = HuksTagType.HUKS_TAG_TYPE_BOOL \| 303|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_USER_AUTH_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 304<br>Differences: HUKS_TAG_USER_AUTH_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 304|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AUTH_TIMEOUT = HuksTagType.HUKS_TAG_TYPE_UINT \| 305<br>Differences: HUKS_TAG_AUTH_TIMEOUT = HuksTagType.HUKS_TAG_TYPE_UINT \| 305|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AUTH_TOKEN = HuksTagType.HUKS_TAG_TYPE_BYTES \| 306<br>Differences: HUKS_TAG_AUTH_TOKEN = HuksTagType.HUKS_TAG_TYPE_BYTES \| 306|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_AUTH_ACCESS_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 307<br>Differences: HUKS_TAG_KEY_AUTH_ACCESS_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 307|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_SECURE_SIGN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 308<br>Differences: HUKS_TAG_KEY_SECURE_SIGN_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 308|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_CHALLENGE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 309<br>Differences: HUKS_TAG_CHALLENGE_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 309|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_CHALLENGE_POS = HuksTagType.HUKS_TAG_TYPE_UINT \| 310<br>Differences: HUKS_TAG_CHALLENGE_POS = HuksTagType.HUKS_TAG_TYPE_UINT \| 310|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_AUTH_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT \| 311<br>Differences: HUKS_TAG_KEY_AUTH_PURPOSE = HuksTagType.HUKS_TAG_TYPE_UINT \| 311|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AUTH_STORAGE_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT \| 316<br>Differences: HUKS_TAG_AUTH_STORAGE_LEVEL = HuksTagType.HUKS_TAG_TYPE_UINT \| 316|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_CHALLENGE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 501<br>Differences: HUKS_TAG_ATTESTATION_CHALLENGE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 501|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_APPLICATION_ID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 502<br>Differences: HUKS_TAG_ATTESTATION_APPLICATION_ID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 502|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_BRAND = HuksTagType.HUKS_TAG_TYPE_BYTES \| 503<br>Differences: HUKS_TAG_ATTESTATION_ID_BRAND = HuksTagType.HUKS_TAG_TYPE_BYTES \| 503|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_DEVICE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 504<br>Differences: HUKS_TAG_ATTESTATION_ID_DEVICE = HuksTagType.HUKS_TAG_TYPE_BYTES \| 504|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_PRODUCT = HuksTagType.HUKS_TAG_TYPE_BYTES \| 505<br>Differences: HUKS_TAG_ATTESTATION_ID_PRODUCT = HuksTagType.HUKS_TAG_TYPE_BYTES \| 505|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_SERIAL = HuksTagType.HUKS_TAG_TYPE_BYTES \| 506<br>Differences: HUKS_TAG_ATTESTATION_ID_SERIAL = HuksTagType.HUKS_TAG_TYPE_BYTES \| 506|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_IMEI = HuksTagType.HUKS_TAG_TYPE_BYTES \| 507<br>Differences: HUKS_TAG_ATTESTATION_ID_IMEI = HuksTagType.HUKS_TAG_TYPE_BYTES \| 507|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_MEID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 508<br>Differences: HUKS_TAG_ATTESTATION_ID_MEID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 508|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_MANUFACTURER = HuksTagType.HUKS_TAG_TYPE_BYTES \| 509<br>Differences: HUKS_TAG_ATTESTATION_ID_MANUFACTURER = HuksTagType.HUKS_TAG_TYPE_BYTES \| 509|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_MODEL = HuksTagType.HUKS_TAG_TYPE_BYTES \| 510<br>Differences: HUKS_TAG_ATTESTATION_ID_MODEL = HuksTagType.HUKS_TAG_TYPE_BYTES \| 510|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 511<br>Differences: HUKS_TAG_ATTESTATION_ID_ALIAS = HuksTagType.HUKS_TAG_TYPE_BYTES \| 511|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_SOCID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 512<br>Differences: HUKS_TAG_ATTESTATION_ID_SOCID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 512|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_UDID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 513<br>Differences: HUKS_TAG_ATTESTATION_ID_UDID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 513|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 514<br>Differences: HUKS_TAG_ATTESTATION_ID_SEC_LEVEL_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 514|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ATTESTATION_ID_VERSION_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 515<br>Differences: HUKS_TAG_ATTESTATION_ID_VERSION_INFO = HuksTagType.HUKS_TAG_TYPE_BYTES \| 515|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1001<br>Differences: HUKS_TAG_IS_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1001|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 1002<br>Differences: HUKS_TAG_KEY_STORAGE_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 1002|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IS_ALLOWED_WRAP = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1003<br>Differences: HUKS_TAG_IS_ALLOWED_WRAP = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1003|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_WRAP_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 1004<br>Differences: HUKS_TAG_KEY_WRAP_TYPE = HuksTagType.HUKS_TAG_TYPE_UINT \| 1004|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_AUTH_ID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 1005<br>Differences: HUKS_TAG_KEY_AUTH_ID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 1005|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_ROLE = HuksTagType.HUKS_TAG_TYPE_UINT \| 1006<br>Differences: HUKS_TAG_KEY_ROLE = HuksTagType.HUKS_TAG_TYPE_UINT \| 1006|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 1007<br>Differences: HUKS_TAG_KEY_FLAG = HuksTagType.HUKS_TAG_TYPE_UINT \| 1007|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IS_ASYNCHRONIZED = HuksTagType.HUKS_TAG_TYPE_UINT \| 1008<br>Differences: HUKS_TAG_IS_ASYNCHRONIZED = HuksTagType.HUKS_TAG_TYPE_UINT \| 1008|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_SECURE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1009<br>Differences: HUKS_TAG_SECURE_KEY_ALIAS = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1009|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_SECURE_KEY_UUID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 1010<br>Differences: HUKS_TAG_SECURE_KEY_UUID = HuksTagType.HUKS_TAG_TYPE_BYTES \| 1010|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_DOMAIN = HuksTagType.HUKS_TAG_TYPE_UINT \| 1011<br>Differences: HUKS_TAG_KEY_DOMAIN = HuksTagType.HUKS_TAG_TYPE_UINT \| 1011|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IS_DEVICE_PASSWORD_SET = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1012<br>Differences: HUKS_TAG_IS_DEVICE_PASSWORD_SET = HuksTagType.HUKS_TAG_TYPE_BOOL \| 1012|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PROCESS_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10001<br>Differences: HUKS_TAG_PROCESS_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10001|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PACKAGE_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10002<br>Differences: HUKS_TAG_PACKAGE_NAME = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10002|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ACCESS_TIME = HuksTagType.HUKS_TAG_TYPE_UINT \| 10003<br>Differences: HUKS_TAG_ACCESS_TIME = HuksTagType.HUKS_TAG_TYPE_UINT \| 10003|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_USES_TIME = HuksTagType.HUKS_TAG_TYPE_UINT \| 10004<br>Differences: HUKS_TAG_USES_TIME = HuksTagType.HUKS_TAG_TYPE_UINT \| 10004|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_CRYPTO_CTX = HuksTagType.HUKS_TAG_TYPE_ULONG \| 10005<br>Differences: HUKS_TAG_CRYPTO_CTX = HuksTagType.HUKS_TAG_TYPE_ULONG \| 10005|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10006<br>Differences: HUKS_TAG_KEY = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10006|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_KEY_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT \| 10007<br>Differences: HUKS_TAG_KEY_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT \| 10007|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_PAYLOAD_LEN = HuksTagType.HUKS_TAG_TYPE_UINT \| 10008<br>Differences: HUKS_TAG_PAYLOAD_LEN = HuksTagType.HUKS_TAG_TYPE_UINT \| 10008|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_AE_TAG = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10009<br>Differences: HUKS_TAG_AE_TAG = HuksTagType.HUKS_TAG_TYPE_BYTES \| 10009|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_IS_KEY_HANDLE = HuksTagType.HUKS_TAG_TYPE_ULONG \| 10010<br>Differences: HUKS_TAG_IS_KEY_HANDLE = HuksTagType.HUKS_TAG_TYPE_ULONG \| 10010|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_OS_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT \| 10101<br>Differences: HUKS_TAG_OS_VERSION = HuksTagType.HUKS_TAG_TYPE_UINT \| 10101|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_OS_PATCHLEVEL = HuksTagType.HUKS_TAG_TYPE_UINT \| 10102<br>Differences: HUKS_TAG_OS_PATCHLEVEL = HuksTagType.HUKS_TAG_TYPE_UINT \| 10102|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_SYMMETRIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20001<br>Differences: HUKS_TAG_SYMMETRIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20001|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20002<br>Differences: HUKS_TAG_ASYMMETRIC_PUBLIC_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20002|api/@ohos.security.huks.d.ts|
|New API |NA|Class name: HuksTag;<br>API declaration: HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20003<br>Differences: HUKS_TAG_ASYMMETRIC_PRIVATE_KEY_DATA = HuksTagType.HUKS_TAG_TYPE_BYTES \| 20003|api/@ohos.security.huks.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.security.huks.d.ts<br>Differences: UniversalKeystoreKit|api/@ohos.security.huks.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.UniversalKeystoreKit.d.ts<br>Differences: UniversalKeystoreKit|kits/@kit.UniversalKeystoreKit.d.ts|
