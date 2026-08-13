# RdbPredicates

表示关系型数据库（RDB）的谓词。该类确定RDB中条件表达式的值是true还是false。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md#RdbPredicates)

<!--Device-rdb-class RdbPredicates--><!--Device-rdb-class RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## and

```TypeScript
and(): RdbPredicates
```

向谓词添加和条件。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [and](arkts-arkdata-relationalstore-rdbpredicates-c.md#and)

<!--Device-RdbPredicates-and(): RdbPredicates--><!--Device-RdbPredicates-and(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回带有和条件的Rdb谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
    .and()
    .equalTo("SALARY", 200.5)
```

## beginWrap

```TypeScript
beginWrap(): RdbPredicates
```

向谓词添加左括号。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [beginWrap](arkts-arkdata-relationalstore-rdbpredicates-c.md#beginWrap)

<!--Device-RdbPredicates-beginWrap(): RdbPredicates--><!--Device-RdbPredicates-beginWrap(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回带有左括号的Rdb谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()
```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): RdbPredicates
```

配置谓词以匹配数据字段为string且值以指定字符串开头的字段。该方法等同于SQL语句中的"LIKE 'xxx%'"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [beginsWith](arkts-arkdata-relationalstore-rdbpredicates-c.md#beginsWith)

<!--Device-RdbPredicates-beginsWith(field: string, value: string): RdbPredicates--><!--Device-RdbPredicates-beginsWith(field: string, value: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值，长度不超过1024字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了以指定字符串开头条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.beginsWith("NAME", "os")
```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): RdbPredicates
```

将谓词配置为匹配数据字段为ValueType且value在给定范围内的指定字段。该方法等同于SQL语句中的"BETWEEN"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [between](arkts-arkdata-relationalstore-rdbpredicates-c.md#between)

<!--Device-RdbPredicates-between(field: string, low: ValueType, high: ValueType): RdbPredicates--><!--Device-RdbPredicates-between(field: string, low: ValueType, high: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| low | ValueType | 是 | 指示与谓词匹配的最小值。 |
| high | ValueType | 是 | 指示要与谓词匹配的最大值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了在给定范围内条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.between("AGE", 10, 50)
```

## constructor

```TypeScript
constructor(name: string)
```

构造函数。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md#RdbPredicates)

