# ResultSet（系统接口）

提供通过查询数据库生成的数据库结果集的访问方法。下列API示例中，需先使用[query](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i-sys.md#query)方法获取ResultSet实例，再调用对应方法。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## close

```TypeScript
close(): void
```

关闭结果集，若不关闭可能会引起内存泄漏。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('close');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.close();
  } catch (err) {
    console.error(`close failed with error: ${err.code}, ${err.message}`);
  }
}
```

phAccessHelper的创建请参考[photoAccessHelper.getPhotoAccessHelper](arkts-apis-photoAccessHelper-f.md#photoaccesshelpergetphotoaccesshelper)的示例使用。

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';

async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('fetchResultCloseDemo');
  let predicates: dataSharePredicates.DataSharePredicates = new dataSharePredicates.DataSharePredicates();
  let fetchOption: photoAccessHelper.FetchOptions = {
    fetchColumns: [],
    predicates: predicates
  };
  try {
    let fetchResult: photoAccessHelper.FetchResult<photoAccessHelper.PhotoAsset> = await phAccessHelper.getAssets(fetchOption);
    fetchResult.close();
    console.info('close succeed.');
  } catch (err) {
    console.error(`close fail. error: ${err.code}, ${err.message}`);
  }
}
```

## getRow

```TypeScript
getRow(): ValuesBucket
```

获取指定行的所有列值。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValuesBucket | 返回指定行的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    const row = resultSet.getRow();
    resultSet.close();
  } catch (err) {
    console.error(`getRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## getValue

```TypeScript
getValue(columnIndex: number): ValueType
```

获取当前行中指定列的值。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。取值范围为0到结果集列数减1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 表示允许的数据字段类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: columnIndex invalid. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('getValue');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    const codes = resultSet.getValue(0);
    resultSet.close();
  } catch (err) {
    console.error(`getValue failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

转到结果集的第一行。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功转到结果集的第一行，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToFirstRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToFirstRow();
    resultSet.close();
  } catch (err) {
    console.error(`goToFirstRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

转到结果集的下一行。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功转到结果集的下一行，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToNextRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToNextRow();
    resultSet.close();
  } catch (err) {
    console.error(`goToNextRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## goToRow

```TypeScript
goToRow(position: number): boolean
```

转到结果集的指定行。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 指定行的索引，从0开始。取值范围为0到结果集行数减1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功转到结果集的指定行，则为true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | Scene parameters validate failed, possible causes: position invalid. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. It is recommended to retry and check the logs. Possible causes:  1. Database corrupted;  2. The file system is abnormal;  3. The IPC request timed out. |

**示例**

```TypeScript
async function example(phAccessHelper: photoAccessHelper.PhotoAccessHelper) {
  console.info('goToRow');
  try {
    let resultSet: photoAccessHelper.ResultSet = await phAccessHelper.query('SELECT * from Photos');
    resultSet.goToRow(0);
    resultSet.close();
  } catch (err) {
    console.error(`goToRow failed with error: ${err.code}, ${err.message}`);
  }
}
```

## columnCount

```TypeScript
columnCount: number
```

获取结果集的列数。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isAtLastRow

```TypeScript
isAtLastRow: boolean
```

检查游标是否位于最后一行。true表示位于最后一行，false表示不位于最后一行。

**类型：** boolean

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## rowCount

```TypeScript
rowCount: number
```

获取结果集的行数。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## rowIndex

```TypeScript
rowIndex: number
```

获取结果集的当前行索引。

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
