# @ohos.security.huksExternalCrypto(External Key Management)

/*
 Copyright (c) 2025-2026 Huawei Device Co., Ltd.
 Licensed under the Apache License, Version 2.0 (the "License");
 you may not use this file except in compliance with the License.
 You may obtain a copy of the License at
 http://www.apache.org/licenses/LICENSE-2.0
 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
 /


**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-unnamed-declare namespace huksExternalCrypto--><!--Device-unnamed-declare namespace huksExternalCrypto-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [clearUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-clearukeypinauthstate-f.md#clearUkeyPinAuthState) | 清除指定资源ID的PIN码认证状态。使用Promise异步回调。 |
| [closeResource](arkts-universalkeystore-huksexternalcrypto-closeresource-f.md#closeResource) | 关闭指定资源ID的资源。使用Promise异步回调。 该接口会回调 [onClearUkeyPinAuthState](arkts-universalkeystore-security-cryptoextensionability-cryptoextensionability-c.md#onClearUkeyPinAuthState) 清理该资源关联的PIN认证状态，以及会回调 [onFinishSession](arkts-universalkeystore-security-cryptoextensionability-cryptoextensionability-c.md#onFinishSession) 清理该资源关联的会话handle。 |
| [getErrorInfo](arkts-universalkeystore-huksexternalcrypto-geterrorinfo-f.md#getErrorInfo) | 查询上次接口调用产生的详细错误信息。 |
| [getProperty](arkts-universalkeystore-huksexternalcrypto-getproperty-f.md#getProperty) | 调用此接口获取属性值并返回结果。使用Promise异步回调。 propertyId表示查询属性的ID信息，当前仅支持GMT 0016-2023中定义的SKF接口名作为属性ID，支持的ID包括如下： - SKF_EnumDev - SKF_GetDevInfo - SKF_EnumApplication - SKF_EnumContainer |
| [getResourceId](arkts-universalkeystore-huksexternalcrypto-getresourceid-f.md#getResourceId) | 获取密钥扩展能力的资源ID。使用Promise异步回调。 |
| [getUkeyPinAuthState](arkts-universalkeystore-huksexternalcrypto-getukeypinauthstate-f.md#getUkeyPinAuthState) | 获取PIN码认证状态。使用Promise异步回调。 |
| [openResource](arkts-universalkeystore-huksexternalcrypto-openresource-f.md#openResource) | 打开指定资源ID的资源。使用Promise异步回调。 |
| [registerProvider](arkts-universalkeystore-huksexternalcrypto-registerprovider-f.md#registerProvider) | 注册指定的外部provider。使用Promise异步回调。 若需使用自定义PIN码弹窗，在注册provider时需要同步注册UIExtensionAbility，注意事项如下： 1. 自定义ability通过UIExtensionAbility扩展实现。 2. 注册的UIExtensionAbility可以通过证书管理kit提供的[openUKeyAuthDialog](../../apis-device-certificate-kit/arkts-apis/arkts-security-certmanager.md#@ohos.security.certManager)接口统一拉起。 3. 系统拉起自定义弹窗时会通过want接口向开发者传递以下参数： - Action：string参数类型，在拉起自定义弹窗时want传输的Action为"UkeyPINAuth"。 - appUid：number参数类型，通过want.parameters传输。"appUid"字段为应用id，开发者可以通过该字段完成应用隔离。 - keyUri：string参数类型其值为resourceId，通过want.parameters传输，表示Ukey证书的索引。 4. 开发者实现UIExtensionAbility时，应用需根据指定场景返回对应的错误码： - 用户取消操作时，返回-1001。 - keyUri指定的证书/密钥不存在时，返回-1008。 - 参数格式错误时，返回-1014。 - 其余失败场景返回错误码-1000，成功时返回0。 |
| [setProperty](arkts-universalkeystore-huksexternalcrypto-setproperty-f.md#setProperty) | The set-type operations of the external crypto extension support calling custom interfaces. However, the custom interface must be registered with the provider. |
| [unregisterProvider](arkts-universalkeystore-huksexternalcrypto-unregisterprovider-f.md#unregisterProvider) | 注销指定的外部provider。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [authUkeyPin](arkts-universalkeystore-huksexternalcrypto-authukeypin-f-sys.md#authUkeyPin) | PIN码认证。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [HuksExternalCryptoParam](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptoparam-i.md) | 表示调用接口使用的param数组的类型。 |
| [HuksExternalErrorInfo](arkts-universalkeystore-huksexternalcrypto-huksexternalerrorinfo-i.md) | 详细错误信息 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [HuksExternalCryptoTag](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotag-e.md) | 表示调用参数的Tag。 |
| [HuksExternalCryptoTagType](arkts-universalkeystore-huksexternalcrypto-huksexternalcryptotagtype-e.md) | 表示外部加密数据类型的枚举。 |
| [HuksExternalPinAuthState](arkts-universalkeystore-huksexternalcrypto-huksexternalpinauthstate-e.md) | 枚举PIN认证的状态 |

