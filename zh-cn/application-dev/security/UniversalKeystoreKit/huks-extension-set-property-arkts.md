# 属性设置(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本26.0.0开始，huksExternalCrypto提供设置属性的功能接口。应用可通过setProperty接口设置指定资源的属性值，由[CryptoExtensionAbility](../../reference/apis-universal-keystore-kit/js-apis-CryptoExtensionAbility.md)实现方提供，推荐使用GMT 0016-2023中定义的SKF接口名作为属性ID。具体的场景介绍及规格，请参考[通用查询介绍及规格](huks-ukey-general-query-overview.md)。

## 开发步骤

1. 获取资源ID。可通过[openAuthorizeDialog](../../reference/apis-device-certificate-kit/js-apis-certManagerDialog.md#certificatemanagerdialogopenauthorizedialog22)获取keyUri作为resourceId，或通过[getResourceId](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetresourceid)获取外部密钥管理扩展的资源ID。

2. 调用[setProperty](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptosetproperty)设置属性值。

## 开发案例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';

async function setProperty(resourceId: string, propertyId: string): Promise<void> {
  try {
    await huksExternalCrypto.setProperty(resourceId, propertyId)
      .then(() => {
        console.info('promise: setProperty success.');
      }).catch((error: BusinessError) => {
        console.error(`promise: setProperty failed, errCode : ${error.code}, errMsg : ${error.message}`);
      });
  } catch (error) {
    console.error('promise: setProperty input arg invalid.');
  }
}
```