# 其它操作介绍及规格

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->


HUKS在密钥管理扩展场景下提供一组"其它操作"接口，覆盖资源标识、资源打开/关闭、查询、属性设置、错误信息获取等场景。除getResourceId和getErrorInfo外，其他操作（getProperty、setProperty等）均要求资源已打开。

## 整体关系

| 类别 | 涉及接口 | 调用阶段 | 是否需要资源已打开 | 详细文档 |
|------|---------|---------|-------------------|---------|
| 资源标识 | getResourceId | 任何操作之前 | 否 | [获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md) |
| 资源生命周期 | openResource/closeResource | 密钥管理扩展操作前/后 | — | [打开/关闭资源(ArkTS)](huks-open-close-resource-arkts.md) / [(C/C++)](huks-open-close-resource-ndk.md) |
| 通用查询 | getProperty | 资源已打开后 | 是 | [查询(ArkTS)](huks-extension-ability-general-query-arkts.md)/[(C/C++)](huks-extension-ability-general-query-ndk.md) |
| 属性设置 | setProperty | 资源已打开后 | 是 | [属性设置(ArkTS)](huks-extension-set-property-arkts.md) |
| 错误信息 | getErrorInfo | 任意操作失败后 | 否 | [获取错误信息(ArkTS)](huks-extension-ability-get-error-info-arkts.md) |

## 各接口详细规格

详细规格请参考各接口的独立文档：

| 接口 | ArkTS 文档 | C/C++ 文档 |
|------|----------|-----------|
| 资源标识 | [获取资源ID(ArkTS)](huks-extension-get-resource-id-arkts.md) | — |
| 打开/关闭资源 | [打开/关闭资源(ArkTS)](huks-open-close-resource-arkts.md) | [打开/关闭资源(C/C++)](huks-open-close-resource-ndk.md) |
| 通用查询 | [查询(ArkTS)](huks-extension-ability-general-query-arkts.md) | [查询(C/C++)](huks-extension-ability-general-query-ndk.md) |
| 属性设置 | [属性设置(ArkTS)](huks-extension-set-property-arkts.md) | — |
| 错误信息 | [获取错误信息(ArkTS)](huks-extension-ability-get-error-info-arkts.md) | — |



> **说明：**
>
> 1. resourceId是提供者的资源ID，用于标识要查询的远程资源，长度必须介于1-1024字节。接口的propertyId参数需要与密钥管理扩展服务实现方约定调用规则，长度为1-100字节，建议采用GM/T 0016-2023标准中定义的SKF函数名称。
> 2. 输出参数通过[HUKS_EXT_CRYPTO_TAG_EXTRA_DATA](../../reference/apis-universal-keystore-kit/js-apis-huksExternalCrypto.md#huksexternalcryptotag)携带，应用可以提取该查询出的属性数据，并按照和驱动应用（外部密钥管理扩展能力提供方）的约定，解析数据。