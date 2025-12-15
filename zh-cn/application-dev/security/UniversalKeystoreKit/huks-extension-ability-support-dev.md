# CryptoExtensionAbility适配开发指导

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

## 适配指导

本指导是提供给驱动厂商继承实现[CryptoExtensionAbility](../../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)需要的接口能力，此处给出实现参考，其他实现依照业务需要依次调用driver封装的底层驱动函数。

在DevEco Studio工程中手动新建一个CryptoExtensionAbility组件，具体步骤如下：

1. 在工程Module对应的ets目录下，右键选择“New > Directory”，新建一个目录，名称可以自己定义，例如cryptoability。

2. 在cryptoability目录，右键选择“New > ArkTS File”，新建一个文件，名称可以自己定义，例如CryptoAbility.ets。

   其目录结构如下所示：
   ```
   ├── ets
   │   └── cryptoability
   │       └── CryptoAbility.ets
   ```

3. 在工程Module对应的module.json5配置文件中注册AppServiceExtensionAbility组件，name标签表示ability名称，长度最大为127字节，srcEntry标签表示当前CryptoExtensionAbility组件所对应的代码路径，type标签需要设置为“crypto”，exported标签设置为false表示不允许三方驱动应用调用，配置多个ability时要求每个name标签必须是唯一的。

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

4. 在CryptoAbility.ets文件中，增加导入CryptoExtensionAbility的依赖包，自定义类继承CryptoExtensionAbility组件并实现其中的接口函数。导入CryptoExtensionAbility需要实现在[CryptoExtensionAbility](../../reference/apis-ability-kit/js-apis-app-ability-extensionAbility.md)中给出的所有函数，此处给出实现参考，与底层驱动的调用对应关系见下文。

   ```ts
   import { huks, huksExternalCrypto, CryptoExtensionAbility, HuksCryptoExtensionCertInfo, HuksCryptoExtensionResult } from '@kit.UniversalKeystoreKit';

   function Uint8ArrayToString(fileData: Uint8Array) {
     let dataString = '';
     for (let i = 0; i < fileData.length; i++) {
       dataString += String.fromCharCode(fileData[i]);
     }
     return dataString;
   }

   class CryptoExtension extends CryptoExtensionAbility {
     // ...
     onOpenResource(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       let resource: string = JSON.parse(resourceId);
       let index: string = '';
       if (resource['index']['key']) {
         index = resource['index']['key'];
       } else {
         index = resource['index'];
       }
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onCloseResource(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onGetProperty(handle: string, propertyId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let emptyArray: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         property: emptyArray
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onAuthUkeyPin(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       let pin: string | undefined = undefined;
       for (let param of params) {
         if (param.tag == huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_UKEY_PIN) {
           pin = Uint8ArrayToString(param.value as Uint8Array);
         }
       }
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         authState: 0,
         retryCount: 0
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onGetUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         authState: 0
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onClearUkeyPinAuthState(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onInitSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         handle: ""
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onUpdateSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let certs: Uint8Array = new Uint8Array();
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         outData: certs
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onFinishSession(handle: string, params: huks.HuksOptions): Promise<HuksCryptoExtensionResult> {
       // ...
       let certs: Uint8Array = new Uint8Array();
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         outData: certs
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onExportCertificate(resourceId: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: certInfoSetArray
       };
   
       let res: HuksCryptoExtensionResult
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
   
     onEnumCertificates(handle: string, params: Array<huksExternalCrypto.HuksExternalCryptoParam>): Promise<HuksCryptoExtensionResult> {
       // ...
       let certInfoSetArray: Array<HuksCryptoExtensionCertInfo> = []
       let result: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: certInfoSetArray
       };
   
       let res: HuksCryptoExtensionResult
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
   }
   ```

5. HuksCryptoExtensionResult的构造与错误码转换，详细错误码详见API参考中的定义，如无要求直接返回SKF错误码即可。

   ```ts
   let huksResult: HuksCryptoExtensionResult = {
     resultCode: -1,
   }
   ```

6. 封装底层Ukey driver实现接口调用，此处以使用SKF库的driver为例。

   ```ts
   import { HuksCryptoExtensionResult, HuksCryptoExtensionCertInfo } from '@kit.UniversalKeystoreKit';

   class YourUKeyDriver {
     YourDriver_onOpenResource(index, ...) {
       // ...
       // 根据index索引具体资源（app/device/container等）,调用相应SKF函数打开
       SKF_OpenApplication();
       SKF_ConnectDev();
       SKF_OpenContainer();
       // ...
     }
   
     YourDriver_onCloseResource(handle, ...) {
       // ...
       // 根据index索引具体资源（app/device/container等）,调用相应SKF函数关闭
       SKF_CloseApplication();
       SKF_DisconnectDev();
       SKF_CloseContainer();
       // ...
     }
   
     YourDriver_onGetProperty(...) {
       // ...
     }
   
     YourDriver_onAuthUkeyPin(pin, ...) {
       // ...
       SKF_VerifyPIN();
       // ...
     }
   
     YourDriver_onGetUkeyPinAuthState(...) {
       // ...
     }
   
     YourDriver_onClearUkeyPinAuthState(...) {
       // ...
       SKF_ClearSecureState();
       // ...
     }
   
     YourDriver_onInitSession(...) {
       // ...
       SKF_DigestInit();
       // ...
     }
   
     YourDriver_onUpdateSession(...) {
       // ...
       SKF_DigestUpdate();
       // ...
     }
   
     YourDriver_onFinishSession(...) {
       // ...
       SKF_DigestFinish();
       // ...
     }
   
     YourDriver_onExportCertificate(...) {
       // ...
       SKF_ExportCertificate();
       // ...
     }
   
     YourDriver_onEnumCertificates(...): HuksCryptoExtensionResult {
       // ...
       let huksResult: HuksCryptoExtensionResult = {
         resultCode: -1,
         certs: new Array<HuksCryptoExtensionCertInfo>()
       }
       for (...) {
         if (huksResult.certs != undefined) {
           huksResult.certs.push(SKF_ExportCertificate());
         }
       }
       return huksResult;
     }
   }
   ```

## 驱动应用注册、解注册CryptoExtensionAbility适配

### 注册CryptoExtensionAbility

在Ukey插入时，向系统注册CryptoExtensionAbility。

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

在Ukey拔出时，向系统解注册CryptoExtensionAbility。

**示例：**

```ts
huksExternalCrypto.unregisterProvider(provider, ExtPropertiesTemp);
```