# 安全基础能力子系统变更说明

## cl.security.1 Crypto Architecture Kit的非对称密钥转换接口在解析包含长度超过2GB的原始元素的DER编码数据时由不确定行为变更为返回失败

**访问级别**

公开接口

**变更原因**

修复OpenSSL CVE-2026-34180漏洞，导致加解密算法框架服务接口有行为变更。

CVE-2026-34180是OpenSSL的ASN.1解码器存在整数截断问题，在解析包含长度超过2GB的原始元素的DER编码数据时，在64-bit Unix及类Unix平台上可能触发堆缓冲区越界读取，导致信息泄露或拒绝服务攻击。

**变更影响**

该变更为非兼容性变更。

变更前：调用算法库接口将外部DER编码的非对称密钥数据转换为算法库密钥对象时，若密钥数据包含长度超过2GB的原始元素，解析密钥数据时将产生不确定行为，如导致应用崩溃。

变更后：调用算法库接口将外部DER编码的非对称密钥数据转换为算法库密钥对象时，若密钥数据包含长度超过2GB的原始元素，解析密钥数据失败，接口将返回失败。

**起始 API Level**

10

**变更发生版本**

从OpenHarmony SDK 7.0.0.32版本开始。

**变更的接口/组件**

@ohos.security.cryptoFramework.d.ts文件中AsyKeyGenerator interface的convertKey、convertKeySync。

CryptoArchitectureKit/crypto_asym_key.h文件中的OH_CryptoAsymKeyGenerator_Convert接口。

**适配指导**

请不要使用超过2GB的DER编码的非对称密钥数据。正常情况下DER编码的非对称密钥数据长度不超过1KB，较大的RSA 8192密钥数据长度不超过5KB。


## cl.security.2 Device Certificate Kit中证书算法库框架的CMS解析接口在解析使用了非AEAD加密算法或小于4字节认证标签的带认证CMS封装数据消息时由可能返回成功变更为始终返回失败

**访问级别**

公开接口

**变更原因**

修复OpenSSL CVE-2026-34182漏洞，导致证书算法库框架解析使用了非AEAD加密算法或小于4字节认证标签的带认证CMS封装数据消息始终返回失败。

CVE-2026-34182是OpenSSL在处理带认证CMS封装数据消息时，对消息中的加密算法和认证标签长度字段未能进行有效验证，允许攻击者获取密钥等效功能或绕过完整性校验。

**变更影响**

该变更为非兼容性变更。

变更前：调用证书库解析带认证CMS封装数据消息，若CMS消息中使用了非AEAD加密算法或小于4字节认证标签，接口可能返回成功。

变更后：调用证书库解析带认证CMS封装数据消息，若CMS消息中使用了非AEAD加密算法或小于4字节认证标签，接口始终返回失败。

**起始 API Level**

22

**变更发生版本**

从OpenHarmony SDK 7.0.0.32版本开始。

**变更的接口/组件**

@ohos.security.cert.d.ts文件中CmsParser interface的decryptEnvelopedData接口。

**适配指导**

若带认证CMS封装数据消息中使用了非AEAD加密算法或小于4字节认证标签，您的应用将面临安全风险，请勿信任该CMS消息。正常情况下，带认证CMS封装数据消息会使用AEAD加密算法（如AES-GCM算法）以及大于4字节的认证标签（如AES-GCM算法的认证标签通常为16字节）。