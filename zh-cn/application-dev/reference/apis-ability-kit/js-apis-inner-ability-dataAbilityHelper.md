# DataAbilityHelper

可以通过[acquireDataAbilityHelper](js-apis-ability-featureAbility.md#featureabilityacquiredataabilityhelper7)接口获取DataAbilityHelper对象。

> **说明：**
> 
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import ability from '@ohos.ability.ability';
```

## 使用说明

使用前根据具体情况引入如下模块
```ts
import ohos_data_ability from '@ohos.data.dataAbility';
import relationalStore from '@ohos.data.relationalStore';
```

## DataAbilityHelper.openFile

openFile(uri: string, mode: string, callback: AsyncCallback\<number>): void

打开指定uri对应的文件，返回文件描述符。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                   | 必填 | 说明                               |
| -------- | ---------------------- | ---- | ---------------------------------- |
| uri      | string                 | 是   | 表示待打开文件的uri。           |
| mode     | string                 | 是   | 表示文件打开模式，可以设置为‘r’表示只读访问，‘w’表示只写访问，‘rw’表示读写访问等。            |
| callback | AsyncCallback\<number> | 是   | 回调函数，返回文件描述符。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let mode = 'rw';
DAHelper.openFile('dataability:///com.example.DataAbility', mode, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`openFile fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`openFile success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.openFile

openFile(uri: string, mode: string): Promise\<number>

打开指定uri对应的文件，返回文件描述符。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明                     |
| ---- | ------ | ---- | ------------------------ |
| uri  | string | 是   | 表示待打开文件的uri。 |
| mode | string | 是   | 表示文件打开模式，可以设置为‘r’表示只读访问，‘w’表示只写访问，‘rw’表示读写访问等。  |

**返回值：**

| 类型             | 说明             |
| ---------------- | ---------------- |
| Promise\<number> | Promise对象，返回文件说明符。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let mode = 'rw';
DAHelper.openFile('dataability:///com.example.DataAbility', mode).then((data) => {
    console.info(`openFile data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.on('dataChange')

on(type: 'dataChange', uri: string, callback: AsyncCallback\<void>): void

注册观察者以监听uri指定数据的数据变化通知。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| type     | string               | 是   | 表示监听操作类型，'dataChange'表示数据变化操作。               |
| uri      | string               | 是   | 表示待监听数据变化的uri。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当注册观察者以监听uri指定数据的数据变化通知成功，err为undefined，否则为错误对象。   |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
function onChangeNotify() {
    console.info('onChangeNotify call back');
};
DAHelper.on(
    'dataChange',
    'dataability:///com.example.DataAbility',
    onChangeNotify
);
```

## DataAbilityHelper.off('dataChange')

off(type: 'dataChange', uri: string, callback?: AsyncCallback\<void>): void

注销观察者以停止监听uri指定数据的数据变化通知。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| type     | string               | 是   | 表示监听操作类型，'dataChange'表示数据变化操作。               |
| uri      | string               | 是   | 表示待取消监听数据变化的uri。 |
| callback | AsyncCallback\<void> | 否   | 回调函数。当注销观察者以停止监听uri指定数据的数据变化通知成功，err为undefined，否则为错误对象。       |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
function onChangeNotify() {
    console.info('onChangeNotify call back');
};
DAHelper.off(
    'dataChange',
    'dataability:///com.example.DataAbility',
    onChangeNotify
);
DAHelper.off(
    'dataChange',
    'dataability:///com.example.DataAbility',
);
```

## DataAbilityHelper.getType

getType(uri: string, callback: AsyncCallback\<string>): void

获取给定uri指向数据的媒体资源类型。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                   | 必填 | 说明                                          |
| -------- | ---------------------- | ---- | --------------------------------------------- |
| uri      | string                 | 是   | 表示待获取数据的uri。                      |
| callback | AsyncCallback\<string> | 是   | 回调函数，返回与uri指向数据匹配的媒体资源类型。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.getType('dataability:///com.example.DataAbility', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`getType fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`getType success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.getType

getType(uri: string): Promise\<string>

获取给定uri指向数据的媒体资源类型。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明                     |
| ---- | ------ | ---- | ------------------------ |
| uri  | string | 是   | 表示待获取数据的uri。 |

**返回值：**

| 类型             | 说明                                |
| ---------------- | ----------------------------------- |
| Promise\<string> | Promise对象，返回与uri指向数据匹配的媒体资源类型。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.getType('dataability:///com.example.DataAbility').then((data) => {
    console.info(`getType data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.getFileTypes

getFileTypes(uri: string, mimeTypeFilter: string, callback: AsyncCallback<Array\<string>>): void

获取支持的文件媒体资源类型。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名           | 类型                           | 必填 | 说明                               |
| -------------- | ------------------------------ | ---- | ---------------------------------- |
| uri            | string                         | 是   | 表示待获取文件的uri。           |
| mimeTypeFilter | string                         | 是   | 表示待获取文件的媒体资源类型。       |
| callback       | AsyncCallback\<Array\<string>> | 是   | 回调函数，返回匹配的媒体资源类型数组。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.getFileTypes( 'dataability:///com.example.DataAbility', 'image/*', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`getFileTypes fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`getFileTypes success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.getFileTypes

getFileTypes(uri: string, mimeTypeFilter: string): Promise\<Array\<string>>

获取支持的文件媒体资源类型。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名           | 类型   | 必填 | 说明                         |
| -------------- | ------ | ---- | ---------------------------- |
| uri            | string | 是   | 表示待获取文件的uri。     |
| mimeTypeFilter | string | 是   | 表示待获取文件的媒体资源类型。 |

**返回值：**

| 类型                     | 说明                     |
| ------------------------ | ------------------------ |
| Promise\<Array\<string>> | Promise对象，返回匹配的媒体资源类型数组。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.getFileTypes('dataability:///com.example.DataAbility', 'image/*').then((data) => {
    console.info(`getFileTypes data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.normalizeUri

normalizeUri(uri: string, callback: AsyncCallback\<string>): void

将引用数据功能的给定uri转换为规范化uri。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                   | 必填 | 说明                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| uri      | string                 | 是   | 表示要规范化的uri对象。                                      |
| callback | AsyncCallback\<string> | 是   | 回调函数，如果数据功能支持uri规范化，则返回规范化uri对象；否则返回null。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.normalizeUri('dataability:///com.example.DataAbility', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`normalizeUri fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`normalizeUri success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.normalizeUri

normalizeUri(uri: string): Promise\<string>

将引用数据功能的给定uri转换为规范化uri。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ---- | ------ | ---- | ----------------------- |
| uri  | string | 是   | 表示要规范化的uri对象。 |

**返回值：**

| 类型             | 说明                                                   |
| ---------------- | ------------------------------------------------------ |
| Promise\<string> | Promise对象，如果数据功能支持uri规范化，则返回规范化uri对象；否则返回null。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.normalizeUri('dataability:///com.example.DataAbility',).then((data) => {
    console.info(`normalizeUri data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.denormalizeUri

denormalizeUri(uri: string, callback: AsyncCallback\<string>): void

将由normalizeUri（uri）生成的给定规范化uri转换为非规范化uri。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                   | 必填 | 说明                                                |
| -------- | ---------------------- | ---- | --------------------------------------------------- |
| uri      | string                 | 是   | 表示要反规范化的uri对象。                             |
| callback | AsyncCallback\<string> | 是   | 回调函数，返回反规范化uri对象。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.denormalizeUri('dataability:///com.example.DataAbility', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`denormalizeUri fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`denormalizeUri success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.denormalizeUri

denormalizeUri(uri: string): Promise\<string>

将由normalizeUri（uri）生成的给定规范化uri转换为非规范化uri。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ---- | ------ | ---- | ----------------------- |
| uri  | string | 是   | 表示要规范化的uri对象。 |

**返回值：**

| 类型             | 说明                                      |
| ---------------- | ----------------------------------------- |
| Promise\<string> |Promise对象，返回反规范化uri对象。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.denormalizeUri('dataability:///com.example.DataAbility',).then((data) => {
    console.info(`denormalizeUri data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.notifyChange

notifyChange(uri: string, callback: AsyncCallback\<void>): void

通知注册的观察者，uri指定数据的数据变化。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名     | 类型                 | 必填 | 说明                     |
| -------- | -------------------- | ---- | ------------------------ |
| uri      | string               | 是   | 表示数据变化的uri。 |
| callback | AsyncCallback\<void> | 是   | 回调函数。当通知注册的观察者成功，err为undefined，否则为错误对象。               |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.notifyChange('dataability:///com.example.DataAbility', (error) => {
    if (error && error.code !== 0) {
        console.error(`notifyChange fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log('notifyChange success');
    }
});
```

## DataAbilityHelper.notifyChange

notifyChange(uri: string): Promise\<void>

通知注册的观察者，uri指定数据的数据变化。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名 | 类型   | 必填 | 说明                     |
| ---- | ------ | ---- | ------------------------ |
| uri  | string | 是   | 表示数据变化的uri。 |

**返回值：**

| 类型           | 说明                  |
| -------------- | --------------------- |
| Promise\<void> | Promise对象。无返回结果的Promise对象。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.notifyChange('dataability:///com.example.DataAbility').then(() => {
    console.info('================>notifyChangeCallback================>');
});
```

## DataAbilityHelper.insert

insert(uri: string, valuesBucket: [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket), callback: AsyncCallback\<number>): void

将单个数据记录插入数据库。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                   | 必填 | 说明                                                   |
| ------------ | ---------------------- | ---- | ------------------------------------------------------ |
| uri          | string                 | 是   | 表示要插入数据的uri。                               |
| valuesBucket | [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)       | 是   | 表示要插入的数据记录。如果此参数为空，将插入一个空行。 |
| callback     | AsyncCallback\<number> | 是   | 回调函数，返回插入数据记录的索引。                     |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
const valueBucket: rdb.ValuesBucket = {
    'name': 'rose',
    'age': 22,
    'salary': 200.5,
    'blobType': 'u8',
};
DAHelper.insert('dataability:///com.example.DataAbility', valueBucket, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`insert fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`insert success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.insert

insert(uri: string, valuesBucket: [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)): Promise\<number>

将单个数据记录插入数据库。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型             | 必填 | 说明                                                   |
| ------------ | ---------------- | ---- | ------------------------------------------------------ |
| uri          | string           | 是   | 表示要插入数据的uri。                               |
| valuesBucket | [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket) | 是   | 表示要插入的数据记录。如果此参数为空，将插入一个空行。 |

**返回值：**

| 类型             | 说明                     |
| ---------------- | ------------------------ |
| Promise\<number> | Promise对象，返回插入数据记录的索引。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
const valueBucket: rdb.ValuesBucket = {
    'name': 'rose1',
    'age': 221,
    'salary': 20.5,
    'blobType': 'u8',
};
DAHelper.insert('dataability:///com.example.DataAbility', valueBucket).then((data) => {
    console.info(`insert data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.batchInsert

batchInsert(uri: string, valuesBuckets: Array\<rdb.ValuesBucket>, callback: AsyncCallback\<number>): void

将多个数据记录插入数据库。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。
**参数：**

| 参数名         | 类型                    | 必填 | 说明                             |
| ------------ | ----------------------- | ---- | -------------------------------- |
| uri          | string                  | 是   | 表示要插入数据的uri。         |
| valuesBuckets | Array\<[rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)> | 是   | 表示要插入的数据记录数组。           |
| callback     | AsyncCallback\<number>  | 是   | 回调函数，返回插入的数据记录数。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let cars = new Array({'name': 'roe11', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket,
                     {'name': 'roe12', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket,
                     {'name': 'roe13', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket);
DAHelper.batchInsert('dataability:///com.example.DataAbility', cars, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`batchInsert fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`batchInsert success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.batchInsert

batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>): Promise\<number>

将多个数据记录插入数据库。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                    | 必填 | 说明                     |
| ------------ | ----------------------- | ---- | ------------------------ |
| uri          | string                  | 是   | 表示要插入数据的uri。 |
| valuesBuckets | Array<[rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)> | 是   | 表示要插入的数据记录数组。   |

**返回值：**

| 类型             | 说明                   |
| ---------------- | ---------------------- |
| Promise\<number> | Promise对象，返回插入的数据记录数。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let cars = new Array({'name': 'roe11', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket,
                     {'name': 'roe12', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket,
                     {'name': 'roe13', 'age': 21, 'salary': 20.5, 'blobType': 'u8',} as rdb.ValuesBucket);
DAHelper.batchInsert('dataability:///com.example.DataAbility', cars).then((data) => {
    console.info(`batchInsert data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.delete

delete(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback\<number>): void

从数据库中删除一个或多个数据记录。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要删除数据的uri。                         |
| predicates | dataAbility.DataAbilityPredicates | 是   | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |
| callback     | AsyncCallback\<number>            | 是   | 回调函数，返回已删除的数据记录数。               |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.delete('dataability:///com.example.DataAbility', da, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`delete fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`delete success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.delete

delete(uri: string, predicates?: dataAbility.DataAbilityPredicates): Promise\<number>

从数据库中删除一个或多个数据记录。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要删除数据的uri。                         |
| predicates | dataAbility.DataAbilityPredicates | 否   | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |

**返回值：**

| 类型             | 说明                     |
| ---------------- | ------------------------ |
| Promise\<number> | Promise对象，返回已删除的数据记录数。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.delete('dataability:///com.example.DataAbility', da).then((data) => {
    console.info(`delete data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.delete

delete(uri: string, callback: AsyncCallback\<number>): void

predicates筛选条件为空，自定义数据库删除数据记录的处理逻辑。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要删除数据的uri。                         |
| callback     | AsyncCallback\<number>            | 是   | 回调函数，返回已删除的数据记录数。               |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.delete('dataability:///com.example.DataAbility', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`delete fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`delete success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.update

update(uri: string, valuesBucket: [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket), predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback\<number>): void

更新数据库中的数据记录。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要更新数据的uri。                         |
| valuesBucket | [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)                  | 是   | 表示要更新的数据。                               |
| predicates   | dataAbility.DataAbilityPredicates | 是   | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |
| callback     | AsyncCallback\<number>            | 是   | 回调函数，返回更新的数据记录数。                 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
const va: rdb.ValuesBucket = {
    'name': 'roe1',
    'age': 21,
    'salary': 20.5,
    'blobType': 'u8',
};
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.update('dataability:///com.example.DataAbility', va, da, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`update fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`update success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.update

update(uri: string, valuesBucket: [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket), predicates?: dataAbility.DataAbilityPredicates): Promise\<number>

更新数据库中的数据记录。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要更新数据的uri。                         |
| valuesBucket | [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)                  | 是   | 表示要更新的数据。                               |
| predicates   | dataAbility.DataAbilityPredicates | 否   | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |

**返回值：**

| 类型             | 说明                                         |
| ---------------- | -------------------------------------------- |
| Promise\<number> | Promise对象，返回更新的数据记录数。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
const va: rdb.ValuesBucket = {
    'name': 'roe1',
    'age': 21,
    'salary': 20.5,
    'blobType': 'u8',
};
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.update('dataability:///com.example.DataAbility', va, da).then((data) => {
    console.info(`update data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.update

update(uri: string, valuesBucket: [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket), callback: AsyncCallback\<number>): void

predicates筛选条件为空，自定义更新数据库的处理逻辑。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名         | 类型                              | 必填 | 说明                                             |
| ------------ | --------------------------------- | ---- | ------------------------------------------------ |
| uri          | string                            | 是   | 表示要更新数据的uri。                         |
| valuesBucket | [rdb.ValuesBucket](../apis-arkdata/js-apis-data-rdb.md#valuesbucket)                  | 是   | 表示要更新的数据。                               |
| callback     | AsyncCallback\<number>            | 是   | 回调函数，返回更新的数据记录数。                 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import rdb from '@ohos.data.rdb';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
const va: rdb.ValuesBucket = {
    'name': 'roe1',
    'age': 21,
    'salary': 20.5,
    'blobType': 'u8',
};
DAHelper.update('dataability:///com.example.DataAbility', va, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`update fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`update success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.query

query(uri: string, columns: Array\<string>, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback\<ResultSet>): void

查询数据库中的数据。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                            | 是   | 表示要查询数据的uri。                         |
| columns    | Array\<string>                | 是   | 表示要查询的列。如果此参数为空，则查询所有列。   |
| predicates | dataAbility.DataAbilityPredicates | 是   | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |
| callback   | AsyncCallback\<[ResultSet](../apis-arkdata/js-apis-data-relationalStore.md#resultset)>         | 是   | 回调函数，返回查询结果。                         |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let cars=new Array('value1', 'value2', 'value3', 'value4');
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.query('dataability:///com.example.DataAbility', cars, da, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`query fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`query success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.query

query(uri: string, callback: AsyncCallback\<ResultSet>): void

查询数据库中的数据。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                            | 是   | 表示要查询数据的uri。                         |
| callback   | AsyncCallback\<[ResultSet](../apis-arkdata/js-apis-data-relationalStore.md#resultset)>         | 是   | 回调函数，返回查询结果。                         |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
DAHelper.query('dataability:///com.example.DataAbility', (error, data) => {
    if (error && error.code !== 0) {
        console.error(`query fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`query success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.query

query(uri: string, columns: Array\<string>, callback: AsyncCallback\<ResultSet>): void

查询数据库中的数据。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                            | 是   | 表示要查询数据的uri。                         |
| columns    | Array\<string>                | 是   | 表示要查询的列。如果此参数为空，则查询所有列。   |
| callback   | AsyncCallback\<[ResultSet](../apis-arkdata/js-apis-data-relationalStore.md#resultset)>         | 是   | 回调函数，返回查询结果。                         |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let cars = new Array('value1', 'value2', 'value3', 'value4');
DAHelper.query('dataability:///com.example.DataAbility', cars, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`query fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`query success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.query

query(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback\<ResultSet>): void

查询数据库中的数据。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                            | 是   | 表示要查询数据的uri。                         |
| predicates | dataAbility.DataAbilityPredicates | 是   | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |
| callback   | AsyncCallback\<[ResultSet](../apis-arkdata/js-apis-data-relationalStore.md#resultset)>         | 是   | 回调函数，返回查询结果。                         |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.query('dataability:///com.example.DataAbility', da, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`query fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`query success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.query

query(uri: string, columns?: Array\<string>, predicates?: dataAbility.DataAbilityPredicates): Promise\<ResultSet>

查询数据库中的数据。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                            | 是   | 表示要查询数据的uri。                         |
| columns    | Array\<string>               | 否   | 表示要查询的列。如果此参数为空，则查询所有列。   |
| predicates | dataAbility.DataAbilityPredicates | 否   | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |

**返回值：**

| 类型                | 说明           |
| ------------------- | -------------- |
| Promise\<[ResultSet](../apis-arkdata/js-apis-data-relationalStore.md#resultset)> | Promise对象，返回查询结果。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import ohos_data_ability from '@ohos.data.dataAbility';

let DAHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.DataAbility'
);
let cars = new Array('value1', 'value2', 'value3', 'value4');
let da = new ohos_data_ability.DataAbilityPredicates();
DAHelper.query('dataability:///com.example.DataAbility', cars, da).then((data) => {
    console.info(`query data: ${JSON.stringify(data)}`);
});
```

## DataAbilityHelper.call

call(uri: string, method: string, arg: string, extras: PacMap, callback: AsyncCallback\<PacMap>): void

调用DataAbility的扩展接口。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                 | 是   | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'           |
| method    | string                  | 是   | 表示被调用的方法名。   |
| arg      | string                   | 是   | 表示需传入的参数。      |
| extras   | [PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap)        | 是   | 表示扩展的键值对参数。       |
| callback | AsyncCallback\<[PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap)> | 是 | 回调函数，返回扩展的键值对参数。     |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

let dataAbilityHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.jsapidemo.UserDataAbility'
);
dataAbilityHelper.call('dataability:///com.example.jsapidemo.UserDataAbility',
    'method', 'arg', {'key1':'value1'}, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`call fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`call success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.call

call(uri: string, method: string, arg: string, extras: PacMap): Promise\<PacMap>

调用DataAbility的扩展接口。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名       | 类型                              | 必填 | 说明                                             |
| ---------- | --------------------------------- | ---- | ------------------------------------------------ |
| uri        | string                 | 是   | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'           |
| method    | string                  | 是   | 表示被调用的方法名。   |
| arg      | string                   | 是   | 表示需传入的参数。      |
| extras   | [PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap)        | 是   | 表示扩展的键值对参数。       |

**返回值：**

| 类型 | 说明 |
|------ | ------- |
|Promise\<[PacMap](js-apis-inner-ability-dataAbilityHelper.md#pacmap)> | Promise对象，返回扩展的键值对参数。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import { BusinessError } from '@ohos.base';

let dataAbilityHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.jsapidemo.UserDataAbility'
);
dataAbilityHelper.call('dataability:///com.example.jsapidemo.UserDataAbility',
    'method', 'arg', {'key1':'value1'}).then((data) => {
    console.info('call success, data: ${data}');
}).catch((error: BusinessError) => {
    console.error('call failed, error: ${error}');
});
```

## DataAbilityHelper.executeBatch

executeBatch(uri: string, operations: Array\<DataAbilityOperation>, callback: AsyncCallback\<Array\<DataAbilityResult>>): void

批量操作数据库中的数据。使用callback异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名        | 类型                          | 必填 | 说明                                             |
| ----------| ---------------------------------| ---- | ------------------------------------------------ |
| uri       | string                           | 是   | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。|
| operations    |  Array\<[DataAbilityOperation](js-apis-inner-ability-dataAbilityOperation.md)>        | 是   | 表示数据操作数组，其中可以包含对数据库的多个不同操作。   |
| callback      |  AsyncCallback\<Array\<[DataAbilityResult](js-apis-inner-ability-dataAbilityResult.md)>>    | 是   | 回调函数，在DataAbilityResult数组中返回每个操作的结果。      |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';

// 根据DataAbilityOperation列表选择要对数据库做的操作
let op: Array<ability.DataAbilityOperation> = new Array();
let dataAbilityHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.jsapidemo.UserDataAbility'
);
dataAbilityHelper.executeBatch('dataability:///com.example.jsapidemo.UserDataAbility', op, (error, data) => {
    if (error && error.code !== 0) {
        console.error(`executeBatch fail, error: ${JSON.stringify(error)}`);
    } else {
        console.log(`executeBatch success, data: ${JSON.stringify(data)}`);
    }
});
```

## DataAbilityHelper.executeBatch

executeBatch(uri: string, operations: Array\<DataAbilityOperation>): Promise\<Array\<DataAbilityResult>>

批量操作数据库中的数据。使用Promise异步回调。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

**模型约束**：此接口仅可在FA模型下使用。

**参数：**

| 参数名          | 类型                            | 必填 | 说明                                             |
| ----------    | -------------------------------| ---- | ------------------------------------------------ |
| uri           | string                         | 是   | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。|
| operations    |  Array\<[DataAbilityOperation](js-apis-inner-ability-dataAbilityOperation.md)>  | 是   | 表示数据操作数组，其中可以包含对数据库的多个不同操作。   |

**返回值：**

| 类型 | 说明 |
|------ | ------- |
|Promise\<Array\<[DataAbilityResult](js-apis-inner-ability-dataAbilityResult.md)>> | Promise对象，在DataAbilityResult数组中返回每个操作的结果。 |

**示例：**

<!--code_no_check_fa-->
```ts
import ability from '@ohos.ability.ability';
import featureAbility from '@ohos.ability.featureAbility';
import { BusinessError } from '@ohos.base';

// 根据DataAbilityOperation列表选择要对数据库做的操作
let op: Array<ability.DataAbilityOperation> = new Array();
let dataAbilityHelper: ability.DataAbilityHelper = featureAbility.acquireDataAbilityHelper(
    'dataability:///com.example.jsapidemo.UserDataAbility'
);
dataAbilityHelper.executeBatch('dataability:///com.example.jsapidemo.UserDataAbility', op).then((data) => {
    console.info('executeBatch success, data: ${data}');
}).catch((error: BusinessError) => {
    console.error('executeBatch failed, error: ${error}');
});

```

## PacMap

用于存储数据的PacMap类型。

**系统能力**：SystemCapability.Ability.AbilityRuntime.FAModel

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ----- | ---- | ---- | ---- | ---- |
| [key: string]  | number \| string \| boolean \| Array\<string \| number \| boolean> \| null  | 否 | 否 | 数据存储在键值对中。 |
