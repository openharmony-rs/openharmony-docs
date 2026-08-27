# Template（系统接口）

指定订阅中的模板结构。

**起始版本：** 10

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { dataShare } from '@kit.ArkData';
```

## predicates

```TypeScript
predicates: Record<string, string>
```

指定模板的谓词。当调用 on 的回调时，谓词用于生成数据。仅适用于rdb存储数据。

**类型：** Record&lt;string, string&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## scheduler

```TypeScript
scheduler: string
```

指定模板的调度程序sql。其中嵌入自定义函数处理，目前预置自定义函数remindTimer处理。remindTimer在指定场景触发一次订阅刷新。触发场景：
1. 修改数据时且有订阅的情况下触发对应的调度程序sql语句。
2. 添加对应库第一个订阅的情况下触发对应的调度程序sql语句。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

## update

```TypeScript
update?: string
```

指定模板的update sql语句，未定义时默认值为空字符串。当调用 on 的回调时，update参数用于更新数据。仅适用于rdb存储数据。

**类型：** string

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Consumer

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
import { dataSharePredicates, ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
let key1: string = "name";
let value1: string = "roe1";
let key2: string = "age";
let value2: number = 21;
let key3: string = "salary";
let value3: number = 20.5;
const va: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).update(uri, da, va, (err: BusinessError, data: number) => {
      if (err !== undefined) {
        console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info("update succeed, data : " + data);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to update. Code: ${code}, message: ${message}`);
}
```

```TypeScript
import { dataSharePredicates, ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let uri = "datashare:///com.samples.datasharetest.DataShare";
let da = new dataSharePredicates.DataSharePredicates();
da.equalTo("name", "ZhangSan");
let key1: string = "name";
let value1: string = "roe1";
let key2: string = "age";
let value2: number = 21;
let key3: string = "salary";
let value3: number = 20.5;
const va: ValuesBucket = {
  key1: value1,
  key2: value2,
  key3: value3,
};
try {
  if (dataShareHelper != undefined) {
    (dataShareHelper as dataShare.DataShareHelper).update(uri, da, va).then((data: number) => {
      console.info("update succeed, data : " + data);
    }).catch((err: BusinessError) => {
      console.error(`Failed to update. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Failed to update. Code: ${code}, message: ${message}`);
}
```
