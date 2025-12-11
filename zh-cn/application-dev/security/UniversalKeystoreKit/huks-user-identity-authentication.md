# 用户身份认证访问控制开发指导

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

场景介绍及相关概念说明请参考[用户身份认证访问控制简介](huks-identity-authentication-overview.md)。

## 开发步骤

### 生成密钥

指定指纹访问控制类型及相关属性。

生成或导入密钥时，在密钥属性集中需指定三个参数：用户认证类型[HuksUserAuthType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksuserauthtype9)、授权访问类型[HuksAuthAccessType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksauthaccesstype9)、挑战值类型[HuksChallengeType](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukschallengetype9)。

<!-- @[user_authentication_key_generation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->

``` TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
import { userAuth } from '@kit.UserAuthenticationKit';

const KEY_ALIAS = 'test_sm4_key_alias';
const IV = '1234567890123456';
const CIPHER_IN_DATA = 'Hks_SM4_Cipher_Test_101010101010101010110_string';
const AUTH_TYPE = userAuth.UserAuthType.PIN;
const AUTH_TRUST_LEVEL = userAuth.AuthTrustLevel.ATL1;

let sessionHandle: number;
let challenge: Uint8Array;
let authToken: Uint8Array;
let encryptedData: Uint8Array;

class ThrowObject {
  public isThrow: boolean = false;
}

function stringToUint8Array(str: string): Uint8Array {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

/* 步骤1：密钥生成模块 */
const KEY_GENERATION_PROPERTIES: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT | huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_DECRYPT
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_USER_AUTH_TYPE,
    value: huks.HuksUserAuthType.HUKS_USER_AUTH_TYPE_PIN
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_AUTH_ACCESS_TYPE,
    value: huks.HuksAuthAccessType.HUKS_AUTH_ACCESS_INVALID_CLEAR_PASSWORD
  },
  {
    tag: huks.HuksTag.HUKS_TAG_CHALLENGE_TYPE,
    value: huks.HuksChallengeType.HUKS_CHALLENGE_TYPE_NORMAL
  }
];

/* 生成密钥 */
function generateKeyItem(keyAlias: string, huksOptions: huks.HuksOptions, throwObject: ThrowObject): Promise<void> {
  return new Promise<void>((resolve, reject) => {
    try {
      huks.generateKeyItem(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

/* 生成SM4密钥 */
async function step1GenerateKey(): Promise<void> {
  const generateOptions: huks.HuksOptions = {
    properties: KEY_GENERATION_PROPERTIES,
    inData: new Uint8Array([])
  };

  let throwObject: ThrowObject = { isThrow: true };
  try {
    await generateKeyItem(KEY_ALIAS, generateOptions, throwObject)
      .then((data) => {
        console.info('密钥生成成功');
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error('密钥生成失败: ' + JSON.stringify(error));
        }
      });
  } catch (error) {
    console.error('密钥生成参数错误: ' + JSON.stringify(error));
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}

/* 步骤2：初始化会话模块 - 初始化加密会话并获取挑战值 */
const INIT_SESSION_PROPERTIES: huks.HuksParam[] = [
  {
    tag: huks.HuksTag.HUKS_TAG_ALGORITHM,
    value: huks.HuksKeyAlg.HUKS_ALG_SM4,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PURPOSE,
    value: huks.HuksKeyPurpose.HUKS_KEY_PURPOSE_ENCRYPT,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_KEY_SIZE,
    value: huks.HuksKeySize.HUKS_SM4_KEY_SIZE_128,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_BLOCK_MODE,
    value: huks.HuksCipherMode.HUKS_MODE_CBC,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_PADDING,
    value: huks.HuksKeyPadding.HUKS_PADDING_NONE,
  },
  {
    tag: huks.HuksTag.HUKS_TAG_IV,
    value: stringToUint8Array(IV),
  }
];

/* 初始化会话 */
function initSession(keyAlias: string, huksOptions: huks.HuksOptions,
  throwObject: ThrowObject): Promise<huks.HuksSessionHandle> {
  return new Promise<huks.HuksSessionHandle>((resolve, reject) => {
    try {
      huks.initSession(keyAlias, huksOptions, (error, data) => {
        if (error) {
          reject(error);
        } else {
          resolve(data);
        }
      });
    } catch (error) {
      throwObject.isThrow = true;
      const err = error instanceof Error ? error : new Error(String(error));
      throw err;
    }
  });
}

/* 初始化会话并获取挑战值 */
async function step2InitSession(): Promise<void> {
  const initOptions: huks.HuksOptions = {
    properties: INIT_SESSION_PROPERTIES,
    inData: new Uint8Array([])
  };

  let throwObject: ThrowObject = { isThrow: true };
  try {
    await initSession(KEY_ALIAS, initOptions, throwObject)
      .then((data) => {
        sessionHandle = data.handle;
        challenge = data.challenge as Uint8Array;
        console.info('会话初始化成功，挑战值: ' + challenge.toString());
      })
      .catch((error: Error) => {
        if (throwObject.isThrow) {
          const err = error instanceof Error ? error : new Error(String(error));
          throw err;
        } else {
          console.error('会话初始化失败: ' + JSON.stringify(error));
        }
      });
  } catch (error) {
    console.error('会话初始化参数错误: ' + JSON.stringify(error));
    const err = error instanceof Error ? error : new Error(String(error));
    throw err;
  }
}
```

### 通过PIN码认证获取授权令牌
<!-- @[user_authentication_pin_verification](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->

### 使用认证令牌进行加密操作
<!-- @[user_authentication_data_encryption](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/UniversalKeystoreKit/KeyUsage/AccessControl/entry/src/main/ets/pages/UserIdentityAuthentication.ets) -->