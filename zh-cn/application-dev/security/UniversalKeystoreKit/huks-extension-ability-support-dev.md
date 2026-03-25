# CryptoExtensionAbility适配开发指导

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## 适配指导

本文档旨在指导驱动厂商如何继承实现[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)需要的接口能力，此处给出实现参考，其他实现依照业务需要依次调用driver封装的底层驱动函数。

在DevEco Studio工程中手动新建一个CryptoExtensionAbility组件，具体步骤如下：

1. 在工程Module对应的ets目录下，右键选择“New > Directory”，新建一个目录，名称可以自己定义，例如cryptoability。

2. 在cryptoability目录，右键选择“New > ArkTS File”，新建一个文件，名称可以自己定义，例如CryptoAbility.ets。

   其目录结构如下所示：
   ```json5
   ├── ets
   │   └── cryptoability
   │       └── CryptoAbility.ets
   ```

3. 开发CryptoExtensionAbility需要配置[ohos.permission.CRYPTO_EXTENSION_REGISTER](../AccessToken/restricted-permissions.md#ohospermissioncrypto_extension_register)权限，该权限属于[受限开放权限](../AccessToken/restricted-permissions.md)，请按照[申请受限权限](../AccessToken/declare-permissions-in-acl.md)指引为应用进行申请。
   ```json5
   // entry/src/main/module.json5
   {
     "module": {
       // ...
       "requestPermissions": [
         {
           "name": "ohos.permission.CRYPTO_EXTENSION_REGISTER"
         }
       ],
     }
   }
   ```

4. 在工程Module对应的module.json5配置文件中注册AppServiceExtensionAbility组件，name标签表示ability名称，长度最大为127字节，srcEntry标签表示当前CryptoExtensionAbility组件所对应的代码路径，type标签需要设置为“crypto”，exported标签设置为false表示不允许三方应用调用，配置多个ability时要求每个name标签必须是唯一的。

   ```json5
   // entry/src/main/module.json5
   {
     "module": {
       // ...
       "extensionAbilities": [
           {
             "name": "CryptoExtension",
             "srcEntry": "./ets/cryptoability/CryptoAbility.ets",
             "type": "crypto",
             "exported": false
           }
       ],
     }
   }
   ```

5. 在CryptoAbility.ets文件中，增加导入CryptoExtensionAbility的依赖包，自定义类继承CryptoExtensionAbility组件并实现其中的接口函数。导入CryptoExtensionAbility需要实现在[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)中给出的所有函数，此处给出实现参考，与底层驱动的调用对应关系见下文。
   > **注意：**
   >
   > 1. 句柄资源和PIN认证状态需要做基于UID的隔离，在onOpenResource、onCloseResource、onAuthUkeyPin、onGetUkeyPinAuthState和onClearUkeyPinAuthState接口的入参params中会包含业务的UID信息（通过[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)可获取业务身份），可基于此做句柄资源和PIN认证状态的隔离。
   > 2. 接口函数的错误不支持自定义返回，不按接口定义方式返回会导致异常。

   ```ts
   import { huks, huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';
   import { util } from '@kit.ArkTS'
   import { cryptoFramework } from '@kit.CryptoArchitectureKit'

   class CryptoExtension extends CryptoExtensionAbility {
     // 本步骤内的接口函数实现均需在class内，为方便开发者理解及使用，每个接口函数在下文详细解释。
   }
   ```

   **接口介绍：**

   （1）onOpenResource在Ukey签名验签操作中用于打开指定资源（如建立会话或连接）。resourceId表示要打开的资源标识，应用身份可以在params中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0，handle成员非空；调用失败时，resultCode携带错误码信息。

   ```ts
   onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // 构造结果对象，默认返回操作失败，返回值为HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     // 获取 appId
     let appId: string | undefined = params.find((param =>
       param.tag === huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UID))?.value.toString();
     if (appId === undefined) {
       return Promise.resolve(result);
     }

     // 解析 resource index
     let index: string = JSON.parse(resourceId)['index'];

     // ...
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onOpenResource(index, ...);
       // 场景：打开资源成功
       result.resultCode = res.resultCode
       result.handle = res.handle
     } catch (error) {
       // 场景：打开资源失败
       result.resultCode = res.resultCode
       console.error(`promise: onOpenResource failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （2）onCloseResource在Ukey签名验签操作中用于关闭指定资源（如释放会话或连接）。handle为待关闭资源的句柄，应用身份可以在params中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0；调用失败时，resultCode携带错误码信息。

   ```ts
   onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };
     
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_closeOpenResource(handle, ...);
       // 场景：关闭资源成功
       result.resultCode = res.resultCode
     } catch (error) {
       // 场景：关闭资源失败
       result.resultCode = res.resultCode
       console.error(`promise: onCloseResource failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （3）onGetProperty在Ukey签名验签操作中用于获取指定资源的属性信息。handle为资源句柄，propertyId为待获取的属性标识，应用身份可以在params中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0，返回值中的property成员包含属性信息。调用失败时，resultCode携带错误码信息。

   在onGetProperty中须实现导出公钥功能，以便上游业务使用PIN加密传输并完成PIN码认证。加密算法支持RSA、SM2等。当入参propertyId为SKF_ExportPublicKey时，返回的公钥信息采用JSON格式，包含以下4个必选字段，分别是publicKey（公钥数据）、algo（算法类型及密钥长度）、transformation（密码学操作参数，如填充模式）、size（公钥数据长度）。具体实现可参考下方示例代码中onGetProperty接口的相关部分。

   ```ts
   onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       property: emptyArray
     };

     // 导出公钥
     if (propertyId == 'SKF_ExportPublicKey') {
       result.resultCode = 0
       let encryptionAlgo: string = 'RSA1024'
       let padding: string = 'PRIMES_2';
       // 1. 创建一个AsyKeyGenerator实例。
       let rsaGenerator = cryptoFramework.createAsyKeyGenerator(`${encryptionAlgo}|${padding}`);
       // 2. 使用密钥生成器随机生成非对称密钥对。
       let keyPair = rsaGenerator.generateKeyPairSync();
       // 3. 将公钥导出，并转换为Json字符串
       const pkData = Array.from(keyPair.pubKey.getEncoded().data);
       let transformation: string = 'RSA1024|PKCS1'
       const encoder = new util.TextEncoder();
       let info = encoder.encodeInto(JSON.stringify({
         publicKey: pkData,
         algo: encryptionAlgo,
         transformation: transformation,
         size: pkData.length
       }));
       // 4. 保存私钥，后续用于解密加密的数据
       let privKey = keyPair.priKey
       // 返回用来加密传pin的公钥和加密算法信息，详见导出公钥文档
       result.property = [
         { tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_EXTRA_DATA, value: info }
       ]
       return Promise.resolve(result);
     }
  
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：获取属性成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onGetProperty(...);
       result.resultCode = res.resultCode
       result.property = res.property
     } catch (error) {
       // 场景：获取属性失败
       result.resultCode = res.resultCode
       console.error(`promise: onGetProperty failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （4）onAuthUkeyPin用于在Ukey签名之前验证PIN码。加密后的PIN码通过param中传入[HUKS_EXT_CRYPTO_TAG_UKEY_PIN](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带，需使用onGetProperty中保存的私钥进行解密。

   当PIN码校验成功时，返回值中的resultCode成员设置为0，返回值中的authState设置为[HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate)。当PIN码不正确时，resultCode携带错误码信息，返回值中的retryCount设置为剩余重试次数，每次认证失败重试次数减1，当重试次数为0时，resultCode设置为[HUKS_CRYPTO_EXTENSION_ERR_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensionresultcode)，authState设置为[HUKS_EXT_CRYPTO_PIN_LOCKED](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalpinauthstate)。

   ```ts
   onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     let pin: string | undefined = undefined;
     for (let param of params) {
       if (param.tag == huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN) {
         let originPinData = param.value as Uint8Array;
         // 根据导出公钥所传出的加密算法和填充方式进行解密originPinData获取pin
         // ...
       }
     }
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       authState: huksExternalCrypto.HuksExternalPinAuthState.HUKS_EXT_CRYPTO_PIN_NO_AUTH,
       retryCount: 0
     };
  
     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：PIN码认证成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onAuthUkeyPin(pin, ...);
       result.resultCode = res.resultCode
       result.authState = res.authState
     } catch (error) {
       // 场景：PIN码认证失败
       result.resultCode = res.resultCode
       result.retryCount = res.retryCount
       console.error(`promise: onAuthUkeyPin failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （5）onGetUkeyPinAuthState用于应用查询PIN码的认证状态。当调用成功时，返回值中的resultCode成员设置为0，返回值中的authState设置为对应的认证状态。调用失败时，resultCode携带错误码信息。

   ```ts
   onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       authState: 0
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：获取PIN码认证状态成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onAuthUkeyPin(...);
       result.resultCode = res.resultCode
       result.authState = res.authState
       if (result.authState != 0) {
         // 场景： PIN码已认证
         // ...
       } else {
         // 场景： PIN码未认证
         // ...
       }
     } catch (error) {
       // 场景：获取PIN码认证状态失败
       result.resultCode = res.resultCode
       console.error(`promise: onGetUkeyPinAuthState failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （6）onClearUkeyPinAuthState用于重置PIN码的认证状态。当调用成功时，返回值中的resultCode成员设置为0。调用失败时，resultCode携带错误码信息。

   ```ts
   onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：清除PIN码认证状态成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onClearUkeyPinAuthState(...);
       result.resultCode = res.resultCode
     } catch (error) {
       // 场景：清除PIN码认证状态失败
       result.resultCode = res.resultCode
       console.error(`promise: onClearUkeyPinAuthState failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （7）onInitSession在Ukey签名验签操作中用于初始化密钥会话。应用身份可以在param中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0，handle成员非空。调用失败时，resultCode携带错误码信息。

   ```ts
   onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       handle: ""
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：三段式init阶段成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onInitSession(...);
       result.resultCode = res.resultCode
       result.handle = res.handle
     } catch (error) {
       // 场景：三段式init阶段失败
       result.resultCode = res.resultCode
       console.error(`promise: onInitSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （8）onUpdateSession在Ukey签名验签操作中用于分段传输大批量数据。应用身份可以在param中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0。调用失败时，resultCode携带错误码信息。

   ```ts
   onUpdateSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let certs: Uint8Array = new Uint8Array();
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: certs
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：三段式update阶段成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onUpdateSession(...);
       result.resultCode = res.resultCode
       result.outData = res.outData
     } catch (error) {
       // 场景：三段式update阶段失败
       result.resultCode = res.resultCode
       console.error(`promise: onUpdateSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （9）onFinishSession在Ukey签名操作中用于传输最后一段明文，在验签操作中用于传输签名。应用身份可以在param中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0。调用失败时，resultCode携带错误码信息。

   ```ts
   onFinishSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
     // ...
     let certs: Uint8Array = new Uint8Array();
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       outData: certs
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     };
     try {
       // 场景：三段式finish阶段成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onFinishSession(...);
       result.resultCode = res.resultCode
       result.outData = res.outData
     } catch (error) {
       // 场景：三段式finish阶段失败
       result.resultCode = res.resultCode
       console.error(`promise: onFinishSession failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （10）onExportCertificate用于查询某个resourceId下的证书。可以通过解析参数[HUKS_EXT_CRYPTO_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)获取业务希望的证书类型。如未指定，默认获取的证书类型是签名证书。<br>其值含义如下：<br>0：默认用途。<br>1：用于查询所有凭据。<br>2：用于凭据签名。<br>3：用于凭据加密。

   ```ts
   onExportCertificate(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       certs: certInfoSetArray
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：导出证书成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onExportCertificate(...);
       result.resultCode = res.resultCode
       result.certs = res.certs
     } catch (error) {
       // 场景：导出证书失败
       result.resultCode = res.resultCode
       console.error(`promise: onExportCertificate failed`);
     }
     return Promise.resolve(result);
   }
   ```

   （11）onEnumCertificates在Ukey签名验签操作中用于枚举证书列表。应用身份可以在params中由[HUKS_EXT_CRYPTO_TAG_UID](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数携带。当调用成功时，返回值中的resultCode成员设置为0，返回值中的certs成员包含证书列表（类型为Array<[HuksCryptoExtensionCertInfo](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md#hukscryptoextensioncertinfo)>）。调用失败时，resultCode携带错误码信息。

   ```ts
   onEnumCertificates(params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
     // ...
     let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
     let result: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
       certs: certInfoSetArray
     };

     let res: HuksCryptoExtensionResult = {
       resultCode: HuksCryptoExtensionResultCode.HUKS_CRYPTO_EXTENSION_ERR_EXTENSION_FAIL,
     }
     try {
       // 场景：导出所有证书成功
       let driver: YourUKeyDriver = YourDriverInstance;
       res = driver.YourDriver_onEnumCertificates(...);
       result.resultCode = res.resultCode
       result.certs = res.certs
     } catch (error) {
       // 场景：导出所有证书失败
       result.resultCode = res.resultCode
       console.error(`promise: onEnumCertificates failed`);
     }
     return Promise.resolve(result);
   }
   ```

## 驱动应用注册、解注册CryptoExtensionAbility适配

### 注册CryptoExtensionAbility

驱动HAP检测到Ukey存在时，向系统注册CryptoExtensionAbility。例如：Ukey插入等。

**示例：**

```ts
// ./ets/cryptoability/CryptoAbility.ts

import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

let ExtPropertiesTemp: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array("YourCryptoExtensionName")
  }
]

// provider名称，为保证全局唯一，建议包含厂商信息。
let provider = "testProvider"
huksExternalCrypto.registerProvider(provider, ExtPropertiesTemp);
```

### 解注册CryptoExtensionAbility

驱动HAP检测到Ukey不存在时，向系统解注册CryptoExtensionAbility。例如：Ukey拔出等。

**示例：**

```ts
huksExternalCrypto.unregisterProvider(provider, ExtPropertiesTemp);
```