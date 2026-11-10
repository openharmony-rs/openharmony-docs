# Two-Way SSL Login in Browser

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=f70f62268656d3b182431efa45d33eb33ec094f1 translatedAt=2026-11-10T02:59:45.344Z pushedAt=2026-11-10T06:21:44.089Z nl=1 -->

## Development Modes

Currently, the following development modes are available for two-way SSL authentication:

### Browser Uses System ArkWeb Capabilities and a Custom Client

1. The application on the device calls the certificate management capability to open the certificate selection dialog box, waits for the user to select a certificate, and obtains the [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as the resource ID.

2. The application listens to the PIN authentication callback, processes the event, and calls the certificate management capability to open the PIN authentication dialog box.

3. The certificate management capability returns the authentication result to the application on the device, and the application returns the result to the ArkWeb component.

### Browser Uses a Custom Web Component and a Custom Client

1. The application on the device calls the certificate management capability to open the certificate selection dialog box, waits for the user to select a certificate, obtains the [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as the resource ID, and transparently passes it to the **Web** component.

2. The **Web** component obtains the certificate data through certificate management, uses the [keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22) as the resource ID to call the resource opening API of the HUKS, and queries the PIN authentication status.

3. Perform the following operations based on the authentication result:

   - If the authentication is not performed, the application on the device needs to start PIN authentication. In this case, the application receives the authentication request, processes the event, and calls the certificate management capability to open the PIN authentication dialog box. After obtaining the authentication result, the application returns the result to the **Web** component and then performs the authenticated process.
   - If the authentication is successful, the **Web** component can directly call the [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9)/[updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9)/[finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) APIs of HUKS for signing.

> **NOTE**
>
> To call the three-stage capabilities of the underlying extension, ensure that the parameters passed contain [OH_HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_tag), with its value set to [OH_HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/capi-native-huks-type-h.md#oh_huks_keyclasstype).

## Example

The following is an example of using the system capability for two-way SSL authentication in a browser.

1. The application on the device calls the certificate management capability to open the certificate selection dialog box [certificateManagerDialog.openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22) and waits for the user to select a certificate.

   <!-- @[open_authorize_dialog_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/OpenAuthorizeDialog.ets) -->

   ``` TypeScript
   import { certificateManagerDialog, certificateManager } from '@kit.DeviceCertificateKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';

   @Entry
   @Component
   struct AuthorizeDialogPage {
     private context: common.Context = getContext(this) as common.Context;

     build() {
       Column() {
         Button($r('app.string.open_authorize_dialog'))
           .onClick(() => {
             this.openAuthorizeDialog();
           })
       }
       .width('100%')
       .height('100%')
     }

     private openAuthorizeDialog(): void {
       let certTypes: certificateManagerDialog.CertificateType[] = [
         certificateManagerDialog.CertificateType.CREDENTIAL_USER,
         certificateManagerDialog.CertificateType.CREDENTIAL_APP,
         certificateManagerDialog.CertificateType.CREDENTIAL_UKEY
       ];
       let certPurpose: certificateManager.CertificatePurpose =
         certificateManager.CertificatePurpose.PURPOSE_DEFAULT;
       let authorizeRequest: certificateManagerDialog.AuthorizeRequest = {
         certTypes: certTypes, certPurpose: certPurpose
       };
       try {
         certificateManagerDialog.openAuthorizeDialog(this.context, authorizeRequest)
           .then((certReference: certificateManagerDialog.CertReference) => {
             /* Record the keyUri obtained from the certificate selection dialog box for later use. */
             let keyUri = certReference.keyUri;
             console.info('Succeeded in opening authorize dialog.');
           }).catch((err: BusinessError) => {
             console.error(`Failed to open authorize dialog. Code: ${err.code}, message: ${err.message}`);
           });
       } catch (err) {
         let error = err as BusinessError;
         console.error(`Failed to open authorize dialog. Code: ${error.code}, message: ${error.message}`);
       }
     }
   }
   ```

2. The **Web** component parses the certificate, calls the HUKS to open the resource, and queries the PIN authentication status.

   First, call the NDK API of certificate management, OH_CertManager_GetUkeyCertificate](../../reference/apis-device-certificate-kit/capi-cm-native-api-h.md#oh_certmanager_getukeycertificate), to parse the certificate selected by the user and obtain the corresponding certificate data.

   Next, use **keyUri** selected by the user as the resource ID to call the HUKS NDK API, [OH_Huks_OpenResource](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_openresource) to open the resource.

   Finally, call the HUKS NDK API [OH_Huks_GetUkeyPinAuthState](../../reference/apis-universal-keystore-kit/capi-native-huks-external-crypto-api-h.md#oh_huks_getukeypinauthstate) to query the PIN authentication status.

   <!-- @[ukey_best_practice_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   /* 1. Call the certificate management API to parse the certificate selected by the user and obtain the corresponding certificate data. */
   static napi_value GetUkeyCert(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value argv[1] = { nullptr };
       napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
       if (argc != 1) {
           return nullptr;
       }
       /* Obtain the keyUri length. */
       size_t length = 0;
       napi_get_value_string_utf8(env, argv[0], nullptr, 0, &length);
       if (length == 0 || length >= SIZE_MAX) {
           return nullptr;
       }
       /* Obtain the keyUri value. */
       char *keyUriBuffer = static_cast<char*>(malloc(length + 1));
       if (keyUriBuffer == nullptr) {
           return nullptr;
       }
       size_t result = 0;
       napi_get_value_string_utf8(env, argv[0], keyUriBuffer, length + 1, &result);
       OH_CM_Blob keyUri = { static_cast<uint32_t>(length), (uint8_t*)keyUriBuffer };

       /* Define the UkeyInfo input parameter. */
       OH_CM_UkeyInfo ukeyInfo = { OH_CM_CERT_PURPOSE_SIGN };

       /* Obtain the UKey certificate details corresponding to the keyUri. */
       OH_CM_CredentialDetailList credentialList = { 0, nullptr };
       int32_t ret = OH_CertManager_GetUkeyCertificate(&keyUri, &ukeyInfo, &credentialList);

       /* Release the memory after the call ends. */
       OH_CertManager_FreeUkeyCertificate(&credentialList);
       free(keyUriBuffer);
       /* Return the call result. */
       napi_value retNapi;
       napi_create_int32(env, ret, &retNapi);
       return retNapi;
   }

   /* 2. Use the keyUri selected by the user as the resourceId and call the HUKS API to open the resource. */
   static struct OH_Huks_ExternalCryptoParam g_bpOpenResourceParamsTest[] = {};

   static napi_value BpOpenResource(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value argv[1] = { nullptr };
       napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
       if (argc != 1) {
           return nullptr;
       }
       /* Obtain the keyUri length. */
       size_t length = 0;
       napi_get_value_string_utf8(env, argv[0], nullptr, 0, &length);
       if (length == 0 || length >= SIZE_MAX) {
           return nullptr;
       }
       /* Obtain the keyUri value. */
       char *keyUriBuffer = static_cast<char*>(malloc(length + 1));
       if (keyUriBuffer == nullptr) {
           return nullptr;
       }
       size_t result = 0;
       napi_get_value_string_utf8(env, argv[0], keyUriBuffer, length + 1, &result);
       OH_Huks_Blob resourceId = {
           .size = static_cast<uint32_t>(length),
           .data = (uint8_t*)keyUriBuffer
       };

       struct OH_Huks_ExternalCryptoParamSet *openResourceParamSet = nullptr;
       OH_Huks_Result ohResult;
       do {
           ohResult = InitParamSet(&openResourceParamSet, g_bpOpenResourceParamsTest,
               sizeof(g_bpOpenResourceParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
           ohResult = OH_Huks_OpenResource(&resourceId, openResourceParamSet);
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
       } while (0);
       free(keyUriBuffer);
       OH_Huks_FreeExternalCryptoParamSet(&openResourceParamSet);

       napi_value ret;
       napi_create_int32(env, ohResult.errorCode, &ret);
       return ret;
   }

   /* 3. Call the HUKS API to query the PIN authentication status. */
   static struct OH_Huks_ExternalCryptoParam g_bpGetPinStateParamsTest[] = {};

   static napi_value BpGetUkeyPinAuthState(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value argv[1] = { nullptr };
       napi_get_cb_info(env, info, &argc, argv, nullptr, nullptr);
       if (argc != 1) {
           return nullptr;
       }
       /* Obtain the keyUri length. */
       size_t length = 0;
       napi_get_value_string_utf8(env, argv[0], nullptr, 0, &length);
       if (length == 0 || length >= SIZE_MAX) {
           return nullptr;
       }
       /* Obtain the keyUri value. */
       char *keyUriBuffer = static_cast<char*>(malloc(length + 1));
       if (keyUriBuffer == nullptr) {
           return nullptr;
       }
       size_t result = 0;
       napi_get_value_string_utf8(env, argv[0], keyUriBuffer, length + 1, &result);
       OH_Huks_Blob resourceId = {
           .size = static_cast<uint32_t>(length),
           .data = (uint8_t*)keyUriBuffer
       };

       struct OH_Huks_ExternalCryptoParamSet *pinStateParamSet = nullptr;
       OH_Huks_ExternalPinAuthState authState = OH_HUKS_EXT_CRYPTO_PIN_NO_AUTH;
       OH_Huks_Result ohResult;
       do {
           ohResult = InitParamSet(&pinStateParamSet, g_bpGetPinStateParamsTest,
               sizeof(g_bpGetPinStateParamsTest) / sizeof(OH_Huks_ExternalCryptoParam));
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
           ohResult = OH_Huks_GetUkeyPinAuthState(&resourceId, pinStateParamSet, &authState);
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
       } while (0);
       free(keyUriBuffer);
       OH_Huks_FreeExternalCryptoParamSet(&pinStateParamSet);

       napi_value ret;
       napi_create_int32(env, ohResult.errorCode, &ret);
       return ret;
   }

   /* 4. Define and register the API. */
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           { "getUkeyCert", nullptr, GetUkeyCert, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "openResource", nullptr, BpOpenResource, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "getUkeyPinAuthState", nullptr, BpGetUkeyPinAuthState, nullptr, nullptr, nullptr, napi_default, nullptr },
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }

   static napi_module demoModule = {
       .nm_version = 1,
       .nm_flags = 0,
       .nm_filename = nullptr,
       .nm_register_func = Init,
       .nm_modname = "entry",
       .nm_priv = ((void*)0),
       .reserved = { 0 },
   };
   extern "C" __attribute__((constructor)) void RegisterHelloModule(void)
   {
       napi_module_register(&demoModule);
   }
   ```

   The corresponding d.ts API declaration is as follows:

   ``` TypeScript
   export function getUkeyCert(keyUri: string): number;

   export function openResource(keyUri: string): number;

   export function getUkeyPinAuthState(keyUri: string): number;
   ```

   The API call method is as follows:

   <!-- @[ukey_best_practice_arkts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/UkeyBestPractice.ets) -->

   ``` TypeScript
   import testNapi from 'libentry.so';
   @Entry
   @Component
   struct Index {
       /* Obtain it through the certificate popup API. */
       @State keyUri: string = 'Hello World';
       build() {
           Row() {
           Column() {
               Text('Hello World')
                   .fontSize(50)
                   .fontWeight(FontWeight.Bold)
                   .onClick(() => {
                       testNapi.getUkeyCert(this.keyUri);
                       testNapi.openResource(this.keyUri);
                       testNapi.getUkeyPinAuthState(this.keyUri);
                   })
           }
           .width('100%')
           }
           .height('100%')
       }
   }
   ```

3. Perform the following operations based on the authentication result:

   If the authentication is not performed, the application needs to start PIN authentication. In this case, the device application receives the authentication request, processes the event, and calls the certificate management capability to open the PIN authentication dialog box [certificateManagerDialog.openUkeyAuthDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenukeyauthdialog22). After obtaining the authentication result, the application returns the result to the **Web** component and then performs the authenticated process.

   <!-- @[open_ukey_auth_dialog_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/ets/pages/UkeyAuthDialog.ets) -->

   ``` TypeScript
   import { certificateManagerDialog } from '@kit.DeviceCertificateKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { common } from '@kit.AbilityKit';

   @Entry
   @Component
   struct UkeyAuthDialogPage {
     private context: common.Context = getContext(this) as common.Context;
     /* keyUri is the unique identifier of the certificate credential. It was recorded in the first step, and this is only an example. */
     private keyUri: string = 'testKeyAlias';

     build() {
       Column() {
         Button($r('app.string.open_ukey_auth_dialog'))
           .onClick(() => {
             this.openUkeyAuthDialog();
           })
       }
       .width('100%')
       .height('100%')
     }

     private openUkeyAuthDialog(): void {
       let ukeyAuthRequest: certificateManagerDialog.UkeyAuthRequest = { keyUri: this.keyUri };
       try {
         certificateManagerDialog.openUkeyAuthDialog(this.context, ukeyAuthRequest)
           .then(() => {
             console.info('Succeeded in opening ukey authorization dialog.');
           }).catch((err: BusinessError) => {
             console.error(`Failed to open ukey authorization dialog. Code: ${err.code}, message: ${err.message}`);
           });
       } catch (err) {
         let error = err as BusinessError;
         console.error(`Failed to open ukey authorization dialog. Code: ${error.code}, message: ${error.message}`);
       }
     }
   }
   ```

   If the authentication is successful, the **Web** component can directly call the three-stage HUKS APIs for signing.

   <!-- @[ukey_sign_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/UkeyExtension/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   /* Call the HUKS three-stage API to obtain the signed data. */
   static struct OH_Huks_Param g_signParamsTest[] = {
       {
           .tag = OH_HUKS_TAG_ALGORITHM,
           .uint32Param = OH_HUKS_ALG_RSA
       }, {
           .tag = OH_HUKS_TAG_PURPOSE,
           .uint32Param = OH_HUKS_KEY_PURPOSE_SIGN
       }, {
           .tag = OH_HUKS_TAG_KEY_SIZE,
           .uint32Param = OH_HUKS_RSA_KEY_SIZE_2048
       }, {
           .tag = OH_HUKS_TAG_PADDING,
           .uint32Param = OH_HUKS_PADDING_PSS
       }, {
           .tag = OH_HUKS_TAG_DIGEST,
           .uint32Param = OH_HUKS_DIGEST_SHA384
       }, {
           .tag = OH_HUKS_TAG_KEY_CLASS,
           .uint32Param = OH_HUKS_KEY_CLASS_EXTENSION
       }
   };

   static const uint32_t RSA_COMMON_SIZE = 1024;
   static const char *DATA_TO_SIGN = "testData";
   static const char *KEY_ALIAS = "testKeyAlias";

   static napi_value Sign(napi_env env, napi_callback_info info)
   {
       struct OH_Huks_Blob keyAlias = {
           (uint32_t)strlen(KEY_ALIAS),
           (uint8_t *)KEY_ALIAS
       };
       struct OH_Huks_Blob inData = {
           (uint32_t)strlen(DATA_TO_SIGN),
           (uint8_t *)DATA_TO_SIGN
       };
       struct OH_Huks_ParamSet *signParamSet = nullptr;
       OH_Huks_Result ohResult;
       do {
           ohResult = InitHuksParamSet(&signParamSet, g_signParamsTest,
               sizeof(g_signParamsTest) / sizeof(OH_Huks_Param));
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
           uint8_t handleS[sizeof(uint64_t)] = {0};
           struct OH_Huks_Blob handleSign = { (uint32_t)sizeof(uint64_t), handleS };
           ohResult = OH_Huks_InitSession(&keyAlias, signParamSet, &handleSign, nullptr);
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
           uint8_t outDataS[RSA_COMMON_SIZE] = {0};
           struct OH_Huks_Blob outDataSign = { RSA_COMMON_SIZE, outDataS };
           ohResult = OH_Huks_FinishSession(&handleSign, signParamSet, &inData, &outDataSign);
           if (ohResult.errorCode != OH_HUKS_SUCCESS) {
               break;
           }
       } while (0);
       OH_Huks_FreeParamSet(&signParamSet);

       napi_value ret;
       napi_create_int32(env, ohResult.errorCode, &ret);
       return ret;
   }
   ```
