# 属性设置(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本22开始，huksExternalCrypto设置属性[setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty)接口。

## 规格说明

打开密钥管理扩展服务中的资源后，可调用该接口设置指定资源的属性值，由密钥管理扩展服务（即[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)）实现方提供具体的propertyId。具体的场景介绍请参考[获取属性介绍及规格](huks-ukey-general-query-overview.md)。// TODO

- resourceId为已通过[打开资源](huks-open-close-resource-arkts.md#打开资源)步骤打开的资源ID，长度为1-1024字节。

- propertyId需要与密钥管理扩展约定调用规则，长度为1-100字节。建议采用GM/T 0016-2023标准中定义的SKF函数名称。

> **PIN认证说明**：是否需要PIN认证取决于propertyId和密钥管理扩展的实现。设置设备名称等操作通常不需要，涉及密钥属性或敏感信息时，通常需要先完成PIN认证。

## 开发步骤

1. 通过[获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md)获取resourceId，并传入该resourceId[打开资源](huks-open-close-resource-arkts.md#打开资源)。

2. 构造propertyId和可选输入参数。

2. 调用[setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty)设置属性值。

## 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setProperty(resourceId: string, propertyId: string): Promise<void> {
  try {
    await huksExternalCrypto.setProperty(resourceId, propertyId)
      .then(() => console.info('promise: setProperty success.'))
      .catch((error: BusinessError) => {
        console.error(`promise: setProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: setProperty input arg invalid.');
  }
}
```