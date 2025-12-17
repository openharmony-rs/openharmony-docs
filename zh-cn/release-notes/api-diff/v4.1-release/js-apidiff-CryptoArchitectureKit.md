| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace cryptoFramework<br>差异内容：declare namespace cryptoFramework|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum Result<br>差异内容：enum Result|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Result；<br>API声明：INVALID_PARAMS = 401<br>差异内容：INVALID_PARAMS = 401|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Result；<br>API声明：NOT_SUPPORT = 801<br>差异内容：NOT_SUPPORT = 801|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Result；<br>API声明：ERR_OUT_OF_MEMORY = 17620001<br>差异内容：ERR_OUT_OF_MEMORY = 17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Result；<br>API声明：ERR_RUNTIME_ERROR = 17620002<br>差异内容：ERR_RUNTIME_ERROR = 17620002|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Result；<br>API声明：ERR_CRYPTO_OPERATION = 17630001<br>差异内容：ERR_CRYPTO_OPERATION = 17630001|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DataBlob<br>差异内容：interface DataBlob|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DataBlob；<br>API声明：data: Uint8Array;<br>差异内容：data: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ParamsSpec<br>差异内容：interface ParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ParamsSpec；<br>API声明：algName: string;<br>差异内容：algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface IvParamsSpec<br>差异内容：interface IvParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：IvParamsSpec；<br>API声明：iv: DataBlob;<br>差异内容：iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface GcmParamsSpec<br>差异内容：interface GcmParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：GcmParamsSpec；<br>API声明：iv: DataBlob;<br>差异内容：iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：GcmParamsSpec；<br>API声明：aad: DataBlob;<br>差异内容：aad: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：GcmParamsSpec；<br>API声明：authTag: DataBlob;<br>差异内容：authTag: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface CcmParamsSpec<br>差异内容：interface CcmParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CcmParamsSpec；<br>API声明：iv: DataBlob;<br>差异内容：iv: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CcmParamsSpec；<br>API声明：aad: DataBlob;<br>差异内容：aad: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CcmParamsSpec；<br>API声明：authTag: DataBlob;<br>差异内容：authTag: DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum CryptoMode<br>差异内容：enum CryptoMode|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CryptoMode；<br>API声明：ENCRYPT_MODE = 0<br>差异内容：ENCRYPT_MODE = 0|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CryptoMode；<br>API声明：DECRYPT_MODE = 1<br>差异内容：DECRYPT_MODE = 1|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Key<br>差异内容：interface Key|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Key；<br>API声明：getEncoded(): DataBlob;<br>差异内容：getEncoded(): DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Key；<br>API声明：readonly format: string;<br>差异内容：readonly format: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Key；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface SymKey<br>差异内容：interface SymKey|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKey；<br>API声明：clearMem(): void;<br>差异内容：clearMem(): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface PriKey<br>差异内容：interface PriKey|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PriKey；<br>API声明：clearMem(): void;<br>差异内容：clearMem(): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PriKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface PubKey<br>差异内容：interface PubKey|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PubKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface KeyPair<br>差异内容：interface KeyPair|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyPair；<br>API声明：readonly priKey: PriKey;<br>差异内容：readonly priKey: PriKey;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyPair；<br>API声明：readonly pubKey: PubKey;<br>差异内容：readonly pubKey: PubKey;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Random<br>差异内容：interface Random|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Random；<br>API声明：generateRandom(len: number, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：generateRandom(len: number, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Random；<br>API声明：generateRandom(len: number): Promise\<DataBlob>;<br>差异内容：generateRandom(len: number): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Random；<br>API声明：generateRandomSync(len: number): DataBlob;<br>差异内容：generateRandomSync(len: number): DataBlob;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Random；<br>API声明：setSeed(seed: DataBlob): void;<br>差异内容：setSeed(seed: DataBlob): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Random；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createRandom(): Random;<br>差异内容：function createRandom(): Random;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface AsyKeyGenerator<br>差异内容：interface AsyKeyGenerator|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：generateKeyPair(callback: AsyncCallback\<KeyPair>): void;<br>差异内容：generateKeyPair(callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：generateKeyPair(): Promise\<KeyPair>;<br>差异内容：generateKeyPair(): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback\<KeyPair>): void;<br>差异内容：convertKey(pubKey: DataBlob, priKey: DataBlob, callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null, callback: AsyncCallback\<KeyPair>): void;<br>差异内容：convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null, callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertKey(pubKey: DataBlob, priKey: DataBlob): Promise\<KeyPair>;<br>差异内容：convertKey(pubKey: DataBlob, priKey: DataBlob): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null): Promise\<KeyPair>;<br>差异内容：convertKey(pubKey: DataBlob \| null, priKey: DataBlob \| null): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface SymKeyGenerator<br>差异内容：interface SymKeyGenerator|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKeyGenerator；<br>API声明：generateSymKey(callback: AsyncCallback\<SymKey>): void;<br>差异内容：generateSymKey(callback: AsyncCallback\<SymKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKeyGenerator；<br>API声明：generateSymKey(): Promise\<SymKey>;<br>差异内容：generateSymKey(): Promise\<SymKey>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKeyGenerator；<br>API声明：convertKey(key: DataBlob, callback: AsyncCallback\<SymKey>): void;<br>差异内容：convertKey(key: DataBlob, callback: AsyncCallback\<SymKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKeyGenerator；<br>API声明：convertKey(key: DataBlob): Promise\<SymKey>;<br>差异内容：convertKey(key: DataBlob): Promise\<SymKey>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SymKeyGenerator；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createAsyKeyGenerator(algName: string): AsyKeyGenerator;<br>差异内容：function createAsyKeyGenerator(algName: string): AsyKeyGenerator;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createSymKeyGenerator(algName: string): SymKeyGenerator;<br>差异内容：function createSymKeyGenerator(algName: string): SymKeyGenerator;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Mac<br>差异内容：interface Mac|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：init(key: SymKey, callback: AsyncCallback\<void>): void;<br>差异内容：init(key: SymKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：init(key: SymKey): Promise\<void>;<br>差异内容：init(key: SymKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：update(input: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：update(input: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：doFinal(callback: AsyncCallback\<DataBlob>): void;<br>差异内容：doFinal(callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：doFinal(): Promise\<DataBlob>;<br>差异内容：doFinal(): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：getMacLength(): number;<br>差异内容：getMacLength(): number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Mac；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createMac(algName: string): Mac;<br>差异内容：function createMac(algName: string): Mac;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Md<br>差异内容：interface Md|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：update(input: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：update(input: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：digest(callback: AsyncCallback\<DataBlob>): void;<br>差异内容：digest(callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：digest(): Promise\<DataBlob>;<br>差异内容：digest(): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：getMdLength(): number;<br>差异内容：getMdLength(): number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Md；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createMd(algName: string): Md;<br>差异内容：function createMd(algName: string): Md;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum CipherSpecItem<br>差异内容：enum CipherSpecItem|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CipherSpecItem；<br>API声明：OAEP_MD_NAME_STR = 100<br>差异内容：OAEP_MD_NAME_STR = 100|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CipherSpecItem；<br>API声明：OAEP_MGF_NAME_STR = 101<br>差异内容：OAEP_MGF_NAME_STR = 101|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CipherSpecItem；<br>API声明：OAEP_MGF1_MD_STR = 102<br>差异内容：OAEP_MGF1_MD_STR = 102|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CipherSpecItem；<br>API声明：OAEP_MGF1_PSRC_UINT8ARR = 103<br>差异内容：OAEP_MGF1_PSRC_UINT8ARR = 103|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CipherSpecItem；<br>API声明：SM2_MD_NAME_STR = 104<br>差异内容：SM2_MD_NAME_STR = 104|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum SignSpecItem<br>差异内容：enum SignSpecItem|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：PSS_MD_NAME_STR = 100<br>差异内容：PSS_MD_NAME_STR = 100|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：PSS_MGF_NAME_STR = 101<br>差异内容：PSS_MGF_NAME_STR = 101|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：PSS_MGF1_MD_STR = 102<br>差异内容：PSS_MGF1_MD_STR = 102|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：PSS_SALT_LEN_NUM = 103<br>差异内容：PSS_SALT_LEN_NUM = 103|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：PSS_TRAILER_FIELD_NUM = 104<br>差异内容：PSS_TRAILER_FIELD_NUM = 104|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignSpecItem；<br>API声明：SM2_USER_ID_UINT8ARR = 105<br>差异内容：SM2_USER_ID_UINT8ARR = 105|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Cipher<br>差异内容：interface Cipher|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback\<void>): void;<br>差异内容：init(opMode: CryptoMode, key: Key, params: ParamsSpec, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null, callback: AsyncCallback\<void>): void;<br>差异内容：init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise\<void>;<br>差异内容：init(opMode: CryptoMode, key: Key, params: ParamsSpec): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null): Promise\<void>;<br>差异内容：init(opMode: CryptoMode, key: Key, params: ParamsSpec \| null): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：update(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：update(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：update(data: DataBlob): Promise\<DataBlob>;<br>差异内容：update(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：doFinal(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：doFinal(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：doFinal(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：doFinal(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：doFinal(data: DataBlob): Promise\<DataBlob>;<br>差异内容：doFinal(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：doFinal(data: DataBlob \| null): Promise\<DataBlob>;<br>差异内容：doFinal(data: DataBlob \| null): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void;<br>差异内容：setCipherSpec(itemType: CipherSpecItem, itemValue: Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：getCipherSpec(itemType: CipherSpecItem): string \| Uint8Array;<br>差异内容：getCipherSpec(itemType: CipherSpecItem): string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createCipher(transformation: string): Cipher;<br>差异内容：function createCipher(transformation: string): Cipher;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Sign<br>差异内容：interface Sign|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：init(priKey: PriKey, callback: AsyncCallback\<void>): void;<br>差异内容：init(priKey: PriKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：init(priKey: PriKey): Promise\<void>;<br>差异内容：init(priKey: PriKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：update(data: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：update(data: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：update(data: DataBlob): Promise\<void>;<br>差异内容：update(data: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：sign(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：sign(data: DataBlob, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：sign(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：sign(data: DataBlob \| null, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：sign(data: DataBlob): Promise\<DataBlob>;<br>差异内容：sign(data: DataBlob): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：sign(data: DataBlob \| null): Promise\<DataBlob>;<br>差异内容：sign(data: DataBlob \| null): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：setSignSpec(itemType: SignSpecItem, itemValue: number): void;<br>差异内容：setSignSpec(itemType: SignSpecItem, itemValue: number): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：setSignSpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;<br>差异内容：setSignSpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：getSignSpec(itemType: SignSpecItem): string \| number;<br>差异内容：getSignSpec(itemType: SignSpecItem): string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Sign；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Verify<br>差异内容：interface Verify|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：init(pubKey: PubKey, callback: AsyncCallback\<void>): void;<br>差异内容：init(pubKey: PubKey, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：init(pubKey: PubKey): Promise\<void>;<br>差异内容：init(pubKey: PubKey): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：update(data: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：update(data: DataBlob, callback: AsyncCallback\<void>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：update(data: DataBlob): Promise\<void>;<br>差异内容：update(data: DataBlob): Promise\<void>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：verify(data: DataBlob, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;<br>差异内容：verify(data: DataBlob, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：verify(data: DataBlob \| null, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;<br>差异内容：verify(data: DataBlob \| null, signatureData: DataBlob, callback: AsyncCallback\<boolean>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：verify(data: DataBlob, signatureData: DataBlob): Promise\<boolean>;<br>差异内容：verify(data: DataBlob, signatureData: DataBlob): Promise\<boolean>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：verify(data: DataBlob \| null, signatureData: DataBlob): Promise\<boolean>;<br>差异内容：verify(data: DataBlob \| null, signatureData: DataBlob): Promise\<boolean>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：setVerifySpec(itemType: SignSpecItem, itemValue: number): void;<br>差异内容：setVerifySpec(itemType: SignSpecItem, itemValue: number): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：setVerifySpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;<br>差异内容：setVerifySpec(itemType: SignSpecItem, itemValue: number \| Uint8Array): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：getVerifySpec(itemType: SignSpecItem): string \| number;<br>差异内容：getVerifySpec(itemType: SignSpecItem): string \| number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Verify；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createSign(algName: string): Sign;<br>差异内容：function createSign(algName: string): Sign;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createVerify(algName: string): Verify;<br>差异内容：function createVerify(algName: string): Verify;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface KeyAgreement<br>差异内容：interface KeyAgreement|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyAgreement；<br>API声明：generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：generateSecret(priKey: PriKey, pubKey: PubKey, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyAgreement；<br>API声明：generateSecret(priKey: PriKey, pubKey: PubKey): Promise\<DataBlob>;<br>差异内容：generateSecret(priKey: PriKey, pubKey: PubKey): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyAgreement；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createKeyAgreement(algName: string): KeyAgreement;<br>差异内容：function createKeyAgreement(algName: string): KeyAgreement;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum AsyKeySpecItem<br>差异内容：enum AsyKeySpecItem|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DSA_P_BN = 101<br>差异内容：DSA_P_BN = 101|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DSA_Q_BN = 102<br>差异内容：DSA_Q_BN = 102|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DSA_G_BN = 103<br>差异内容：DSA_G_BN = 103|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DSA_SK_BN = 104<br>差异内容：DSA_SK_BN = 104|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DSA_PK_BN = 105<br>差异内容：DSA_PK_BN = 105|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_FP_P_BN = 201<br>差异内容：ECC_FP_P_BN = 201|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_A_BN = 202<br>差异内容：ECC_A_BN = 202|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_B_BN = 203<br>差异内容：ECC_B_BN = 203|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_G_X_BN = 204<br>差异内容：ECC_G_X_BN = 204|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_G_Y_BN = 205<br>差异内容：ECC_G_Y_BN = 205|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_N_BN = 206<br>差异内容：ECC_N_BN = 206|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_H_NUM = 207<br>差异内容：ECC_H_NUM = 207|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_SK_BN = 208<br>差异内容：ECC_SK_BN = 208|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_PK_X_BN = 209<br>差异内容：ECC_PK_X_BN = 209|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_PK_Y_BN = 210<br>差异内容：ECC_PK_Y_BN = 210|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_FIELD_TYPE_STR = 211<br>差异内容：ECC_FIELD_TYPE_STR = 211|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_FIELD_SIZE_NUM = 212<br>差异内容：ECC_FIELD_SIZE_NUM = 212|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ECC_CURVE_NAME_STR = 213<br>差异内容：ECC_CURVE_NAME_STR = 213|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：RSA_N_BN = 301<br>差异内容：RSA_N_BN = 301|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：RSA_SK_BN = 302<br>差异内容：RSA_SK_BN = 302|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：RSA_PK_BN = 303<br>差异内容：RSA_PK_BN = 303|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DH_P_BN = 401<br>差异内容：DH_P_BN = 401|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DH_G_BN = 402<br>差异内容：DH_G_BN = 402|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DH_L_NUM = 403<br>差异内容：DH_L_NUM = 403|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DH_SK_BN = 404<br>差异内容：DH_SK_BN = 404|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：DH_PK_BN = 405<br>差异内容：DH_PK_BN = 405|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ED25519_SK_BN = 501<br>差异内容：ED25519_SK_BN = 501|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：ED25519_PK_BN = 502<br>差异内容：ED25519_PK_BN = 502|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：X25519_SK_BN = 601<br>差异内容：X25519_SK_BN = 601|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecItem；<br>API声明：X25519_PK_BN = 602<br>差异内容：X25519_PK_BN = 602|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：enum AsyKeySpecType<br>差异内容：enum AsyKeySpecType|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecType；<br>API声明：COMMON_PARAMS_SPEC = 0<br>差异内容：COMMON_PARAMS_SPEC = 0|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecType；<br>API声明：PRIVATE_KEY_SPEC = 1<br>差异内容：PRIVATE_KEY_SPEC = 1|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecType；<br>API声明：PUBLIC_KEY_SPEC = 2<br>差异内容：PUBLIC_KEY_SPEC = 2|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpecType；<br>API声明：KEY_PAIR_SPEC = 3<br>差异内容：KEY_PAIR_SPEC = 3|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface AsyKeySpec<br>差异内容：interface AsyKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpec；<br>API声明：algName: string;<br>差异内容：algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeySpec；<br>API声明：specType: AsyKeySpecType;<br>差异内容：specType: AsyKeySpecType;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DSACommonParamsSpec<br>差异内容：interface DSACommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSACommonParamsSpec；<br>API声明：p: bigint;<br>差异内容：p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSACommonParamsSpec；<br>API声明：q: bigint;<br>差异内容：q: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSACommonParamsSpec；<br>API声明：g: bigint;<br>差异内容：g: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DSAPubKeySpec<br>差异内容：interface DSAPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSAPubKeySpec；<br>API声明：params: DSACommonParamsSpec;<br>差异内容：params: DSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSAPubKeySpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DSAKeyPairSpec<br>差异内容：interface DSAKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSAKeyPairSpec；<br>API声明：params: DSACommonParamsSpec;<br>差异内容：params: DSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSAKeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DSAKeyPairSpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECField<br>差异内容：interface ECField|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECField；<br>API声明：fieldType: string;<br>差异内容：fieldType: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECFieldFp<br>差异内容：interface ECFieldFp|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECFieldFp；<br>API声明：p: bigint;<br>差异内容：p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Point<br>差异内容：interface Point|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Point；<br>API声明：x: bigint;<br>差异内容：x: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Point；<br>API声明：y: bigint;<br>差异内容：y: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECCCommonParamsSpec<br>差异内容：interface ECCCommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：field: ECField;<br>差异内容：field: ECField;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：a: bigint;<br>差异内容：a: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：b: bigint;<br>差异内容：b: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：g: Point;<br>差异内容：g: Point;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：n: bigint;<br>差异内容：n: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCCommonParamsSpec；<br>API声明：h: number;<br>差异内容：h: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECCPriKeySpec<br>差异内容：interface ECCPriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCPriKeySpec；<br>API声明：params: ECCCommonParamsSpec;<br>差异内容：params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCPriKeySpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECCPubKeySpec<br>差异内容：interface ECCPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCPubKeySpec；<br>API声明：params: ECCCommonParamsSpec;<br>差异内容：params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCPubKeySpec；<br>API声明：pk: Point;<br>差异内容：pk: Point;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ECCKeyPairSpec<br>差异内容：interface ECCKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCKeyPairSpec；<br>API声明：params: ECCCommonParamsSpec;<br>差异内容：params: ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCKeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCKeyPairSpec；<br>API声明：pk: Point;<br>差异内容：pk: Point;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：class ECCKeyUtil<br>差异内容：class ECCKeyUtil|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ECCKeyUtil；<br>API声明：static genECCCommonParamsSpec(curveName: string): ECCCommonParamsSpec;<br>差异内容：static genECCCommonParamsSpec(curveName: string): ECCCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DHCommonParamsSpec<br>差异内容：interface DHCommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHCommonParamsSpec；<br>API声明：p: bigint;<br>差异内容：p: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHCommonParamsSpec；<br>API声明：g: bigint;<br>差异内容：g: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHCommonParamsSpec；<br>API声明：l: number;<br>差异内容：l: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DHPriKeySpec<br>差异内容：interface DHPriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHPriKeySpec；<br>API声明：params: DHCommonParamsSpec;<br>差异内容：params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHPriKeySpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DHPubKeySpec<br>差异内容：interface DHPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHPubKeySpec；<br>API声明：params: DHCommonParamsSpec;<br>差异内容：params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHPubKeySpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface DHKeyPairSpec<br>差异内容：interface DHKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHKeyPairSpec；<br>API声明：params: DHCommonParamsSpec;<br>差异内容：params: DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHKeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHKeyPairSpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：class DHKeyUtil<br>差异内容：class DHKeyUtil|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：DHKeyUtil；<br>API声明：static genDHCommonParamsSpec(pLen: number, skLen?: number): DHCommonParamsSpec;<br>差异内容：static genDHCommonParamsSpec(pLen: number, skLen?: number): DHCommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ED25519PriKeySpec<br>差异内容：interface ED25519PriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ED25519PriKeySpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ED25519PubKeySpec<br>差异内容：interface ED25519PubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ED25519PubKeySpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ED25519KeyPairSpec<br>差异内容：interface ED25519KeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ED25519KeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ED25519KeyPairSpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface X25519PriKeySpec<br>差异内容：interface X25519PriKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：X25519PriKeySpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface X25519PubKeySpec<br>差异内容：interface X25519PubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：X25519PubKeySpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface X25519KeyPairSpec<br>差异内容：interface X25519KeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：X25519KeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：X25519KeyPairSpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface RSACommonParamsSpec<br>差异内容：interface RSACommonParamsSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSACommonParamsSpec；<br>API声明：n: bigint;<br>差异内容：n: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface RSAPubKeySpec<br>差异内容：interface RSAPubKeySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSAPubKeySpec；<br>API声明：params: RSACommonParamsSpec;<br>差异内容：params: RSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSAPubKeySpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface RSAKeyPairSpec<br>差异内容：interface RSAKeyPairSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSAKeyPairSpec；<br>API声明：params: RSACommonParamsSpec;<br>差异内容：params: RSACommonParamsSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSAKeyPairSpec；<br>API声明：sk: bigint;<br>差异内容：sk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：RSAKeyPairSpec；<br>API声明：pk: bigint;<br>差异内容：pk: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface AsyKeyGeneratorBySpec<br>差异内容：interface AsyKeyGeneratorBySpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generateKeyPair(callback: AsyncCallback\<KeyPair>): void;<br>差异内容：generateKeyPair(callback: AsyncCallback\<KeyPair>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generateKeyPair(): Promise\<KeyPair>;<br>差异内容：generateKeyPair(): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generatePriKey(callback: AsyncCallback\<PriKey>): void;<br>差异内容：generatePriKey(callback: AsyncCallback\<PriKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generatePriKey(): Promise\<PriKey>;<br>差异内容：generatePriKey(): Promise\<PriKey>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generatePubKey(callback: AsyncCallback\<PubKey>): void;<br>差异内容：generatePubKey(callback: AsyncCallback\<PubKey>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：generatePubKey(): Promise\<PubKey>;<br>差异内容：generatePubKey(): Promise\<PubKey>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGeneratorBySpec；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createAsyKeyGeneratorBySpec(asyKeySpec: AsyKeySpec): AsyKeyGeneratorBySpec;<br>差异内容：function createAsyKeyGeneratorBySpec(asyKeySpec: AsyKeySpec): AsyKeyGeneratorBySpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface KdfSpec<br>差异内容：interface KdfSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KdfSpec；<br>API声明：algName: string;<br>差异内容：algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface PBKDF2Spec<br>差异内容：interface PBKDF2Spec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PBKDF2Spec；<br>API声明：password: string \| Uint8Array;<br>差异内容：password: string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PBKDF2Spec；<br>API声明：salt: Uint8Array;<br>差异内容：salt: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PBKDF2Spec；<br>API声明：iterations: number;<br>差异内容：iterations: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PBKDF2Spec；<br>API声明：keySize: number;<br>差异内容：keySize: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface Kdf<br>差异内容：interface Kdf|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Kdf；<br>API声明：generateSecret(params: KdfSpec, callback: AsyncCallback\<DataBlob>): void;<br>差异内容：generateSecret(params: KdfSpec, callback: AsyncCallback\<DataBlob>): void;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Kdf；<br>API声明：generateSecret(params: KdfSpec): Promise\<DataBlob>;<br>差异内容：generateSecret(params: KdfSpec): Promise\<DataBlob>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：Kdf；<br>API声明：readonly algName: string;<br>差异内容：readonly algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createKdf(algName: string): Kdf;<br>差异内容：function createKdf(algName: string): Kdf;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CipherResponse<br>差异内容：export interface CipherResponse|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherResponse；<br>API声明：text: string;<br>差异内容：text: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CipherRsaOptions<br>差异内容：export interface CipherRsaOptions|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：action: string;<br>差异内容：action: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：text: string;<br>差异内容：text: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：key: string;<br>差异内容：key: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：transformation?: string;<br>差异内容：transformation?: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：success: (data: CipherResponse) => void;<br>差异内容：success: (data: CipherResponse) => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：fail: (data: string, code: number) => void;<br>差异内容：fail: (data: string, code: number) => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherRsaOptions；<br>API声明：complete: () => void;<br>差异内容：complete: () => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface CipherAesOptions<br>差异内容：export interface CipherAesOptions|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：action: string;<br>差异内容：action: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：text: string;<br>差异内容：text: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：key: string;<br>差异内容：key: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：transformation?: string;<br>差异内容：transformation?: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：iv?: string;<br>差异内容：iv?: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：ivOffset?: string;<br>差异内容：ivOffset?: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：ivLen?: string;<br>差异内容：ivLen?: string;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：success: (data: CipherResponse) => void;<br>差异内容：success: (data: CipherResponse) => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：fail: (data: string, code: number) => void;<br>差异内容：fail: (data: string, code: number) => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：CipherAesOptions；<br>API声明：complete: () => void;<br>差异内容：complete: () => void;|api/@system.cipher.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Cipher<br>差异内容：export default class Cipher|api/@system.cipher.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：static rsa(options: CipherRsaOptions): void;<br>差异内容：static rsa(options: CipherRsaOptions): void;|api/@system.cipher.d.ts|
|新增API|NA|类名：Cipher；<br>API声明：static aes(options: CipherAesOptions): void;<br>差异内容：static aes(options: CipherAesOptions): void;|api/@system.cipher.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.security.cryptoFramework.d.ts<br>差异内容：CryptoArchitectureKit|api/@ohos.security.cryptoFramework.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.cipher.d.ts<br>差异内容：CryptoArchitectureKit|api/@system.cipher.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.CryptoArchitectureKit.d.ts<br>差异内容：CryptoArchitectureKit|kits/@kit.CryptoArchitectureKit.d.ts|
