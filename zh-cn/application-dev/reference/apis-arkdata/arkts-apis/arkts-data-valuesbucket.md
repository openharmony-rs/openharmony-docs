# @ohos.data.ValuesBucket

**ValuesBucket**  是开发者向数据库插入的数据集合，数据集以键值对的形式进行传输。


## 导入模块

```TypeScript
import { ValueType, ValuesBucket } from '@kit.ArkData';
```

## 汇总

### 类型

| 名称 | 说明 |
| --- | --- |
| [ValuesBucket](arkts-arkdata-valuesbucket-t.md) | 用于存储键值对的类型。该类型不是多线程安全的，如果应用中存在多线程同时操作该类派生出的实例，注意加锁保护。 |
| [ValueType](arkts-arkdata-valuetype-t.md) | 该类型用于表示数据库允许的数据字段类型。 |
