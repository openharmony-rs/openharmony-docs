# @ohos.security.huksExternalCrypto (外部密钥管理)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

模块提供外部密钥管理扩展功能的注册与注销，PIN码认证与认证状态获取等。

> **说明**
>
> 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
```

## HuksExternalCryptoTagType

表示外部加密数据类型的枚举。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称  | 值   | 说明    |
| ----- | ---- | -------- |
| HUKS_EXT_CRYPTO_TAG_TYPE_INT | 1 << 28   | 表示TAG的值为整数类型。 |
| HUKS_EXT_CRYPTO_TAG_TYPE_BYTES | 5 << 28  | 表示TAG的值为字节数组。 |

## HuksExternalCryptoTag

表示调用参数的Tag。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称    | 值   | 说明   |
| ------- | ---- | -------- |
| HUKS_EXT_CRYPTO_TAG_UKEY_PIN | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200001    | 表示PIN码的TAG。 |
| HUKS_EXT_CRYPTO_TAG_ABILITY_NAME | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200002    | 表示[CryptoExtensionAbility](js-apis-CryptoExtensionAbility.md)的名称。 |
| HUKS_EXT_CRYPTO_TAG_EXTRA_DATA | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200003    | 外部数据，在通用查询场景，表示返回的数据。 |
| HUKS_EXT_CRYPTO_TAG_UID | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT \| 200004    | 表示调用方的uid。 |
| HUKS_EXT_CRYPTO_TAG_PURPOSE | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_INT \| 200005    | 表示证书链对应密钥的使用类型，具体类型详见[CertificatePurpose定义](../apis-device-certificate-kit/js-apis-certManager.md#certificatepurpose22)。 |
| HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO<sup>26+</sup> | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200007    | 表示获取资源ID所需的信息，格式和内容由厂商自定义。 |
| HUKS_EXT_CRYPTO_TAG_BUNDLE_NAME<sup>26+</sup> | HuksExternalCryptoTagType.HUKS_EXT_CRYPTO_TAG_TYPE_BYTES \| 200009    | 表示CryptoExtensionAbility所属的HAP Bundle名称。 |

## HuksExternalCryptoParam

表示调用接口使用的param数组的类型。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称 | 类型        | 只读 | 可选 | 说明         |
| ------ | ----------------------------------- | ---- | ---- | ------------ |
| tag    | [HuksExternalCryptoTag](#huksexternalcryptotag)  | 否   | 否   | 参数标签，用于区分参数。 |
| value  | boolean\|number\|bigint\|Uint8Array | 否   | 否   | 标签对应值。 |

## HuksExternalPinAuthState

表示Ukey PIN码管理的状态值的枚举。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称    | 值   | 说明   |
| ------- | ---- | -------- |
| HUKS_EXT_CRYPTO_PIN_NO_AUTH | 0 | Ukey PIN未认证。 |
| HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED | 1 | Ukey PIN认证成功。 |
| HUKS_EXT_CRYPTO_PIN_LOCKED  | 2 | Ukey PIN已锁定。 |

## HuksExternalErrorInfo<sup>26+</sup>

表示详细错误信息的类型。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

| 名称 | 类型        | 只读 | 可选 | 说明         |
| ------ | ----------------------------------- | ---- | ---- | ------------ |
| errno    | number  | 否   | 否   | 详细错误码。 |
| errorDesc  | string | 否   | 否   | 详细错误描述。 |


## huksExternalCrypto.registerProvider

registerProvider(providerName: string, params: Array\<HuksExternalCryptoParam>): Promise\<void>

注册指定的外部provider。使用Promise异步回调。

**需要权限：** ohos.permission.CRYPTO_EXTENSION_REGISTER

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | -------|
| providerName | string | 是   | provider名称，最大长度为128。建议包含厂商信息，全局唯一，不要包含个人联系方式等敏感数据。<br>最多支持注册10个provider。 |
| params  | Array<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 是  | 操作时需传入的参数，必选TAG：[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag)，表示ability的名字，根据业务自己内部定义按照实际填写。 |

**返回值：**

| 类型  | 说明  |
| ------------- | --------|
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | check permission failed. |
| 801 | api is not supported. |
| 12000002 | the ability name param is missing. |
| 12000005 | IPC communication failed. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000019 | the provider is already registered. |
| 12000020 | an error occurred in the dependent module. |
| 12000025 | the number of providers exceeds the limit. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.registerProvider(providerName, extProperties)
    .then((data) => {
        console.info(`promise: registerProvider success`);
    });
```

## huksExternalCrypto.unregisterProvider

unregisterProvider(providerName: string, params?: Array\<HuksExternalCryptoParam>): Promise\<void>

注销指定的外部provider。使用Promise异步回调。

