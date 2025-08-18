# @ohos.data.ValuesBucket (数据集)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @woodenarow-->
<!--Designer: @woodenarow; @xuelei3-->
<!--Tester: @chenwan188; @logic42-->
<!--Adviser: @ge-yafang-->

**数据集（ValuesBucket）** 是开发者向数据库插入的数据集合，数据集以键值对的形式进行传输。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 本模块接口仅可在Stage模型下使用。


## 导入模块

```ts
import { ValueType, ValuesBucket } from '@kit.ArkData';
```

## ValueType

type ValueType = number | string | boolean

该类型用于表示数据库允许的数据字段类型。

**系统能力：**  SystemCapability.DistributedDataManager.DataShare.Core

**原子化服务API：**  从API version 20开始，该接口支持在原子化服务中使用。

| 类型    | 说明                 |
| ------- | -------------------- |
| number  | 表示字段类型为数字。   |
| string  | 表示字段类型为字符串。 |
| boolean | 表示字段类型为布尔值。 |

## ValuesBucket

type ValuesBucket = Record<string, ValueType | Uint8Array | null>

用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。

**系统能力：**  SystemCapability.DistributedDataManager.DataShare.Core

| 类型          | 说明                                      |
| ------------- | --------------------------------------------- |
| Record<string, [ValueType](#valuetype) \| Uint8Array \| null> | 表示键值对类型。键的类型为string，值的类型为[ValueType](#valuetype) \| Uint8Array \| null。|
