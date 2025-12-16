| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增错误码|类名：PriKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：NA|类名：PriKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：801|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：PubKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：NA|类名：PubKey；<br>API声明：getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>差异内容：801|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：init(key: SymKey, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Mac；<br>API声明：init(key: SymKey, callback: AsyncCallback\<void>): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：init(key: SymKey): Promise\<void>;<br>差异内容：NA|类名：Mac；<br>API声明：init(key: SymKey): Promise\<void>;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：initSync(key: SymKey): void;<br>差异内容：NA|类名：Mac；<br>API声明：initSync(key: SymKey): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Mac；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：NA|类名：Mac；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Mac；<br>API声明：updateSync(input: DataBlob): void;<br>差异内容：NA|类名：Mac；<br>API声明：updateSync(input: DataBlob): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Md；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：NA|类名：Md；<br>API声明：update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Md；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：NA|类名：Md；<br>API声明：update(input: DataBlob): Promise\<void>;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增错误码|类名：Md；<br>API声明：updateSync(input: DataBlob): void;<br>差异内容：NA|类名：Md；<br>API声明：updateSync(input: DataBlob): void;<br>差异内容：17620001|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：PriKey；<br>API声明：getEncodedPem(format: string, config: KeyEncodingConfig): string;<br>差异内容：getEncodedPem(format: string, config: KeyEncodingConfig): string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertPemKey(pubKey: string \| null, priKey: string \| null, password: string): Promise\<KeyPair>;<br>差异内容：convertPemKey(pubKey: string \| null, priKey: string \| null, password: string): Promise\<KeyPair>;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：AsyKeyGenerator；<br>API声明：convertPemKeySync(pubKey: string \| null, priKey: string \| null, password: string): KeyPair;<br>差异内容：convertPemKeySync(pubKey: string \| null, priKey: string \| null, password: string): KeyPair;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：function createMac(macSpec: MacSpec): Mac;<br>差异内容：function createMac(macSpec: MacSpec): Mac;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface KeyEncodingConfig<br>差异内容：interface KeyEncodingConfig|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyEncodingConfig；<br>API声明：password: string;<br>差异内容：password: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：KeyEncodingConfig；<br>API声明：cipherName: string;<br>差异内容：cipherName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface MacSpec<br>差异内容：interface MacSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：MacSpec；<br>API声明：algName: string;<br>差异内容：algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface HmacSpec<br>差异内容：interface HmacSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：HmacSpec；<br>API声明：mdName: string;<br>差异内容：mdName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface CmacSpec<br>差异内容：interface CmacSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：CmacSpec；<br>API声明：cipherName: string;<br>差异内容：cipherName: string;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：interface ScryptSpec<br>差异内容：interface ScryptSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：passphrase: string \| Uint8Array;<br>差异内容：passphrase: string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：salt: Uint8Array;<br>差异内容：salt: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：n: number;<br>差异内容：n: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：r: number;<br>差异内容：r: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：p: number;<br>差异内容：p: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：maxMemory: number;<br>差异内容：maxMemory: number;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：ScryptSpec；<br>API声明：keySize: number;<br>差异内容：keySize: number;|api/@ohos.security.cryptoFramework.d.ts|
