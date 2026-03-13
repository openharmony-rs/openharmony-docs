| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New API|NA|Class name: global;<br>API declaration: declare namespace cryptoFramework<br>Differences: declare namespace cryptoFramework|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum Result<br>Differences: enum Result|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Result;<br>API declaration: INVALID_PARAMS = 401<br>Differences: INVALID_PARAMS = 401|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Result;<br>API declaration: NOT_SUPPORT = 801<br>Differences: NOT_SUPPORT = 801|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Result;<br>API declaration: ERR_OUT_OF_MEMORY = 17620001<br>Differences: ERR_OUT_OF_MEMORY = 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Result;<br>API declaration: ERR_RUNTIME_ERROR = 17620002<br>Differences: ERR_RUNTIME_ERROR = 17620002|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Result;<br>API declaration: ERR_CRYPTO_OPERATION = 17630001<br>Differences: ERR_CRYPTO_OPERATION = 17630001|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DataBlob<br>Differences: interface DataBlob|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DataBlob;<br>API declaration: data: Uint8Array;<br>Differences: data: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ParamsSpec<br>Differences: interface ParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ParamsSpec;<br>API declaration: algName: string;<br>Differences: algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface IvParamsSpec<br>Differences: interface IvParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: IvParamsSpec;<br>API declaration: iv: DataBlob;<br>Differences: iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface GcmParamsSpec<br>Differences: interface GcmParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: GcmParamsSpec;<br>API declaration: iv: DataBlob;<br>Differences: iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: GcmParamsSpec;<br>API declaration: aad: DataBlob;<br>Differences: aad: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: GcmParamsSpec;<br>API declaration: authTag: DataBlob;<br>Differences: authTag: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface CcmParamsSpec<br>Differences: interface CcmParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CcmParamsSpec;<br>API declaration: iv: DataBlob;<br>Differences: iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CcmParamsSpec;<br>API declaration: aad: DataBlob;<br>Differences: aad: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CcmParamsSpec;<br>API declaration: authTag: DataBlob;<br>Differences: authTag: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum CryptoMode<br>Differences: enum CryptoMode|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CryptoMode;<br>API declaration: ENCRYPT_MODE = 0<br>Differences: ENCRYPT_MODE = 0|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CryptoMode;<br>API declaration: DECRYPT_MODE = 1<br>Differences: DECRYPT_MODE = 1|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Key<br>Differences: interface Key|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Key;<br>API declaration: getEncoded(): DataBlob;<br>Differences: getEncoded(): DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Key;<br>API declaration: readonly format: string;<br>Differences: readonly format: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Key;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface SymKey<br>Differences: interface SymKey|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKey;<br>API declaration: clearMem(): void;<br>Differences: clearMem(): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface PriKey<br>Differences: interface PriKey|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PriKey;<br>API declaration: clearMem(): void;<br>Differences: clearMem(): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PriKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>Differences: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface PubKey<br>Differences: interface PubKey|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PubKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>Differences: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface KeyPair<br>Differences: interface KeyPair|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KeyPair;<br>API declaration: readonly priKey: PriKey;<br>Differences: readonly priKey: PriKey;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KeyPair;<br>API declaration: readonly pubKey: PubKey;<br>Differences: readonly pubKey: PubKey;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Random<br>Differences: interface Random|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Random;<br>API declaration: generateRandom(len: number, callback: AsyncCallback\<DataBlob>): void;<br>Differences: generateRandom(len: number, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Random;<br>API declaration: generateRandom(len: number): Promise\<DataBlob>;<br>Differences: generateRandom(len: number): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Random;<br>API declaration: generateRandomSync(len: number): DataBlob;<br>Differences: generateRandomSync(len: number): DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Random;<br>API declaration: setSeed(seed: DataBlob): void;<br>Differences: setSeed(seed: DataBlob): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Random;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createRandom(): Random;<br>Differences: function createRandom(): Random;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface AsyKeyGenerator<br>Differences: interface AsyKeyGenerator|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: generateKeyPair(callback: AsyncCallback\<KeyPair>): void;<br>Differences: generateKeyPair(callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: generateKeyPair(): Promise\<KeyPair>;<br>Differences: generateKeyPair(): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback\<KeyPair>): void;<br>Differences: convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null, callback: AsyncCallback\<KeyPair>): void;<br>Differences: convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null, callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: convertKey(pubKey: DataBlob, priKey: DataBlob): Promise\<KeyPair>;<br>Differences: convertKey(pubKey: DataBlob, priKey: DataBlob): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null): Promise\<KeyPair>;<br>Differences: convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGenerator;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface SymKeyGenerator<br>Differences: interface SymKeyGenerator|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKeyGenerator;<br>API declaration: generateSymKey(callback: AsyncCallback\<SymKey>): void;<br>Differences: generateSymKey(callback: AsyncCallback\<SymKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKeyGenerator;<br>API declaration: generateSymKey(): Promise\<SymKey>;<br>Differences: generateSymKey(): Promise\<SymKey>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKeyGenerator;<br>API declaration: convertKey(key: DataBlob, callback: AsyncCallback\<SymKey>): void;<br>Differences: convertKey(key: DataBlob, callback: AsyncCallback\<SymKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKeyGenerator;<br>API declaration: convertKey(key: DataBlob): Promise\<SymKey>;<br>Differences: convertKey(key: DataBlob): Promise\<SymKey>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SymKeyGenerator;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createAsyKeyGenerator(algName: string): AsyKeyGenerator;<br>Differences: function createAsyKeyGenerator(algName: string): AsyKeyGenerator;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createSymKeyGenerator(algName: string): SymKeyGenerator;<br>Differences: function createSymKeyGenerator(algName: string): SymKeyGenerator;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Mac<br>Differences: interface Mac|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: init(key: SymKey, callback: AsyncCallback\<void>): void;<br>Differences: init(key: SymKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: init(key: SymKey): Promise\<void>;<br>Differences: init(key: SymKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>Differences: update(input: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>Differences: update(input: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: doFinal(callback: AsyncCallback\<DataBlob>): void;<br>Differences: doFinal(callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: doFinal(): Promise\<DataBlob>;<br>Differences: doFinal(): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: getMacLength(): number;<br>Differences: getMacLength(): number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Mac;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createMac(algName: string): Mac;<br>Differences: function createMac(algName: string): Mac;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Md<br>Differences: interface Md|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>Differences: update(input: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>Differences: update(input: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: digest(callback: AsyncCallback\<DataBlob>): void;<br>Differences: digest(callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: digest(): Promise\<DataBlob>;<br>Differences: digest(): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: getMdLength(): number;<br>Differences: getMdLength(): number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Md;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createMd(algName: string): Md;<br>Differences: function createMd(algName: string): Md;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum CipherSpecItem<br>Differences: enum CipherSpecItem|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CipherSpecItem;<br>API declaration: OAEP_MD_NAME_STR = 100<br>Differences: OAEP_MD_NAME_STR = 100|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CipherSpecItem;<br>API declaration: OAEP_MGF_NAME_STR = 101<br>Differences: OAEP_MGF_NAME_STR = 101|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CipherSpecItem;<br>API declaration: OAEP_MGF1_MD_STR = 102<br>Differences: OAEP_MGF1_MD_STR = 102|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CipherSpecItem;<br>API declaration: OAEP_MGF1_PSRC_UINT8ARR = 103<br>Differences: OAEP_MGF1_PSRC_UINT8ARR = 103|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: CipherSpecItem;<br>API declaration: SM2_MD_NAME_STR = 104<br>Differences: SM2_MD_NAME_STR = 104|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum SignSpecItem<br>Differences: enum SignSpecItem|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: PSS_MD_NAME_STR = 100<br>Differences: PSS_MD_NAME_STR = 100|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: PSS_MGF_NAME_STR = 101<br>Differences: PSS_MGF_NAME_STR = 101|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: PSS_MGF1_MD_STR = 102<br>Differences: PSS_MGF1_MD_STR = 102|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: PSS_SALT_LEN_NUM = 103<br>Differences: PSS_SALT_LEN_NUM = 103|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: PSS_TRAILER_FIELD_NUM = 104<br>Differences: PSS_TRAILER_FIELD_NUM = 104|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: SignSpecItem;<br>API declaration: SM2_USER_ID_UINT8ARR = 105<br>Differences: SM2_USER_ID_UINT8ARR = 105|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Cipher<br>Differences: interface Cipher|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback\<void>): void;<br>Differences: init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null, callback: AsyncCallback\<void>): void;<br>Differences: init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise\<void>;<br>Differences: init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null): Promise\<void>;<br>Differences: init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: update(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>Differences: update(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: update(data: DataBlob): Promise\<DataBlob>;<br>Differences: update(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: doFinal(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>Differences: doFinal(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: doFinal(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;<br>Differences: doFinal(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: doFinal(data: DataBlob): Promise\<DataBlob>;<br>Differences: doFinal(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: doFinal(data: DataBlob \| null): Promise\<DataBlob>;<br>Differences: doFinal(data: DataBlob \| null): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void;<br>Differences: setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: getCipherSpec(itemType: CipherSpecItem): string \| Uint8Array;<br>Differences: getCipherSpec(itemType: CipherSpecItem): string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createCipher(transformation: string): Cipher;<br>Differences: function createCipher(transformation: string): Cipher;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Sign<br>Differences: interface Sign|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: init(priKey: PriKey, callback: AsyncCallback\<void>): void;<br>Differences: init(priKey: PriKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: init(priKey: PriKey): Promise\<void>;<br>Differences: init(priKey: PriKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: update(data: DataBlob, callback: AsyncCallback\<void>): void;<br>Differences: update(data: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: update(data: DataBlob): Promise\<void>;<br>Differences: update(data: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: sign(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>Differences: sign(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: sign(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;<br>Differences: sign(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: sign(data: DataBlob): Promise\<DataBlob>;<br>Differences: sign(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: sign(data: DataBlob \| null): Promise\<DataBlob>;<br>Differences: sign(data: DataBlob \| null): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: setSignSpec(itemType: SignSpecItem, itemValue: number): void;<br>Differences: setSignSpec(itemType: SignSpecItem, itemValue: number): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: setSignSpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;<br>Differences: setSignSpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: getSignSpec(itemType: SignSpecItem): string \| number;<br>Differences: getSignSpec(itemType: SignSpecItem): string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Sign;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Verify<br>Differences: interface Verify|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: init(pubKey: PubKey, callback: AsyncCallback\<void>): void;<br>Differences: init(pubKey: PubKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: init(pubKey: PubKey): Promise\<void>;<br>Differences: init(pubKey: PubKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: update(data: DataBlob, callback: AsyncCallback\<void>): void;<br>Differences: update(data: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: update(data: DataBlob): Promise\<void>;<br>Differences: update(data: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: verify(data: DataBlob, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;<br>Differences: verify(data: DataBlob, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: verify(data: DataBlob \| null, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;<br>Differences: verify(data: DataBlob \| null, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: verify(data: DataBlob, signatureData: DataBlob): Promise\<boolean>;<br>Differences: verify(data: DataBlob, signatureData: DataBlob): Promise\<boolean>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: verify(data: DataBlob \| null, signatureData: DataBlob): Promise\<boolean>;<br>Differences: verify(data: DataBlob \| null, signatureData: DataBlob): Promise\<boolean>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: setVerifySpec(itemType: SignSpecItem, itemValue: number): void;<br>Differences: setVerifySpec(itemType: SignSpecItem, itemValue: number): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: setVerifySpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;<br>Differences: setVerifySpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: getVerifySpec(itemType: SignSpecItem): string \| number;<br>Differences: getVerifySpec(itemType: SignSpecItem): string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Verify;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createSign(algName: string): Sign;<br>Differences: function createSign(algName: string): Sign;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createVerify(algName: string): Verify;<br>Differences: function createVerify(algName: string): Verify;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface KeyAgreement<br>Differences: interface KeyAgreement|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KeyAgreement;<br>API declaration: generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback\<DataBlob>): void;<br>Differences: generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KeyAgreement;<br>API declaration: generateSecret(priKey: PriKey, pubKey: PubKey): Promise\<DataBlob>;<br>Differences: generateSecret(priKey: PriKey, pubKey: PubKey): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KeyAgreement;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createKeyAgreement(algName: string): KeyAgreement;<br>Differences: function createKeyAgreement(algName: string): KeyAgreement;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum AsyKeySpecItem<br>Differences: enum AsyKeySpecItem|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DSA_P_BN = 101<br>Differences: DSA_P_BN = 101|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DSA_Q_BN = 102<br>Differences: DSA_Q_BN = 102|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DSA_G_BN = 103<br>Differences: DSA_G_BN = 103|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DSA_SK_BN = 104<br>Differences: DSA_SK_BN = 104|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DSA_PK_BN = 105<br>Differences: DSA_PK_BN = 105|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_FP_P_BN = 201<br>Differences: ECC_FP_P_BN = 201|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_A_BN = 202<br>Differences: ECC_A_BN = 202|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_B_BN = 203<br>Differences: ECC_B_BN = 203|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_G_X_BN = 204<br>Differences: ECC_G_X_BN = 204|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_G_Y_BN = 205<br>Differences: ECC_G_Y_BN = 205|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_N_BN = 206<br>Differences: ECC_N_BN = 206|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_H_NUM = 207<br>Differences: ECC_H_NUM = 207|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_SK_BN = 208<br>Differences: ECC_SK_BN = 208|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_PK_X_BN = 209<br>Differences: ECC_PK_X_BN = 209|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_PK_Y_BN = 210<br>Differences: ECC_PK_Y_BN = 210|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_FIELD_TYPE_STR = 211<br>Differences: ECC_FIELD_TYPE_STR = 211|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_FIELD_SIZE_NUM = 212<br>Differences: ECC_FIELD_SIZE_NUM = 212|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ECC_CURVE_NAME_STR = 213<br>Differences: ECC_CURVE_NAME_STR = 213|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: RSA_N_BN = 301<br>Differences: RSA_N_BN = 301|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: RSA_SK_BN = 302<br>Differences: RSA_SK_BN = 302|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: RSA_PK_BN = 303<br>Differences: RSA_PK_BN = 303|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DH_P_BN = 401<br>Differences: DH_P_BN = 401|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DH_G_BN = 402<br>Differences: DH_G_BN = 402|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DH_L_NUM = 403<br>Differences: DH_L_NUM = 403|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DH_SK_BN = 404<br>Differences: DH_SK_BN = 404|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: DH_PK_BN = 405<br>Differences: DH_PK_BN = 405|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ED25519_SK_BN = 501<br>Differences: ED25519_SK_BN = 501|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: ED25519_PK_BN = 502<br>Differences: ED25519_PK_BN = 502|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: X25519_SK_BN = 601<br>Differences: X25519_SK_BN = 601|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecItem;<br>API declaration: X25519_PK_BN = 602<br>Differences: X25519_PK_BN = 602|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: enum AsyKeySpecType<br>Differences: enum AsyKeySpecType|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecType;<br>API declaration: COMMON_PARAMS_SPEC = 0<br>Differences: COMMON_PARAMS_SPEC = 0|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecType;<br>API declaration: PRIVATE_KEY_SPEC = 1<br>Differences: PRIVATE_KEY_SPEC = 1|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecType;<br>API declaration: PUBLIC_KEY_SPEC = 2<br>Differences: PUBLIC_KEY_SPEC = 2|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpecType;<br>API declaration: KEY_PAIR_SPEC = 3<br>Differences: KEY_PAIR_SPEC = 3|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface AsyKeySpec<br>Differences: interface AsyKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpec;<br>API declaration: algName: string;<br>Differences: algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeySpec;<br>API declaration: specType: AsyKeySpecType;<br>Differences: specType: AsyKeySpecType;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DSACommonParamsSpec<br>Differences: interface DSACommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSACommonParamsSpec;<br>API declaration: p: bigint;<br>Differences: p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSACommonParamsSpec;<br>API declaration: q: bigint;<br>Differences: q: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSACommonParamsSpec;<br>API declaration: g: bigint;<br>Differences: g: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DSAPubKeySpec<br>Differences: interface DSAPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSAPubKeySpec;<br>API declaration: params: DSACommonParamsSpec;<br>Differences: params: DSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSAPubKeySpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DSAKeyPairSpec<br>Differences: interface DSAKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSAKeyPairSpec;<br>API declaration: params: DSACommonParamsSpec;<br>Differences: params: DSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSAKeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DSAKeyPairSpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECField<br>Differences: interface ECField|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECField;<br>API declaration: fieldType: string;<br>Differences: fieldType: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECFieldFp<br>Differences: interface ECFieldFp|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECFieldFp;<br>API declaration: p: bigint;<br>Differences: p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Point<br>Differences: interface Point|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Point;<br>API declaration: x: bigint;<br>Differences: x: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Point;<br>API declaration: y: bigint;<br>Differences: y: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECCCommonParamsSpec<br>Differences: interface ECCCommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: field: ECField;<br>Differences: field: ECField;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: a: bigint;<br>Differences: a: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: b: bigint;<br>Differences: b: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: g: Point;<br>Differences: g: Point;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: n: bigint;<br>Differences: n: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCCommonParamsSpec;<br>API declaration: h: number;<br>Differences: h: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECCPriKeySpec<br>Differences: interface ECCPriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCPriKeySpec;<br>API declaration: params: ECCCommonParamsSpec;<br>Differences: params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCPriKeySpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECCPubKeySpec<br>Differences: interface ECCPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCPubKeySpec;<br>API declaration: params: ECCCommonParamsSpec;<br>Differences: params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCPubKeySpec;<br>API declaration: pk: Point;<br>Differences: pk: Point;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ECCKeyPairSpec<br>Differences: interface ECCKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCKeyPairSpec;<br>API declaration: params: ECCCommonParamsSpec;<br>Differences: params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCKeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCKeyPairSpec;<br>API declaration: pk: Point;<br>Differences: pk: Point;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: class ECCKeyUtil<br>Differences: class ECCKeyUtil|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ECCKeyUtil;<br>API declaration: static genECCCommonParamsSpec(curveName: string): ECCCommonParamsSpec;<br>Differences: static genECCCommonParamsSpec(curveName: string): ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DHCommonParamsSpec<br>Differences: interface DHCommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHCommonParamsSpec;<br>API declaration: p: bigint;<br>Differences: p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHCommonParamsSpec;<br>API declaration: g: bigint;<br>Differences: g: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHCommonParamsSpec;<br>API declaration: l: number;<br>Differences: l: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DHPriKeySpec<br>Differences: interface DHPriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHPriKeySpec;<br>API declaration: params: DHCommonParamsSpec;<br>Differences: params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHPriKeySpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DHPubKeySpec<br>Differences: interface DHPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHPubKeySpec;<br>API declaration: params: DHCommonParamsSpec;<br>Differences: params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHPubKeySpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface DHKeyPairSpec<br>Differences: interface DHKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHKeyPairSpec;<br>API declaration: params: DHCommonParamsSpec;<br>Differences: params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHKeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHKeyPairSpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: class DHKeyUtil<br>Differences: class DHKeyUtil|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: DHKeyUtil;<br>API declaration: static genDHCommonParamsSpec(pLen: number, skLen?: number): DHCommonParamsSpec;<br>Differences: static genDHCommonParamsSpec(pLen: number, skLen?: number): DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ED25519PriKeySpec<br>Differences: interface ED25519PriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ED25519PriKeySpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ED25519PubKeySpec<br>Differences: interface ED25519PubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ED25519PubKeySpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface ED25519KeyPairSpec<br>Differences: interface ED25519KeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ED25519KeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: ED25519KeyPairSpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface X25519PriKeySpec<br>Differences: interface X25519PriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: X25519PriKeySpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface X25519PubKeySpec<br>Differences: interface X25519PubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: X25519PubKeySpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface X25519KeyPairSpec<br>Differences: interface X25519KeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: X25519KeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: X25519KeyPairSpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface RSACommonParamsSpec<br>Differences: interface RSACommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSACommonParamsSpec;<br>API declaration: n: bigint;<br>Differences: n: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface RSAPubKeySpec<br>Differences: interface RSAPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSAPubKeySpec;<br>API declaration: params: RSACommonParamsSpec;<br>Differences: params: RSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSAPubKeySpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface RSAKeyPairSpec<br>Differences: interface RSAKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSAKeyPairSpec;<br>API declaration: params: RSACommonParamsSpec;<br>Differences: params: RSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSAKeyPairSpec;<br>API declaration: sk: bigint;<br>Differences: sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: RSAKeyPairSpec;<br>API declaration: pk: bigint;<br>Differences: pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface AsyKeyGeneratorBySpec<br>Differences: interface AsyKeyGeneratorBySpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generateKeyPair(callback: AsyncCallback\<KeyPair>): void;<br>Differences: generateKeyPair(callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generateKeyPair(): Promise\<KeyPair>;<br>Differences: generateKeyPair(): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generatePriKey(callback: AsyncCallback\<PriKey>): void;<br>Differences: generatePriKey(callback: AsyncCallback\<PriKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generatePriKey(): Promise\<PriKey>;<br>Differences: generatePriKey(): Promise\<PriKey>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generatePubKey(callback: AsyncCallback\<PubKey>): void;<br>Differences: generatePubKey(callback: AsyncCallback\<PubKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: generatePubKey(): Promise\<PubKey>;<br>Differences: generatePubKey(): Promise\<PubKey>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: AsyKeyGeneratorBySpec;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createAsyKeyGeneratorBySpec(asyKeySpec: AsyKeySpec): AsyKeyGeneratorBySpec;<br>Differences: function createAsyKeyGeneratorBySpec(asyKeySpec: AsyKeySpec): AsyKeyGeneratorBySpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface KdfSpec<br>Differences: interface KdfSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: KdfSpec;<br>API declaration: algName: string;<br>Differences: algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface PBKDF2Spec<br>Differences: interface PBKDF2Spec|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PBKDF2Spec;<br>API declaration: password: string \| Uint8Array;<br>Differences: password: string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PBKDF2Spec;<br>API declaration: salt: Uint8Array;<br>Differences: salt: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PBKDF2Spec;<br>API declaration: iterations: number;<br>Differences: iterations: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: PBKDF2Spec;<br>API declaration: keySize: number;<br>Differences: keySize: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: interface Kdf<br>Differences: interface Kdf|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Kdf;<br>API declaration: generateSecret(params: KdfSpec, callback: AsyncCallback\<DataBlob>): void;<br>Differences: generateSecret(params: KdfSpec, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Kdf;<br>API declaration: generateSecret(params: KdfSpec): Promise\<DataBlob>;<br>Differences: generateSecret(params: KdfSpec): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: Kdf;<br>API declaration: readonly algName: string;<br>Differences: readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: cryptoFramework;<br>API declaration: function createKdf(algName: string): Kdf;<br>Differences: function createKdf(algName: string): Kdf;|api/@ohos.security.cryptoFramework.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface CipherResponse<br>Differences: export interface CipherResponse|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherResponse;<br>API declaration: text: string;<br>Differences: text: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface CipherRsaOptions<br>Differences: export interface CipherRsaOptions|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: action: string;<br>Differences: action: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: text: string;<br>Differences: text: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: key: string;<br>Differences: key: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: transformation?: string;<br>Differences: transformation?: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: success: (data: CipherResponse) => void;<br>Differences: success: (data: CipherResponse) => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: fail: (data: string, code: number) => void;<br>Differences: fail: (data: string, code: number) => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherRsaOptions;<br>API declaration: complete: () => void;<br>Differences: complete: () => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: global;<br>API declaration: export interface CipherAesOptions<br>Differences: export interface CipherAesOptions|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: action: string;<br>Differences: action: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: text: string;<br>Differences: text: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: key: string;<br>Differences: key: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: transformation?: string;<br>Differences: transformation?: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: iv?: string;<br>Differences: iv?: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: ivOffset?: string;<br>Differences: ivOffset?: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: ivLen?: string;<br>Differences: ivLen?: string;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: success: (data: CipherResponse) => void;<br>Differences: success: (data: CipherResponse) => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: fail: (data: string, code: number) => void;<br>Differences: fail: (data: string, code: number) => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: CipherAesOptions;<br>API declaration: complete: () => void;<br>Differences: complete: () => void;|api/@system.cipher.d.ts|
|New API|NA|Class name: global;<br>API declaration: export default class Cipher<br>Differences: export default class Cipher|api/@system.cipher.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: static rsa(options: CipherRsaOptions): void;<br>Differences: static rsa(options: CipherRsaOptions): void;|api/@system.cipher.d.ts|
|New API|NA|Class name: Cipher;<br>API declaration: static aes(options: CipherAesOptions): void;<br>Differences: static aes(options: CipherAesOptions): void;|api/@system.cipher.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@ohos.security.cryptoFramework.d.ts<br>Differences: CryptoArchitectureKit|api/@ohos.security.cryptoFramework.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: api\@system.cipher.d.ts<br>Differences: CryptoArchitectureKit|api/@system.cipher.d.ts|
|New Kit|Class name: global;<br>API declaration: <br>Differences: NA|Class name: global;<br>API declaration: kits\@kit.CryptoArchitectureKit.d.ts<br>Differences: CryptoArchitectureKit|kits/@kit.CryptoArchitectureKit.d.ts|
