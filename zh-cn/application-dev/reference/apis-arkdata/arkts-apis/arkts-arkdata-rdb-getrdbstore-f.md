# getRdbStore

## 导入模块

```TypeScript
```

## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, version: number, callback: AsyncCallback<RdbStore>): void
```

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md)

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 FA模型的应用Context定义见Context。 Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| version | number | 是 | 数据库版本。 目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;RdbStore&gt; | 是 | 回调函数。当操作成功，err为undefined，data为RdbStore对象；否则为错误对象。 |

**示例**

FA模型示例：

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';
import relationalStore from '@ohos.data.relationalStore';
import window from '@ohos.window';
import { BusinessError } from '@ohos.base';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
data_rdb.getRdbStore(this.context, STORE_CONFIG, 1, (err, rdbStore) => {
  if (err) {
    console.error("Get RdbStore failed, err: " + err)
    return
  }
  console.info("Get RdbStore successfully.")
})
```

Stage模型示例：

```TypeScript
import UIAbility from '@ohos.app.ability.UIAbility';
import { BusinessError } from "@ohos.base";
import window from '@ohos.window';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    data_rdb.getRdbStore(this.context, STORE_CONFIG, 1, (err: BusinessError, rdbStore: data_rdb.RdbStore) => {
      if (err) {
        console.error("Get RdbStore failed, err: " + err)
        return
      }
      console.info("Get RdbStore successfully.")
    })
  }
}
```


## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, version: number): Promise<RdbStore>
```

获得一个相关的RdbStore，操作关系型数据库，用户可以根据自己的需求配置RdbStore的参数，然后通过RdbStore调用相关接口可以执行相关的数据操作，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用的上下文。 FA模型的应用Context定义见Context。 Stage模型的应用Context定义见Context。 |
| config | StoreConfig | 是 | 与此RDB存储相关的数据库配置。 |
| version | number | 是 | 数据库版本。 目前暂不支持通过version自动识别数据库升级降级操作，只能由开发者自行维护。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise &lt;RdbStore&gt; | Promise对象。返回RdbStore对象。 |

**示例**

FA模型示例：

```TypeScript
import featureAbility from '@ohos.ability.featureAbility';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
let promise = data_rdb.getRdbStore(this.context, STORE_CONFIG, 1);
promise.then(async (rdbStore) => {
  console.info("Get RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.error("Get RdbStore failed, err: " + err)
})
```

Stage模型示例：

```TypeScript
import UIAbility from '@ohos.app.ability.UIAbility';
import { BusinessError } from "@ohos.base";
import window from '@ohos.window';

const STORE_CONFIG: data_rdb.StoreConfig = { name: "RdbTest.db"}
class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage){
    context = this.context
  }
}

// 获取context后调用getRdbStore
let promise = data_rdb.getRdbStore(this.context, STORE_CONFIG, 1);
promise.then(async (rdbStore: data_rdb.RdbStore) => {
  console.info("Get RdbStore successfully.")
}).catch((err: BusinessError) => {
  console.error("Get RdbStore failed, err: " + err)
})
```
