# 消息摘要计算MD5(ArkTS)

<!--Kit: Crypto Architecture Kit-->
<!--Subsystem: Security-->
<!--Owner: @zxz--3-->
<!--Designer: @lanming-->
<!--Tester: @PAFT-->
<!--Adviser: @zengyawen-->

对应的算法规格请查看[消息摘要计算算法规格](crypto-generate-message-digest-overview.md#支持的算法与规格)。

> **说明：**
> 
> 从API version 12开始，轻量级智能穿戴设备支持消息摘要的计算与操作。

## 开发步骤

在调用update接口传入数据时，可以[一次性传入所有数据](#摘要算法一次性传入)，也可以把数据人工分段，然后[分段update](#分段摘要算法)。对于同一段数据而言，计算结果没有差异。对于数据量较大的数据，开发者可以根据实际需求选择是否分段传入。

下面分别提供两种方式的示例代码。

### 摘要算法（一次性传入）

1. 调用[cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd)，指定摘要算法MD5，生成摘要实例（Md）。

2. 调用[Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-6)，传入自定义消息，进行摘要更新计算。单次update长度没有限制。

3. 调用[Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest)，获取摘要计算结果。

4. 调用[Md.getMdLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmdlength)，获取摘要计算长度，单位为字节。

- 以使用await方式单次传入数据，获取摘要计算结果为例：

<!-- @[message_digest_md5_single_time_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/md5/singleTime/SingleTimeAsync.ets) -->


- 以使用同步方式单次传入数据，获取摘要计算结果为例：

<!-- @[message_digest_md5_single_time_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/md5/singleTime/SingleTimeSync.ets) -->


### 分段摘要算法

1. 调用[cryptoFramework.createMd](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#cryptoframeworkcreatemd)，指定摘要算法MD5，生成摘要实例（Md）。

2. 传入自定义消息，将一次传入数据量设置为20字节，多次调用[Md.update](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#update-7)，进行摘要更新计算。

3. 调用[Md.digest](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#digest-1)，获取摘要计算结果。

4. 调用[Md.getMdLength](../../reference/apis-crypto-architecture-kit/js-apis-cryptoFramework.md#getmdlength)，获取摘要计算长度，单位为字节。

- 以使用await方式分段传入数据，获取摘要计算结果为例：

<!-- @[message_digest_md5_segmentation_async](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/md5/segmentation/SegmentationAsync.ets) -->


- 以使用同步方式分段传入数据，获取摘要计算结果为例：
<!-- @[message_digest_md5_segmentation_sync](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/Security/CryptoArchitectureKit/MessageDigestComputation/entry/src/main/ets/pages/md5/segmentation/SegmentationSync.ets) -->

