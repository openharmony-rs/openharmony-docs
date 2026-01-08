# 通用查询(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API 22开始，huksExternalCrypto提供通用查询功能接口。该接口可以用于从UKey中调用获取设备标识、App标识以及其他通用属性信息的函数，完成属性查询操作。具体的场景介绍请参考[获取属性介绍及规格](huks-ukey-general-query-overview.md)。

## 开发步骤

**获取属性**

1. 通过[证书管理应用](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取[keyUri](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certreference22)作为resourceId，并[打开资源](huks-open-close-resource-ndk.md#打开资源)。

2. 构造输入参数propertyId和可选输入参数[param](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoparam)。

3. 调用[getProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetproperty)获取属性信息。


```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from "@kit.BasicServicesKit";

async function getProperty(): Promise<Array<huksExternalCrypto.HuksExternalCryptoParam>> {
  // 1. 获取resourceId, 假设获取的resourceId如下，并已经打开该资源
  const testResourceId = JSON.stringify({
    providerName: "testProviderName",
    bundleName: "com.example.cryptoapplication",
    abilityName: "CryptoExtension",
    index: {
      key: "testKey"
    } as ESObject
  });

  // 2. 构造输入参数propertyId和可选参数param
  let propertyId = "SKF_EnumDev";
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

  // 3. 调用getProperty获取属性信息
  console.info(`promise: await huksExternalCrypto getProperty`);
  try {
    await huksExternalCrypto.getProperty(testResourceId, propertyId, extProperties)
      .then((data) => {
        console.info(`promise: getProperty success, data: ` + JSON.stringify(data));
      }).catch((error: BusinessError) => {
        console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
      })
  } catch (error) {
    console.error(`promise: getProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
  }
  return extProperties;
}
```

