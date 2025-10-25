# 通过键值型数据库实现数据持久化 (ArkTS)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->


## 场景介绍

键值型数据库存储键值对形式的数据，当需要存储的数据没有复杂的关系模型，比如存储商品名称及对应价格、员工工号及今日是否已出勤等，由于数据复杂度低，更容易兼容不同数据库版本和设备类型，因此推荐使用键值型数据库持久化此类数据。


## 约束限制

- 设备协同数据库，针对每条记录，Key的长度≤896 Byte，Value的长度&lt;4 MB。

- 单版本数据库，针对每条记录，Key的长度≤1 KB，Value的长度&lt;4 MB。

- 每个应用程序最多支持同时打开16个键值型分布式数据库。

- 键值型数据库事件回调方法中不允许进行阻塞操作，例如修改UI组件。


## 接口说明

以下是键值型数据库持久化功能的相关接口，大部分为异步接口。异步接口均有callback和Promise两种返回形式，下表均以callback形式为例，更多接口及使用方式请见[分布式键值数据库](../reference/apis-arkdata/js-apis-distributedKVStore.md)。

| 接口名称 | 描述 | 
| -------- | -------- |
| createKVManager(config: KVManagerConfig): KVManager | 创建一个KVManager对象实例，用于管理数据库对象。 | 
| getKVStore&lt;T&gt;(storeId: string, options: Options, callback: AsyncCallback&lt;T&gt;): void | 指定options和storeId，创建并得到指定类型的KVStore数据库。 | 
| put(key: string, value: Uint8Array \| string \| number \| boolean, callback: AsyncCallback&lt;void&gt;): void | 添加指定类型的键值对到数据库。 | 
| get(key: string, callback: AsyncCallback\<boolean \| string \| number \| Uint8Array>): void | 获取指定键的值。 | 
| delete(key: string, callback: AsyncCallback&lt;void&gt;): void | 从数据库中删除指定键值的数据。 | 
| closeKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void | 通过storeId的值关闭指定的分布式键值数据库。 | 
| deleteKVStore(appId: string, storeId: string, callback: AsyncCallback&lt;void&gt;): void | 通过storeId的值删除指定的分布式键值数据库。 | 


## 开发步骤

1. 若要使用键值型数据库，首先要使用createKVManager()方法获取一个KVManager实例，用于管理数据库对象。示例代码如下所示：

   > **说明：**
   >
   > Logger封装示例参考[Logger](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/common/Logger.ets)。
   >
   > getContext参考EntryAbility.ets文件中的[getContext](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/entryability/EntryAbility.ets)接口。

   ```js
   // 导入模块
   // 在pages目录下新建KvStoreInterface.ets
   import { distributedKVStore } from '@kit.ArkData';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { distributedDeviceManager } from '@kit.DistributedServiceKit';
   import EntryAbility from '../entryability/EntryAbility';
   import Logger from '../common/Logger';

   let kvManager: distributedKVStore.KVManager | undefined = undefined;
   let kvStore: distributedKVStore.SingleKVStore | undefined = undefined;
   let appId: string = 'com.example.kvstoresamples';
   let storeId: string = 'storeId';
   // Stage模型context从EntryAbility.ets中获取
   const context = EntryAbility.getContext();

   // FA模型获取context
   import { featureAbility } from '@kit.AbilityKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   let context = featureAbility.getContext();

   // 下面所有接口的代码都实现在KvInterface中
   export class KvInterface {
   }
   ```
   <!-- @[kv_store1](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

2. 使用getKVStore()方法创建并获取键值数据库。示例代码如下所示：

   <!-- @[kv_store3](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

3. 使用on()方法订阅分布式数据变化，如需关闭订阅分布式数据变化，调用[off('dataChange')](../reference/apis-arkdata/js-apis-distributedKVStore.md#offdatachange)关闭。示例代码如下所示：

   <!-- @[kv_store12](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

4. 调用put()方法向键值数据库中插入数据。示例代码如下所示：

   <!-- @[kv_store4](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

   > **说明：**
   >
   > 当Key值存在时，put()方法会修改其值，否则新增一条数据。

5. 调用get()方法获取指定键的值。示例代码如下所示：

   <!-- @[kv_store5](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

6. 调用delete()方法删除指定键值的数据。示例代码如下所示：

   <!-- @[kv_store6](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

7. 调用closeKVStore()方法通过storeId的值关闭指定的分布式键值数据库。示例代码如下所示：

    <!-- @[kv_store10](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

8. 调用deleteKVStore()方法通过storeId的值删除指定的分布式键值数据库。示例代码如下所示：

    <!-- @[kv_store11](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkData/KvStore/KvStoreSamples/entry/src/main/ets/pages/KvStoreInterface.ets) -->

<!--RP1--><!--RP1End-->