# 指定用户身份操作（仅对系统应用开放）

<!--Kit: Universal Keystore Kit-->
<!--Subsystem: Security-->
<!--Owner: @wutiantian-gitee-->
<!--Designer: @HighLowWorld-->
<!--Tester: @wxy1234564846-->
<!--Adviser: @zengyawen-->

多用户并发进行密钥操作时，为了实现密钥数据隔离和访问控制，HUKS提供了额外的可以指定用户进行密钥操作的接口。

>**说明：**
>
> 轻量级设备不支持指定用户身份操作功能。

## 约束与限制

- 调用方的user id必须在0到99之间，包含0和99。
- 这部分接口是原有能力的增强，仅面向系统应用开放。

## 接口说明

这部分增强接口在现有功能接口的基础上增加了参数`userId`用于指定用户ID。

指定用户的接口额外支持以下功能和使用条件：

1. 使用方可以同时在options参数中传入HUKS_TAG_AUTH_STORAGE_LEVEL标签，以指定存储在指定用户的DE区、CE区或ECE区。

2. 使用方在options参数中不额外传入HUKS_TAG_AUTH_STORAGE_LEVEL标签时，该接口默认行为是：使用指定userId对应CE存储区的密钥。即不传入HUKS_TAG_AUTH_STORAGE_LEVEL参数，等同于传入值为HUKS_AUTH_STORAGE_LEVEL_CE的HUKS_TAG_AUTH_STORAGE_LEVEL参数。

除此之外指定用户的接口的用法和支持的算法规格，与不指定用户的对应接口一致。

| 指定用户的接口 | 说明 | 不指定用户的接口示例参考 |
| -------- | -------- | ----------| 
| generateKeyItemAsUser              |   生成密钥。           |  generateKeyItem             |
| deleteKeyItemAsUser                  |   删除密钥。           |  deleteKeyItem               |
| importKeyItemAsUser                  |   明文导入密钥。      |  importKeyItem                |
| importWrappedKeyItemAsUser    |  安全导入密钥。        |  importWrappedKeyItem             |
| exportKeyItemAsUser                  |   导出密钥。        |  exportKeyItem                |
| getKeyItemPropertiesAsUser    |  获取密钥属性。     |  getKeyItemProperties             |
| hasKeyItemAsUser                        |  查询密钥是否存在。    |  hasKeyItem               |
| initSessionAsUser                      |  初始化密钥会话。       |  initSession   加密解密 签名验签 密钥协商 密钥派生           |
| attestKeyItemAsUser                  |  非匿名密钥证明。    |  attestKeyItem                |
| anonAttestKeyItemAsUser          | 匿名密钥证明。     |  anonAttestKeyItem                |
