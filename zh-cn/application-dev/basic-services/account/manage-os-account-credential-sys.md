# 管理系统账号凭据（仅对系统应用开放）

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

凭据可用于认证用户的身份，本文档将介绍如何录入、认证、更新、查询和删除指定系统账号的凭据。

## 凭据类型

系统账号支持管理以下凭据类型：

| 名称  | 值 | 说明             |
| ----- | ----- | ---------------- |
| PIN   | 1     | 表示PIN认证类型。 |
| FACE  | 2     | 表示人脸认证类型。|
| FINGERPRINT<sup>10+</sup>   | 4     | 表示指纹认证类型。 |

## 凭据子类型

凭据类型进一步细分为以下子类型：

> **说明：**
> 实际设备可支持的凭据类型取决于硬件能力。

| 名称       | 值 | 说明               |
| ---------- | ----- | ------------------ |
| PIN_SIX    | 10000 | 表示6位凭证。       |
| PIN_NUMBER | 10001 | 表示自定义数字凭证。 |
| PIN_MIXED  | 10002 | 表示自定义混合凭据。 |
| FACE_2D    | 20000 | 表示2D人脸凭证。   |
| FACE_3D    | 20001 | 表示3D人脸凭证。   |
| FINGERPRINT_CAPACITIVE<sup>10+</sup>    | 30000 | 表示电容式指纹。   |
| FINGERPRINT_OPTICAL<sup>10+</sup>    | 30001 | 表示光学指纹。   |
| FINGERPRINT_ULTRASONIC<sup>10+</sup>    | 30002 | 表示超声波指纹。   |

## 开发准备

