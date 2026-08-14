# getRdbStore

## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback<RdbStore>): void
```

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用callback异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getRdbStore)

<!--Device-rdb-function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback<RdbStore>): void--><!--Device-rdb-function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback<RdbStore>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 &lt;br&gt;FA模型的应用Context定义见Context。 &lt;br&gt;Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| version | number | 是 | 数据库版本。 &lt;br&gt;目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;RdbStore&gt; | 是 | 回调函数。当操作成功，err为undefined，data为RdbStore对象；否则为错误对象。 |


## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, version: number): Promise<RdbStore>
```

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用Promise异步回调。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

<!--Device-rdb-function getRdbStore(context: Context, config: StoreConfig, version: number): Promise<RdbStore>--><!--Device-rdb-function getRdbStore(context: Context, config: StoreConfig, version: number): Promise<RdbStore>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 &lt;br&gt;FA模型的应用Context定义见Context。 &lt;br&gt;Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| version | number | 是 | 数据库版本。 &lt;br&gt;目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RdbStore&gt; | Promise对象。返回RdbStore对象。 |