**需要权限：** ohos.permission.CRYPTO_EXTENSION_REGISTER

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型 | 必填 | 说明  |
| -------- | ------| ---- | -----|
| providerName | string | 是   | provider名称，最大长度为128。建议包含厂商信息，全局唯一，不要包含个人联系方式等敏感数据。如果provider注册了多个扩展能力，则该provider下的扩展能力都会被注销。 |
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 否 | 操作时需传入的参数。<br>可以在param参数中指定[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag)，将根据“包名 + providerName + abilityName”注销对应的cryptoExtensionAbility。<br>如果未在params参数中指定[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](#huksexternalcryptotag)，或者未传入params参数，则注销对应的providerName下的所有Provider。|

**返回值：**

| 类型   | 说明   |
| -------| ------ |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 201 | check permission failed. |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000011 | the provider is not found. |
| 12000012 | Device environment or input parameter is abnormal. This may happen for several reasons, such as the model already being unloaded. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const providerName = "testProviderName";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
    value: StringToUint8Array("CryptoExtension")
  }
];
huksExternalCrypto.unregisterProvider(providerName, extProperties)
    .then((data) => {
        console.info(`promise: unregisterProvider success`);
    });
```

## huksExternalCrypto.getUkeyPinAuthState

getUkeyPinAuthState(resourceId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<HuksExternalPinAuthState>

获取PIN码认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| resourceId | string | 是   | 资源ID，可通过[导出证书的接口](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取，其结果中附带资源ID。 |
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 否   | 操作的属性。非系统应用传入[HUKS_EXT_CRYPTO_TAG_UID](#huksexternalcryptotag)是非法参数。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<[HuksExternalPinAuthState](#huksexternalpinauthstate)> | Promise对象，返回认证结果。<br>HUKS_EXT_CRYPTO_PIN_NO_AUTH 表示未认证；HUKS_EXT_CRYPTO_PIN_AUTH_SUCCEEDED 表示认证成功；HUKS_EXT_CRYPTO_PIN_LOCKED 表示PIN被锁定。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | api is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | the Ukey driver operation failed. |
| 12000011 | queried entity does not exist. This may happen because the resource ID has not been opened. |
| 12000012 | Device environment or input parameter is abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | memory is insufficient. |
| 12000018 | the input parameter is invalid. |
| 12000020 | the provider operation failed. |
| 12000024 | the provider or Ukey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const testResourceId = "{\"providerName\":\"testProviderName\", \"bundleName\":\"com.example.cryptoapplication\", \"abilityName\":\"CryptoExtension\",\"index\":{\"key\":\"testKey\"}}";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];
huksExternalCrypto.getUkeyPinAuthState(testResourceId, extProperties)
    .then((data) => {
      console.info(`promise: getUkeyPinAuthState success, data: ${data}`);
    });
```

## huksExternalCrypto.getProperty

