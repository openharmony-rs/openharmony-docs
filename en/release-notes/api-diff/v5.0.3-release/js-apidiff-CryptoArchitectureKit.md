| Change Type | Old Version | New Version | d.ts File |
| ---- | ------ | ------ | -------- |
|New error code|Class name: PriKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>DIfferences: NA|Class name: PriKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>DIfferences: 801|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: PubKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>DIfferences: NA|Class name: PubKey;<br>API declaration: getAsyKeySpec(itemType: AsyKeySpecItem): bigint \| string \| number;<br>DIfferences: 801|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: init(key: SymKey, callback: AsyncCallback\<void>): void;<br>DIfferences: NA|Class name: Mac;<br>API declaration: init(key: SymKey, callback: AsyncCallback\<void>): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: init(key: SymKey): Promise\<void>;<br>DIfferences: NA|Class name: Mac;<br>API declaration: init(key: SymKey): Promise\<void>;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: initSync(key: SymKey): void;<br>DIfferences: NA|Class name: Mac;<br>API declaration: initSync(key: SymKey): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>DIfferences: NA|Class name: Mac;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>DIfferences: NA|Class name: Mac;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Mac;<br>API declaration: updateSync(input: DataBlob): void;<br>DIfferences: NA|Class name: Mac;<br>API declaration: updateSync(input: DataBlob): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Md;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>DIfferences: NA|Class name: Md;<br>API declaration: update(input: DataBlob, callback: AsyncCallback\<void>): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Md;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>DIfferences: NA|Class name: Md;<br>API declaration: update(input: DataBlob): Promise\<void>;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New error code|Class name: Md;<br>API declaration: updateSync(input: DataBlob): void;<br>DIfferences: NA|Class name: Md;<br>API declaration: updateSync(input: DataBlob): void;<br>DIfferences: 17620001|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: Result;<br>API declaration: ERR_PARAMETER_CHECK_FAILED = 17620003<br>DIfferences: ERR_PARAMETER_CHECK_FAILED = 17620003|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface KeyEncodingConfig<br>DIfferences: interface KeyEncodingConfig|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: KeyEncodingConfig;<br>API declaration: password: string;<br>DIfferences: password: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: KeyEncodingConfig;<br>API declaration: cipherName: string;<br>DIfferences: cipherName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface MacSpec<br>DIfferences: interface MacSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: MacSpec;<br>API declaration: algName: string;<br>DIfferences: algName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface HmacSpec<br>DIfferences: interface HmacSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: HmacSpec;<br>API declaration: mdName: string;<br>DIfferences: mdName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface CmacSpec<br>DIfferences: interface CmacSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: CmacSpec;<br>API declaration: cipherName: string;<br>DIfferences: cipherName: string;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface ScryptSpec<br>DIfferences: interface ScryptSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: passphrase: string \| Uint8Array;<br>DIfferences: passphrase: string \| Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: salt: Uint8Array;<br>DIfferences: salt: Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: n: number;<br>DIfferences: n: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: r: number;<br>DIfferences: r: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: p: number;<br>DIfferences: p: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: maxMemory: number;<br>DIfferences: maxMemory: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: ScryptSpec;<br>API declaration: keySize: number;<br>DIfferences: keySize: number;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: interface EccSignatureSpec<br>DIfferences: interface EccSignatureSpec|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: EccSignatureSpec;<br>API declaration: r: bigint;<br>DIfferences: r: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: EccSignatureSpec;<br>API declaration: s: bigint;<br>DIfferences: s: bigint;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: cryptoFramework;<br>API declaration: class SignatureUtils<br>DIfferences: class SignatureUtils|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: SignatureUtils;<br>API declaration: static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec;<br>DIfferences: static genEccSignatureSpec(data: Uint8Array): EccSignatureSpec;|api/@ohos.security.cryptoFramework.d.ts|
|New API |NA|Class name: SignatureUtils;<br>API declaration: static genEccSignature(spec: EccSignatureSpec): Uint8Array;<br>DIfferences: static genEccSignature(spec: EccSignatureSpec): Uint8Array;|api/@ohos.security.cryptoFramework.d.ts|
