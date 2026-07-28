# PIN码认证介绍及规格

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

PIN（Personal Identification Number）码是密钥管理扩展服务中的安全访问凭证，服务实现方可以采用"凭证+PIN码"的双因子认证模式：用户必须同时拥有有效的凭证（如物理设备、虚拟服务会话等）和正确的PIN码，才能访问服务内的密钥材料。

PIN码作用如下：

1. 防暴力破解：连续错误输入达到一定次数（与密钥管理扩展服务实现相关）后自动锁定。

2. 硬件级安全：PIN码验证在密钥管理扩展服务内完成，敏感信息不离开服务。

密钥管理扩展服务使用resourceId标识资源，生态应用打开资源之后，如需要操作resourceId对应的私钥执行签名操作，则需要先验证PIN码。

## PIN码认证状态管理

HUKS提供以下PIN码认证状态管理能力：

- **查询认证状态**：通过[getUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptogetukeypinauthstate)查询当前PIN码认证状态。
- **清除认证状态**：从API版本26.0.0开始，可通过[clearUkeyPinAuthState](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptoclearukeypinauthstate)清除指定资源的PIN码认证状态。

### 清除认证状态使用场景

以下场景可能需要清除PIN码认证状态：

- 密钥操作完成后，主动清除认证状态，避免认证状态残留。
- 应用退出或切换用户时，清除认证状态。
- 认证状态异常时，重置认证状态。

具体开发示例可参考[查询认证状态(ArkTS)](huks-query-authentication-status-arkts.md)、[查询认证状态(C/C++)](huks-query-authentication-status-ndk.md)、[清除PIN码认证状态(ArkTS)](huks-clear-pin-auth-state-arkts.md)。

> **说明：**
>
> HUKS提供PIN码认证能力和认证状态查询能力。应用PIN码认证之前，可以先查询认证状态。如果需要PIN码认证，则需要拉起[证书管理应用](../DeviceCertificateKit/certManager-overview.md)，完成PIN码认证。
