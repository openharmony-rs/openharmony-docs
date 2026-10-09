# 密钥封装机制介绍及算法规格

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

密钥封装机制（Key Encapsulation Mechanism，简称KEM）是一种通过非对称密钥在两方之间安全建立共享密钥的密码学机制。与传统密钥协商不同，密钥封装是单向操作：封装端使用公钥生成密文和共享密钥，解封装端使用私钥从密文中恢复共享密钥。

密钥封装与传统密钥协商的区别：

- **密钥协商（如ECDH、DH、X25519）：** 双向协商，双方各持私钥，交换公钥后各自计算出相同共享密钥。
- **密钥封装（如ML-KEM）：** 单向操作，封装端使用对端公钥生成密文和共享密钥，将密文发送给对端；解封装端使用私钥从密文恢复共享密钥，无需双向交换公钥。

ML-KEM（Module-Lattice-Based Key-Encapsulation Mechanism）是NIST FIPS 203标准定义的后量子密码算法，用于替代传统密钥协商算法以抵抗量子计算攻击。

密钥封装生成的共享密钥有两种处理方式：

- **存储到HUKS：** 封装或解封装时指定sharedKeyAlias和sharedKeyParams，共享密钥以指定别名存储到HUKS中，后续可通过该别名直接使用共享密钥进行加解密等操作。此方式下，封装和解封装返回结果中的sharedSecret字段为空。具体开发步骤请参考[密钥封装(ArkTS)](./huks-kem-arkts.md)中共享密钥托管到HUKS的示例。
- **导出到应用：** 封装或解封装时不指定sharedKeyAlias和sharedKeyParams，共享密钥通过封装和解封装返回结果中的sharedSecret字段导出给应用，由应用自行管理共享密钥的存储和使用。此方式下，应用需自行管理密钥。具体开发步骤请参考[密钥封装(ArkTS)](./huks-kem-arkts.md)中共享密钥不托管到HUKS的示例。

> **说明：**
>
> <!--RP1-->轻量级设备<!--RP1End-->不支持密钥封装功能。

## 支持的算法

以下为密钥封装支持的规格说明。
<!--Del-->
面向OpenHarmony的厂商适配密钥管理服务规格分为必选规格和可选规格。必选规格为所有厂商均支持的算法规格。而对于可选规格，厂商将基于实际情况决定是否实现，如需使用，请查阅具体厂商提供的说明，确保规格支持再使用。

**建议开发者使用必选规格开发应用，可保证全平台兼容。**
<!--DelEnd-->

| 算法 | 备注 | 公钥长度（字节） | 密文长度（字节） | 共享密钥长度（字节） | API级别 | <!--DelCol7-->是否必选规格 |
| -------- | -------- | -------- | -------- | -------- | -------- | -------- |
| ML-KEM-768 | 密钥封装类型为ML-KEM，密钥用途为[HUKS_KEY_PURPOSE_WRAP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose)和[HUKS_KEY_PURPOSE_UNWRAP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose)。 | 1184 | 784 | 32 | 26.0.0+ | 是 |
| ML-KEM-1024 | 密钥封装类型为ML-KEM，密钥用途为[HUKS_KEY_PURPOSE_WRAP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose)和[HUKS_KEY_PURPOSE_UNWRAP](../../reference/apis-universal-keystore-kit/js-apis-huks.md#hukskeypurpose)。 | 1568 | 912 | 32 | 26.0.0+ | 否 |