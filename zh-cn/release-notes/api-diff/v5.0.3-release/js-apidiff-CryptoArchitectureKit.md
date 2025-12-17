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
|新增API|NA|类名：Result；<br>API声明：ERR_PARAMETER_CHECK_FAILED = 17620003<br>差异内容：ERR_PARAMETER_CHECK_FAILED = 17620003|api/@ohos.security.cryptoFramework.d.ts|
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
|新增API|NA|类名：cryptoFramework；<br>API声明：interface EccSignatureSpec<br>差异内容：interface EccSignatureSpec|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：EccSignatureSpec；<br>API声明：r: bigint;<br>差异内容：r: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：EccSignatureSpec；<br>API声明：s: bigint;<br>差异内容：s: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：cryptoFramework；<br>API声明：class SignatureUtils<br>差异内容：class SignatureUtils|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignatureUtils；<br>API声明：static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec;<br>差异内容：static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec;|api/@ohos.security.cryptoFramework.d.ts|
|新增API|NA|类名：SignatureUtils；<br>API声明：static genEccSignature(spec: EccSignatureSpec): Uint8Array;<br>差异内容：static genEccSignature(spec: EccSignatureSpec): Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