1. 申请权限，申请流程请参考：[申请应用权限](../../security/AccessToken/determine-application-mode.md#system_basic等级应用申请权限的方式)。
   - ohos.permission.MANAGE_USER_IDM
   - ohos.permission.ACCESS_PIN_AUTH

2. 导入系统账号模块。

   <!-- @[import_system_account_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```


3. 创建凭据管理对象。

   <!-- @[create_credential_management_object](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
      let userIDM: osAccount.UserIdentityManager = new osAccount.UserIdentityManager();
```


## 注册PIN码输入器

输入器用于传递PIN码数据，录入、认证PIN码前需要先注册输入器。

具体开发实例如下：

1. 定义PIN码输入器，并获取PIN码。

   <!-- @[define_pin_inputer_pinData](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
      let pinData: Uint8Array = new Uint8Array([31, 32, 33, 34, 35, 36]);
	// ···
      let inputer: osAccount.IInputer = {
        onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
          callback.onSetData(authSubType, pinData);
        }
      }
```


2. 调用[registerInputer](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#registerinputer8)注册PIN码输入器。

   <!-- @[call_the_api_to_register_the_inputer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
      let PINAuth: osAccount.PINAuth = new osAccount.PINAuth();
	// ···
      PINAuth.registerInputer(inputer);
```


## 打开会话

在进行凭据管理前，请先打开一个新的会话。开发者可以使用[openSession](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#opensession8)接口完成此操作。

具体开发实例如下：

调用[openSession](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#opensession8)接口一个新的凭据管理会话。

   ```ts
   let session: Uint8Array = await userIDM.openSession();
   ```

## 录入PIN码

前述操作完成后，可以进行PIN码录入。开发者可以使用[addCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#addcredential8)接口完成此操作。

具体开发实例如下：

1. 定义PIN码凭据信息。

   <!-- @[define_pin_credential_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
      let credentialInfo :osAccount.CredentialInfo = {
		// ···
        credType:osAccount.AuthType.PIN,
        credSubType:osAccount.AuthSubType.PIN_SIX,
        token:new Uint8Array([0])
      };
```


2. 调用[addCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#addcredential8)接口添加指定的凭据信息，执行结果通过回调获取。

   <!-- @[call_the_api_to_add_the_specified_credentials](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        userIDM.addCredential(credentialInfo,{
          onResult: (err, extraInfo)=>{
            console.info('addCredential result: ' + JSON.stringify(err));
            console.info('edential info: ' + JSON.stringify(extraInfo));
			// ···
          }})
```


## 认证PIN码

录入完PIN码，用户可以进行PIN码认证。开发者可以使用[auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth8)接口完成此操作。

具体开发实例如下：

1. 定义认证参数，包括挑战值、认证类型、认证可信等级。

   **定义挑战值：**

   ```ts
   let challenge: Uint8Array = new Uint8Array([1, 2, 3, 4, 5]);
   ```

   **定义认证类型、认证可信等级：**

   <!-- @[define_parameters_pin_type_and_level_to_auth](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        let authType: osAccount.AuthType = osAccount.AuthType.PIN;
        let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
```


2. 调用[auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth8)接口进行认证。

   <!-- @[call_the_auth_operation_for_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        let userAuth: osAccount.UserAuth = new osAccount.UserAuth();
        userAuth.auth(challenge, authType, authTrustLevel, {
          onResult: (result: number, extraInfo: osAccount.AuthResult) => {
            console.info('pin auth result = ' + result);
            console.info('pin auth extraInfo = ' + JSON.stringify(extraInfo));
            let authToken = extraInfo.token;
			// ···
          }
        });
```


## 录入生物识别凭据

PIN码认证成功后，可以录入人脸/指纹，操作流程与录入PIN码类似。

具体开发实例如下：

1. 认证PIN码，获取授权令牌authToken。

2. 定义人脸凭据信息（以2D人脸为例）。

   <!-- @[define_facial_credential_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let faceCredInfo: osAccount.CredentialInfo = {
      credType: osAccount.AuthType.FACE,
      credSubType: osAccount.AuthSubType.FACE_2D,
      token: new Uint8Array([1, 2, 3, 4, 5])
    }
```


3. 调用[addCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#addcredential8)录入人脸凭据。

   <!-- @[input_facial_credential_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
            userIDM.addCredential(faceCredInfo, {
              onResult: (code: number, result: osAccount.RequestResult) => {
                console.info('add face credential, resultCode: ' + code);
                console.info('add face credential, request result: ' + result);
				// ···
              }
            });
```


4. 定义指纹凭据信息。

   <!-- @[define_fingerprint_credential_information](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let fingerprintCredInfo: osAccount.CredentialInfo = {
      credType: osAccount.AuthType.FINGERPRINT,
      credSubType: osAccount.AuthSubType.FINGERPRINT_CAPACITIVE,
      token: new Uint8Array([1, 2, 3, 4, 5])
    }
```


5. 调用[addCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#addcredential8)录入指纹凭据。

   <!-- @[enter_the_fingerprint_credentials](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
            userIDM.addCredential(fingerprintCredInfo, {
              onResult: (code: number, result: osAccount.RequestResult) => {
                console.info('add fingerprint credential, resultCode: ' + code);
                console.info('add fingerprint credential, request result: ' + result);
				// ···
              }
            });
```


## 认证生物识别凭据

录入生物识别凭据后，用户可以进行生物识别认证。类似PIN码认证，开发者可以使用[auth](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#auth8)接口完成此操作。

具体开发实例如下：

1. 定义认证参数（以人脸认证为例），包括挑战值、认证类型、认证可信等级。

   **定义挑战值：**

   ```ts
   let challenge: Uint8Array = new Uint8Array([1, 2, 3, 4, 5]);
   ```

   **定义认证类型、认证可信等级：**

   <!-- @[define_parameters_face_type_and_level_to_auth](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        let authType: osAccount.AuthType = osAccount.AuthType.FACE;
        let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
```


2. 调用auth接口进行认证。

   <!-- @[call_the_auth_operation_for_face_authentication](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
        let userAuth: osAccount.UserAuth = new osAccount.UserAuth();
        userAuth.auth(challenge, authType, authTrustLevel, {
          onResult: (result: number, extraInfo: osAccount.AuthResult) => {
            console.info('face auth result = ' + result);
            console.info('face auth extraInfo = ' + JSON.stringify(extraInfo));
			// ···
          }
        });
```



## 更新凭据

用户可以修改系统账号的凭据。开发者可以使用[updateCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#updatecredential8)接口完成此操作。

具体开发实例如下：

1. 认证PIN码，获取授权令牌authToken。

2. 定义待更新凭据信息。

   <!-- @[define_the_credential_information_to_be_updated](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let credentialInfo :osAccount.CredentialInfo = {
	// ···
      credType:osAccount.AuthType.PIN,
      credSubType:osAccount.AuthSubType.PIN_SIX,
      token:new Uint8Array([1, 2, 3, 4, 5])
    };
```



3. 调用[updateCredential](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#updatecredential8)更新凭据。

   <!-- @[update_your_credentials](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
          userIDM.updateCredential(credentialInfo, {
            onResult:(result: number, extraInfo: osAccount.RequestResult)=>{
              console.info('updateCredential result: ' + JSON.stringify(result));
              console.info('updateCredential extraInfo: ' + JSON.stringify(extraInfo));
			// ···
            }
          })
```


## 查询凭据信息

凭据管理界面需要向用户展示已录入的凭据信息；锁屏界面需要展示可认证的凭据类型。开发者可以使用[getAuthInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getauthinfo8)接口查询已录入的凭据信息，实现前述业务场景功能。

具体开发实例如下：

1. 查询所有已录入的凭据信息。

   ```ts
   let enrolledCredInfoList: osAccount.EnrolledCredInfo[] = await userIDM.getAuthInfo();
   ```

2. 调用[getAuthInfo](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#getauthinfo8)接口，获取指定类型的凭据信息（以指纹凭据为例）。

   <!-- @[obtain_credential_information_of_the_specified_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
      let enrolledFingerCredInfoList: osAccount.EnrolledCredInfo[] =
        await userIDM.getAuthInfo(osAccount.AuthType.PIN);
```


## 删除凭据

删除凭据前，需要先进行[认证PIN码](#认证pin码)，并获取待删除凭据的标识（参考[查询凭据信息](#查询凭据信息)）。

以删除指纹凭据为例，具体开发实例如下：

1. 获取指纹类型的凭据信息。

   <!-- @[obtain_the_credential_information_of_the_fingerprint_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
    let credentialId: Uint8Array = new Uint8Array([1, 2, 3, 4, 5]);
    let token: Uint8Array = new Uint8Array([1, 2, 3, 4, 5]);
    let credInfoList: osAccount.EnrolledCredInfo[] = 
      await userIDM.getAuthInfo(osAccount.AuthType.FINGERPRINT);
    if (credInfoList.length != 0) {
      credentialId = credInfoList[0].credentialId;
    }
```



2. [认证PIN码](#认证pin码)，获取授权令牌。

3. 调用[delCred](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#delcred8)接口，删除指定凭据。

   <!-- @[delete_specified_credentials](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
            userIDM.delCred(credentialId, authResult.token, {
              onResult: (result: number, extraInfo: osAccount.RequestResult) => {
                console.info('delCred result = ' + result);
                console.info('delCred extraInfo = ' + JSON.stringify(extraInfo));
				// ···
              }
            });
```


## 注销PIN码输入器

不再使用输入器时，可以调用[unregisterInputer](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#unregisterinputer8)注销PIN码输入器。

具体开发实例如下：

<!-- @[deactivate_pin_input_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
          PINAuth.unregisterInputer();
```


## 关闭会话

调用[closeSession](../../reference/apis-basic-services-kit/js-apis-osAccount-sys.md#closesession8)关闭会话，结束凭据管理。

具体开发实例如下：

<!-- @[close_the_session_and_end_credential_management](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Account/ManageSystemAccountCredentials/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
          userIDM.closeSession(this.cid);
```