<!--Device-RdbPredicates-constructor(name: string)--><!--Device-RdbPredicates-constructor(name: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 数据库表名，不能为空字符串。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
```

## contains

```TypeScript
contains(field: string, value: string): RdbPredicates
```

配置谓词以匹配数据字段为string且value包含指定值的字段。该方法等同于SQL语句中的"LIKE '%xxx%'"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [contains](arkts-arkdata-relationalstore-rdbpredicates-c.md#contains)

<!--Device-RdbPredicates-contains(field: string, value: string): RdbPredicates--><!--Device-RdbPredicates-contains(field: string, value: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值，长度不超过1024字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了包含指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.contains("NAME", "os")
```

## distinct

```TypeScript
distinct(): RdbPredicates
```

配置谓词以过滤重复记录并仅保留其中一个。该方法等同于SQL语句中的"DISTINCT"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [distinct](arkts-arkdata-relationalstore-rdbpredicates-c.md#distinct)

<!--Device-RdbPredicates-distinct(): RdbPredicates--><!--Device-RdbPredicates-distinct(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回可用于过滤重复记录的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").distinct()
```

## endWrap

```TypeScript
endWrap(): RdbPredicates
```

向谓词添加右括号。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [endWrap](arkts-arkdata-relationalstore-rdbpredicates-c.md#endWrap)

<!--Device-RdbPredicates-endWrap(): RdbPredicates--><!--Device-RdbPredicates-endWrap(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回带有右括号的Rdb谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap()
```

## endsWith

```TypeScript
endsWith(field: string, value: string): RdbPredicates
```

配置谓词以匹配数据字段为string且值以指定字符串结尾的字段。该方法等同于SQL语句中的"LIKE '%xxx'"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [endsWith](arkts-arkdata-relationalstore-rdbpredicates-c.md#endsWith)

<!--Device-RdbPredicates-endsWith(field: string, value: string): RdbPredicates--><!--Device-RdbPredicates-endsWith(field: string, value: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值，长度不超过1024字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了以指定字符串结尾条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.endsWith("NAME", "se")
```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为ValueType且值等于指定值的字段。该方法等同于SQL语句中的"="。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [equalTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#equalTo)

<!--Device-RdbPredicates-equalTo(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-equalTo(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了等于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "lisi")
```

## glob

```TypeScript
glob(field: string, value: string): RdbPredicates
```

配置RdbPredicates匹配数据字段为string且值符合指定通配符模式的字段，其中*匹配任意多个字符，?匹配单个字符。该方法等同于SQL语句中的"GLOB"

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [glob](arkts-arkdata-relationalstore-rdbpredicates-c.md#glob)

<!--Device-RdbPredicates-glob(field: string, value: string): RdbPredicates--><!--Device-RdbPredicates-glob(field: string, value: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值，长度不超过1024字节 &lt;br&gt;支持通配符，*表示0个、1个或多个数字或字符，?表示1个数字或字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了匹配指定通配符模式条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.glob("NAME", "?h*g")
```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为ValueType且值大于指定值的字段。该方法等同于SQL语句中的">"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [greaterThan](arkts-arkdata-relationalstore-rdbpredicates-c.md#greaterThan)

<!--Device-RdbPredicates-greaterThan(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-greaterThan(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了大于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.greaterThan("AGE", 18)
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为ValueType且value大于或等于指定值的字段。该方法等同于SQL语句中的">="。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [greaterThanOrEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#greaterThanOrEqualTo)

<!--Device-RdbPredicates-greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-greaterThanOrEqualTo(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了大于或等于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.greaterThanOrEqualTo("AGE", 18)
```

## groupBy

```TypeScript
groupBy(fields: Array<string>): RdbPredicates
```

配置RdbPredicates按指定列分组查询结果。该方法等同于SQL语句中的"GROUP BY"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [groupBy](arkts-arkdata-relationalstore-rdbpredicates-c.md#groupBy)

<!--Device-RdbPredicates-groupBy(fields: Array<string>): RdbPredicates--><!--Device-RdbPredicates-groupBy(fields: Array<string>): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fields | Array&lt;string&gt; | 是 | 指定分组依赖的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回分组查询列的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.groupBy(["AGE", "NAME"])
```

## in

```TypeScript
in(field: string, value: Array<ValueType>): RdbPredicates
```

配置RdbPredicates以匹配数据字段为ValueType数组且值在给定范围内的指定字段。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [in](arkts-arkdata-relationalstore-rdbpredicates-c.md#in)

<!--Device-RdbPredicates-in(field: string, value: Array<ValueType>): RdbPredicates--><!--Device-RdbPredicates-in(field: string, value: Array<ValueType>): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | Array&lt;ValueType&gt; | 是 | 以ValueType型数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了值在给定范围内条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.in("AGE", [18, 20])
```

## inAllDevices

```TypeScript
inAllDevices(): RdbPredicates
```

同步分布式数据库时连接到组网内所有的远程设备。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [inAllDevices](arkts-arkdata-relationalstore-rdbpredicates-c.md#inAllDevices)

<!--Device-RdbPredicates-inAllDevices(): RdbPredicates--><!--Device-RdbPredicates-inAllDevices(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了所有远程设备同步条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.inAllDevices()
```

## inDevices

```TypeScript
inDevices(devices: Array<string>): RdbPredicates
```

同步分布式数据库时连接到组网内指定的远程设备。 > **说明：** > > 其中devices通过调用&lt;!--RP2--&gt; > [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#getTrustedDeviceListSync) > 方法得到。&lt;!--RP2End--&gt;deviceManager模块的接口均为系统接口，仅系统应用可用。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [inDevices](arkts-arkdata-relationalstore-rdbpredicates-c.md#inDevices)

<!--Device-RdbPredicates-inDevices(devices: Array<string>): RdbPredicates--><!--Device-RdbPredicates-inDevices(devices: Array<string>): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| devices | Array&lt;string&gt; | 是 | 指定的组网内的远程设备ID，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了指定远程设备同步条件的谓词。 |

## 示例

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let dmInstance: deviceManager.DeviceManager;
let deviceIds: Array<string> = [];
let devices: Array<string> = [];

deviceManager.createDeviceManager("com.example.appdatamgrverify", (err: BusinessError, manager: void) => {
  if (err) {
    console.error("create device manager failed, err=" + err);
    return;
  }
  dmInstance = manager;
  devices = dmInstance.getTrustedDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].deviceId;
  }
})

let predicates = new data_rdb.RdbPredicates("EMPLOYEE");
predicates.inDevices(deviceIds);
```

## indexedBy

```TypeScript
indexedBy(field: string): RdbPredicates
```

配置RdbPredicates以指定索引列。该方法等同于SQL语句中的"INDEXED BY"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [indexedBy](arkts-arkdata-relationalstore-rdbpredicates-c.md#indexedBy)

<!--Device-RdbPredicates-indexedBy(field: string): RdbPredicates--><!--Device-RdbPredicates-indexedBy(field: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 索引列的名称，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回具有指定索引列的RdbPredicates。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.indexedBy("SALARY_INDEX")
```

## isNotNull

```TypeScript
isNotNull(field: string): RdbPredicates
```

配置谓词以匹配值不为null的指定字段。该方法等同于SQL语句中的"IS NOT NULL"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [isNotNull](arkts-arkdata-relationalstore-rdbpredicates-c.md#isNotNull)

<!--Device-RdbPredicates-isNotNull(field: string): RdbPredicates--><!--Device-RdbPredicates-isNotNull(field: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了值不为null条件的谓词。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2 . Incorrect parameter types. |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.isNotNull("NAME")
```

## isNull

```TypeScript
isNull(field: string): RdbPredicates
```

配置谓词以匹配值为null的字段。该方法等同于SQL语句中的"IS NULL"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [isNull](arkts-arkdata-relationalstore-rdbpredicates-c.md#isNull)

<!--Device-RdbPredicates-isNull(field: string): RdbPredicates--><!--Device-RdbPredicates-isNull(field: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了值为null条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.isNull("NAME")
```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为valueType且value小于指定值的字段。该方法等同于SQL语句中的"<"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [lessThan](arkts-arkdata-relationalstore-rdbpredicates-c.md#lessThan)

<!--Device-RdbPredicates-lessThan(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-lessThan(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了小于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.lessThan("AGE", 20)
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为ValueType且value小于或等于指定值的字段。该方法等同于SQL语句中的"<="。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [lessThanOrEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#lessThanOrEqualTo)

<!--Device-RdbPredicates-lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-lessThanOrEqualTo(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了小于或等于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.lessThanOrEqualTo("AGE", 20)
```

## like

```TypeScript
like(field: string, value: string): RdbPredicates
```

配置谓词以匹配数据字段为string且值类似于指定字符串的字段。该方法等同于SQL语句中的"LIKE"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [like](arkts-arkdata-relationalstore-rdbpredicates-c.md#like)

<!--Device-RdbPredicates-like(field: string, value: string): RdbPredicates--><!--Device-RdbPredicates-like(field: string, value: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | string | 是 | 指示要与谓词匹配的值，长度不超过1024字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了类似指定字符串条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.like("NAME", "%os%")
```

## limitAs

```TypeScript
limitAs(value: number): RdbPredicates
```

设置最大数据记录数的谓词。该方法等同于SQL语句中的"LIMIT"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [limitAs](arkts-arkdata-relationalstore-rdbpredicates-c.md#limitAs)

<!--Device-RdbPredicates-limitAs(value: number): RdbPredicates--><!--Device-RdbPredicates-limitAs(value: number): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 最大数据记录数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回可用于设置最大数据记录数的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").limitAs(3)
```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates
```

配置RdbPredicates以匹配数据字段为ValueType且value超出给定范围的指定字段。该方法等同于SQL语句中的"NOT BETWEEN"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [notBetween](arkts-arkdata-relationalstore-rdbpredicates-c.md#notBetween)

<!--Device-RdbPredicates-notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates--><!--Device-RdbPredicates-notBetween(field: string, low: ValueType, high: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| low | ValueType | 是 | 指示与谓词匹配的最小值。 |
| high | ValueType | 是 | 指示要与谓词匹配的最大值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了超出给定范围条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notBetween("AGE", 10, 50)
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): RdbPredicates
```

配置谓词以匹配数据字段为ValueType且值不等于指定值的字段。该方法等同于SQL语句中的"!="。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [notEqualTo](arkts-arkdata-relationalstore-rdbpredicates-c.md#notEqualTo)

<!--Device-RdbPredicates-notEqualTo(field: string, value: ValueType): RdbPredicates--><!--Device-RdbPredicates-notEqualTo(field: string, value: ValueType): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | ValueType | 是 | 指示要与谓词匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了不等于指定值条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notEqualTo("NAME", "lisi")
```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): RdbPredicates
```

将RdbPredicates配置为匹配数据字段为ValueType且值超出给定范围的指定字段。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [notIn](arkts-arkdata-relationalstore-rdbpredicates-c.md#notIn)

<!--Device-RdbPredicates-notIn(field: string, value: Array<ValueType>): RdbPredicates--><!--Device-RdbPredicates-notIn(field: string, value: Array<ValueType>): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |
| value | Array&lt;ValueType&gt; | 是 | 以ValueType数组形式指定的要匹配的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了值超出给定范围内条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.notIn("NAME", ["Lisa", "Rose"])
```

## offsetAs

```TypeScript
offsetAs(rowOffset: number): RdbPredicates
```

配置RdbPredicates以指定返回结果的起始位置。需要同步调用limitAs接口指定查询数量，否则将无查询结果。如需查询指定偏移位置后的所有行，limitAs接口调用需传参数-1。该方法等同于SQL语句中的"OFFSET "。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [offsetAs](arkts-arkdata-relationalstore-rdbpredicates-c.md#offsetAs)

<!--Device-RdbPredicates-offsetAs(rowOffset: number): RdbPredicates--><!--Device-RdbPredicates-offsetAs(rowOffset: number): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rowOffset | number | 是 | 返回结果的起始位置，取值为正整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回具有指定返回结果起始位置的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Rose").limitAs(-1).offsetAs(3)
```

## or

```TypeScript
or(): RdbPredicates
```

将或条件添加到谓词中。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [or](arkts-arkdata-relationalstore-rdbpredicates-c.md#or)

<!--Device-RdbPredicates-or(): RdbPredicates--><!--Device-RdbPredicates-or(): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回带有或条件的Rdb谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.equalTo("NAME", "Lisa")
    .or()
    .equalTo("NAME", "Rose")
```

## orderByAsc

```TypeScript
orderByAsc(field: string): RdbPredicates
```

配置谓词以匹配其值按升序排序的列。该方法等同于SQL语句中的"ORDER BY"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [orderByAsc](arkts-arkdata-relationalstore-rdbpredicates-c.md#orderByAsc)

<!--Device-RdbPredicates-orderByAsc(field: string): RdbPredicates--><!--Device-RdbPredicates-orderByAsc(field: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了按升序排序条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.orderByAsc("NAME")
```

## orderByDesc

```TypeScript
orderByDesc(field: string): RdbPredicates
```

配置谓词以匹配其值按降序排序的列。该方法等同于SQL语句中的"ORDER BY"。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [orderByDesc](arkts-arkdata-relationalstore-rdbpredicates-c.md#orderByDesc)

<!--Device-RdbPredicates-orderByDesc(field: string): RdbPredicates--><!--Device-RdbPredicates-orderByDesc(field: string): RdbPredicates-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| field | string | 是 | 数据库表中的列名，不能为空字符串。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RdbPredicates | 返回配置了按降序排序条件的谓词。 |

## 示例

```TypeScript
let predicates = new data_rdb.RdbPredicates("EMPLOYEE")
predicates.orderByDesc("AGE")
```

