# 签名/验签介绍及算法规格

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

在密钥管理扩展场景下，完成密钥管理扩展PIN认证后，应用可通过resourceId操作对应密钥执行签名/验签操作。该能力通过HUKS提供的三段式接口实现，应用指定相应的算法参数即可（包括算法类型，目的，填充，摘要等）。

## 三段式接口

签名/验签操作通过HUKS的三段式接口实现，通过指定[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示指定密钥由密钥管理扩展服务中的密钥。

具体使用可参考[签名/验签(ArkTS)](huks-extension-ability-signing-signature-verification-arkts.md)和[签名/验签(C/C++)](huks-ukey-signing-signature-verification-ndk.md)。

| 步骤 | 接口 | 说明 |
|------|------|------|
| 1 | [initSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksinitsession9) | 初始化密钥会话，返回会话 handle |
| 2 | [updateSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksupdatesession9) | （可选）传入分段数据，执行中间密码运算 |
| 3 | [finishSession](../../reference/apis-universal-keystore-kit/js-apis-huks.md#huksfinishsession9) | 结束会话，返回最终结果（签名/验签结果） |

> **说明：**
>
> 1. 通过[HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag)指定密钥类别为[HUKS_KEY_CLASS_EXTENSION](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeyclasstype22)，表示该密钥由外部密钥管理扩展管理。
> 2. 三段式操作过程中，keyAlias参数需指定为resourceId。
> 3. finishSession完成后会释放会话句柄。
> 4. 签名/验签是否需要PIN认证取决于密钥用途：私钥签名需要PIN认证，公钥验签无需。

## 规格

具体规格与外部硬件密钥管理扩展实现相关，不同厂家实现有差异。

签名/验签操作需要在 HuksOptions.properties 中指定以下参数：

### 详细参数

| 参数 | 取值 | 必填 | 说明 |
|------|------|------|------|
| [HUKS_TAG_KEY_CLASS](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | `HUKS_KEY_CLASS_EXTENSION` | 是 | 表示由密钥管理扩展管理 |
| [HUKS_TAG_PURPOSE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 用途枚举值 | 否 | 指定用途，未传入则使用密钥管理扩展提供的默认值 |
| [HUKS_TAG_ALGORITHM](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 算法枚举值 | 否 | 指定签名/验签算法 |
| [HUKS_TAG_KEY_SIZE](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukstag) | 密钥长度 | 否 | 如 2048、3072、4096 |