getProperty(resourceId: string, propertyId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<Array\<HuksExternalCryptoParam>>

调用此接口获取属性值并返回结果。使用Promise异步回调。

propertyId表示查询属性的ID信息，当前仅支持GMT 0016-2023中定义的SKF接口名作为属性ID，支持的ID包括如下：

- SKF_EnumDev
- SKF_GetDevInfo
- SKF_EnumApplication
- SKF_EnumContainer

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| resourceId | string | 是   | 资源ID，可通过[导出证书的接口](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取，该接口的返回结果中附带resourceId。 |
| propertyId | string | 是   | 查找操作的属性名称，是GMT 0016-2023中定义的SKF接口名，应用开发者需要针对接口名进行适配。 |
| params  | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 否   | 需要传递给[Extension Ability](js-apis-CryptoExtensionAbility.md)的输入参数。非系统应用传入[HUKS_EXT_CRYPTO_TAG_UID](#huksexternalcryptotag)是非法参数。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)>> | Promise对象，返回调用接口的结果。当调用成功时，返回结果为HuksExternalCryptoParam类型的数组，包含要查询的属性。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | API is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | If the Ukey driver operation failed. Possible causes: 1. Error reported when the provider accesses the SKF interface of Ukey. |
| 12000011 | If the cached resource ID is not found. |
| 12000012 | Device environment or input parameter is abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | If the memory is insufficient. |
| 12000018 | Input parameter is invalid. Possible causes: 1. The resourceId or propertyId length is invalid. 2. The params contains invalid tags or invalid value types. |
| 12000020 | If the provider operation failed. Possible causes: 1. The provider experienced an internal processing error. |
| 12000021 | The Ukey PIN is locked. |
| 12000023 | The Ukey PIN is not authenticated. |
| 12000024 | If the provider or Ukey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

let propertyId = "SKF_EnumDev";
const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

console.info(`promise: await huksExternalCrypto getProperty`);
async function testFunction() : Promise<void>
{
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ` + JSON.stringify(data));
      });
  } catch (error) {
    console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
}
```

## huksExternalCrypto.clearUkeyPinAuthState<sup>26+</sup>

clearUkeyPinAuthState(resourceId: string): Promise\<void>

清除指定资源ID的PIN码认证状态。使用Promise异步回调。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| resourceId | string | 是   | 资源ID。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | API is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | Failed to call the UKey driver interface. Please check the UKey connection and driver status. |
| 12000011 | The cached resource ID not found. |
| 12000012 | Device environment or input parameters are abnormal. This may occur if the process function is null, or due to other issues. |
| 12000014 | The memory is insufficient. |
| 12000018 | The input parameters are invalid. Possible causes: 1. The resourceId length is invalid. |
| 12000020 | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| 12000024 | The provider or UKey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

huksExternalCrypto.clearUkeyPinAuthState(testResourceId)
    .then(() => {
      console.info(`promise: clearUkeyPinAuthState success`);
    });
```

## huksExternalCrypto.getResourceId<sup>26+</sup>

getResourceId(params: Array\<HuksExternalCryptoParam>): Promise\<string>

获取密钥扩展能力的资源ID。使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| params | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 是   | 获取资源ID所需的属性参数，资源信息通过[HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO](#huksexternalcryptotag26)参数携带。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<string> | Promise对象，返回资源ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | API is not supported. |
| 12000005 | IPC communication failed. |
| 12000011 | The cached resource ID not found. |
| 12000012 | Device environment or input parameters are abnormal. This may occur if the process function is null, or due to other issues. |
| 12000014 | The memory is insufficient. |
| 12000018 | The input parameters are invalid. Possible causes: 1. The params contains invalid tags or invalid value types. |
| 12000020 | The provider operation failed. |
| 12000024 | The provider or UKey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

function StringToUint8Array(str: string) {
  let arr: number[] = [];
  for (let i = 0, j = str.length; i < j; ++i) {
    arr.push(str.charCodeAt(i));
  }
  return new Uint8Array(arr);
}

const resourceInfo = JSON.stringify({
  deviceName: "testDevice",
  appName: "testApp",
  containerName: "testContainer"
});

const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
  {
    tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_RESOURCE_INFO,
    value: StringToUint8Array(resourceInfo)
  }
];

huksExternalCrypto.getResourceId(extProperties)
    .then((resourceId) => {
      console.info(`promise: getResourceId success, resourceId: ${resourceId}`);
    });
```

## huksExternalCrypto.openResource<sup>26+</sup>

openResource(resourceId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<void>

打开指定资源ID的资源。使用Promise异步回调。

> **说明：**
>
> 打开的资源必须使用[closeResource](#huksexternalcryptoopenresource26)关闭。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| resourceId | string | 是   | 资源ID。可通过[证书选择接口](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取keyUri作为resourceId，或通过[getResourceId](#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。 |
| params | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 否   | 输入操作参数。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | API is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | Failed to call the UKey driver interface. Please check the UKey connection and driver status. |
| 12000011 | The cached resource ID is not found. This may happen because the resource ID has not been opened. |
| 12000012 | Device environment or input parameters are abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | The memory is insufficient. |
| 12000017 | The resource with the resource ID is already open. |
| 12000018 | Input parameters are invalid. Possible causes: 1. The resourceId length is invalid. 2. The parameters contain invalid tags or invalid value types. |
| 12000020 | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| 12000024 | The provider or UKey is busy. |
| 12000025 | The opened resources exceed the limit. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

huksExternalCrypto.openResource(testResourceId)
    .then(() => {
      console.info(`promise: openResource success`);
    });
```

## huksExternalCrypto.closeResource<sup>26+</sup>

closeResource(resourceId: string, params?: Array\<HuksExternalCryptoParam>): Promise\<void>

关闭指定资源ID的资源。使用Promise异步回调。

该接口会回调[onClearUkeyPinAuthState](js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonclearukeypinauthstate)清理该资源关联的PIN认证状态，以及会回调[onFinishSession](js-apis-CryptoExtensionAbility.md#cryptoextensionabilityonfinishsession)清理该资源关联的会话handle。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

**参数：**

| 参数名   | 类型  | 必填 | 说明  |
| -------- | ------- | ---- | ----------|
| resourceId | string | 是   | 资源ID。可通过[证书选择接口](../apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取keyUri作为resourceId，或通过[getResourceId](#huksexternalcryptogetresourceid26)获取外部密钥管理扩展的资源ID。 |
| params | Array\<[HuksExternalCryptoParam](#huksexternalcryptoparam)> | 否   | 输入操作参数。 |

**返回值：**

| 类型   | 说明   |
| -------- | ------- |
| Promise\<void> | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[HUKS错误码](errorcode-huks.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 801 | API is not supported. |
| 12000005 | IPC communication failed. |
| 12000006 | Failed to call the UKey driver interface. Please check the UKey connection and driver status. |
| 12000012 | Device environment or input parameters are abnormal. This error may occur if the process function is not found, or due to other issues. |
| 12000014 | The memory is insufficient. |
| 12000018 | Input parameters are invalid. Possible causes: 1. The resourceId length is invalid. 2. The parameters contain invalid tags or invalid value types. |
| 12000020 | The provider operation failed. This means an error occurred in the crypto extension before calling the UKey driver interface. |
| 12000024 | The provider or UKey is busy. |

**示例：**

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';

const testResourceId = JSON.stringify({
  providerName: "testProviderName",
  bundleName: "com.example.cryptoapplication",
  abilityName: "CryptoExtension",
  index: {
    key: "testKey"
  } as ESObject
});

huksExternalCrypto.closeResource(testResourceId)
    .then(() => {
      console.info(`promise: closeResource success`);
    });
```
