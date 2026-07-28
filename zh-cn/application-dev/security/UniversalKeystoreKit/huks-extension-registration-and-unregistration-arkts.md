# 注册/注销(ArkTS)

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

从API版本22开始，huksExternalCrypto提供Provider注册和注销功能接口。

## 注册Provider

密钥管理扩展应用检测到密钥管理设备或服务可用时，向系统注册CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件、数字盾（虚拟智能卡）在应用启动或服务就绪时检测。详细规格见[注册注销](huks-extension-ability-support-overview.md#注册注销)。

### 开发步骤

1. 构造注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段，值为Ability名称的UTF-8字节流，长度为1-128字节。

2. 调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口，需捕获BusinessError处理失败。

### 示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8 字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 注册 Provider（仅注册 CryptoExtensionAbility，不注册自定义 PIN 弹窗）
async function registerProvider(): Promise<void> {
  // providerName 建议包含厂商+产品信息以保证全局唯一
  const providerName = 'VendorA_ProductX';
  // abilityName 须与 module.json5 中 extensionAbilities.name 保持一致
  const abilityName = 'CryptoExtensionAbility1';

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName),
    },
  ];

  try {
    await huksExternalCrypto.registerProvider(providerName, extProperties);
    console.info('promise: registerProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: registerProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testRegisterProvider(): Promise<void> {
  await registerProvider();
}
```

## 注册Provider并注册UIExtensionAbility

从API版本26.0.0开始，支持同步注册UIExtensionAbility到系统中。详细规格见[注册注销](huks-extension-ability-support-overview.md#注册注销)。

### 开发步骤

1. 构造注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段，值为Ability名称的UTF-8字节流。

2. 构造UIExtensionAbility注册参数，包含[HUKS_EXT_CRYPTO_TAG_ABILITY_INFO](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)字段。

3. 调用[registerProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoregisterprovider)接口，需捕获BusinessError处理失败。

### 示例

```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';
import { deviceInfo } from '@kit.BasicServicesKit';

// 字符串 → UTF-8 字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 自定义 PIN 弹窗 UIExtensionAbility 列表
const abilityInfoList: Array<{ abilityName: string; index: string }> = [
  { abilityName: 'UiAbility1', index: '' },
  { abilityName: 'UiAbility2', index: 'string2' },
];

// 注册 Provider 并注册自定义 PIN 弹窗 UIExtensionAbility
async function registerProvider(): Promise<void> {
  try {
    /* 1.构造注册参数 ability name */
    const providerName = "testProvider";
    /* 2.构造 ability info */
    const abilityInfo = '[' +
      '{"abilityName":"UiAbility1","index":""},' +
      '{"abilityName":"UiAbility2","index":"string2"}]';
    const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
      {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
        value: StringToUint8Array("CryptoExtension")
      }, {
        tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
        value: StringToUint8Array(abilityInfo)
      }
    ];

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName),
    },
  ];

  // API 26起支持自定义PIN弹窗注册
  if (deviceInfo.sdkApiVersion >= 26) {
    extProperties.push({
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_INFO,
      value: stringToUint8Array(JSON.stringify(abilityInfoList)),
    });
  }

  try {
    await huksExternalCrypto.registerProvider(providerName, extProperties);
    console.info('promise: registerProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: registerProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testRegisterProvider(): Promise<void> {
  await registerProvider();
}
```

## 注销Provider

密钥管理扩展应用检测到密钥管理设备或服务不可用时，从系统注销CryptoExtensionAbility。具体的可用性检测方式因接入的设备/服务形态而异，例如UKey物理设备监听USB插拔事件、数字盾（虚拟智能卡）在应用退出时检测。详细规格见[注册注销](huks-extension-ability-support-overview.md#注册注销)。


### 开发步骤

1. 构造注销参数，注销单个ability需要传入[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数。批量注销不需要传入[HUKS_EXT_CRYPTO_TAG_ABILITY_NAME](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)参数。

2. 调用注销接口[unregisterProvider](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptounregisterprovider)。

**注销单个ability**
```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8 字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 注销单个Ability：精确注销指定providerName+abilityName的CryptoExtensionAbility
async function unregisterProvider(): Promise<void> {
  // providerName须与注册时使用的名称一致
  const providerName = 'testProvider';
  // abilityName须与module.json5中extensionAbilities.name保持一致
  const abilityName = 'CryptoExtensionAbility1';

  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [
    {
      tag: huksExternalCrypto.HuksExternalCryptoTag.HUKS_EXT_CRYPTO_TAG_ABILITY_NAME,
      value: stringToUint8Array(abilityName),
    },
  ];

  try {
    await huksExternalCrypto.unregisterProvider(providerName, extProperties);
    console.info('promise: unregisterProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: unregisterProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testUnregisterProvider(): Promise<void> {
  await unregisterProvider();
}
```

**批量注销**
```ts
import { huksExternalCrypto } from '@kit.UniversalKeystoreKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { util } from '@kit.ArkTS';

// 字符串 → UTF-8 字节流
function stringToUint8Array(str: string): Uint8Array {
  return new util.TextEncoder().encodeInto(str);
}

// 批量注销：注销providerName下的所有CryptoExtensionAbility
async function unregisterProvider(): Promise<void> {
  // providerName 须与注册时使用的名称一致
  const providerName = 'testProvider';

  // 批量注销：extProperties 留空或不指定 HUKS_EXT_CRYPTO_TAG_ABILITY_NAME
  const extProperties: Array<huksExternalCrypto.HuksExternalCryptoParam> = [];

  try {
    await huksExternalCrypto.unregisterProvider(providerName, extProperties);
    console.info('promise: unregisterProvider success.');
  } catch (error) {
    const e = error as BusinessError;
    console.error(`promise: unregisterProvider failed, errCode: ${e.code}, errMsg: ${e.message}`);
  }
}

async function testUnregisterProvider(): Promise<void> {
  await unregisterProvider();
}
```