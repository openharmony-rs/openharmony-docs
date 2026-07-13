# CloudDB（系统接口）

提供云数据库操作接口的类。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

## delete

```TypeScript
delete(
      table: string,
      extensions: Array<Record<string, CloudType>>
    ): Promise<Array<Result<Record<string, CloudType>>>>
```

删除云数据库表中的指定数据。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| extensions | Array&lt;Record&lt;string, CloudType&gt;&gt; | 是 | 表示当前数据的扩展信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Result&lt;Record&lt;string, CloudType&gt;&gt;&gt;&gt; | Promise对象，返回被删除的数据和删除结果。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async delete(table: string, extensions: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    console.info(`delete, table: ${table}`);
    let deleteRes: Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>> = [];
    // ...
    // 返回删除数据的结果
    return deleteRes;
  }
  // ...
}

```

## generateId

```TypeScript
generateId(count: number): Promise<Result<Array<string>>>
```

为插入的云数据生成具有唯一性的ID。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | number | 是 | 表示要生成ID的数量。取值范围大于等于1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;Array&lt;string&gt;&gt;&gt; | Promise对象，以Result结构将生成的ID以数组形式返回。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
  async generateId(count: number): Promise<cloudExtension.Result<Array<string>>> {
    console.info(`generate id, count: ${count}`);
    let result = new Array<string>();
    // ...
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: 'generateId succeeded',
      value: result
    };
  }
  // ...
}

```

## heartbeat

```TypeScript
heartbeat(lockId: number): Promise<Result<LockInfo>>
```

延长数据库的加锁时效。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lockId | number | 是 | 表示需要延时的锁ID，取值为lock方法返回的LockInfo中的lockId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;LockInfo&gt;&gt; | Promise对象，返回锁的信息，包含加锁时长和锁的ID。 |

**示例：**

```TypeScript
let testLockId: number = 1;
let testTime: number = 10;
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async heartbeat(lockId: number): Promise<cloudExtension.Result<cloudExtension.LockInfo>> {
    console.info(`heartbeat lock`);
    // ...
    // 返回心跳检查的结果
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: 'heartbeat succeeded',
      value: {
        interval: testTime,
        lockId: testLockId
      }
    };
  }
  // ...
}

```

## insert

```TypeScript
insert(
      table: string,
      values: Array<Record<string, CloudType>>,
      extensions: Array<Record<string, CloudType>>
    ): Promise<Array<Result<Record<string, CloudType>>>>
```

将数据插入云数据库表中。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| values | Array&lt;Record&lt;string, CloudType&gt;&gt; | 是 | 表示要插入的数据。 |
| extensions | Array&lt;Record&lt;string, CloudType&gt;&gt; | 是 | 表示当前数据的扩展信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Result&lt;Record&lt;string, CloudType&gt;&gt;&gt;&gt; | Promise对象，返回插入的数据和插入结果。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async insert(table: string, values: Array<Record<string, cloudExtension.CloudType>>, extensions: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    console.info(`insert, table: ${table}`);
    let insertRes: Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>> = [];
    // ...
    // 返回插入数据的结果
    return insertRes;
  }
  // ...
}

```

## lock

```TypeScript
lock(): Promise<Result<LockInfo>>
```

为云数据库加锁。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;LockInfo&gt;&gt; | Promise对象，返回加锁的信息，包含加锁时长和锁的ID。 |

**示例：**

```TypeScript
let testTime: number = 10;
let testLockId: number = 1;
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async lock(): Promise<cloudExtension.Result<cloudExtension.LockInfo>> {
    console.info(`DB lock`);
    // ...
    // 返回锁定数据的结果
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: 'lock succeeded',
      value: {
        interval: testTime,
        lockId: testLockId
      }
    };
  }
  // ...
}

```

## query

```TypeScript
query(table: string, fields: Array<string>, queryCount: number, queryCursor: string): Promise<Result<CloudData>>
```

在云数据库表中查询数据。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| fields | Array&lt;string&gt; | 是 | 表示要查询的字段名数组。 |
| queryCount | number | 是 | 表示要查询的数据记录条数。取值范围大于等于1。 |
| queryCursor | string | 是 | 表示要查询的游标。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;CloudData&gt;&gt; | Promise对象，返回被查询的数据和查询结果。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async query(table: string, fields: Array<string>, queryCount: number, queryCursor: string): Promise<cloudExtension.Result<cloudExtension.CloudData>> {
    console.info(`query, table: ${table}`);
    // ...
    // 返回查询数据的结果
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: 'query succeeded',
      value: {
        nextCursor: "test_nextCursor",
        hasMore: true,
        values: []
      }
    };
  }
  // ...
}

```

## unlock

```TypeScript
unlock(lockId: number): Promise<Result<boolean>>
```

为云数据库解锁。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| lockId | number | 是 | 表示锁的ID，取值为lock方法返回的LockInfo中的lockId。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Result&lt;boolean&gt;&gt; | Promise对象，返回解锁结果，true表示解锁成功，false表示解锁失败。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
    // ...
  async unlock(lockId: number): Promise<cloudExtension.Result<boolean>> {
    console.info(`unlock`);
    // ...
    // 返回解锁数据的结果
    return {
      code: cloudExtension.ErrorCode.SUCCESS,
      description: 'unlock succeeded',
      value: false
    };
  }
  // ...
}

```

## update

```TypeScript
update(
      table: string,
      values: Array<Record<string, CloudType>>,
      extensions: Array<Record<string, CloudType>>
    ): Promise<Array<Result<Record<string, CloudType>>>>
```

通过该接口更新云上的数据。使用Promise异步回调。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| table | string | 是 | 表名。 |
| values | Array&lt;Record&lt;string, CloudType&gt;&gt; | 是 | 表示要更新的数据。 |
| extensions | Array&lt;Record&lt;string, CloudType&gt;&gt; | 是 | 表示当前数据的扩展信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Result&lt;Record&lt;string, CloudType&gt;&gt;&gt;&gt; | Promise对象，返回更新的数据和更新结果。 |

**示例：**

```TypeScript
class MyCloudDB implements cloudExtension.CloudDB {
  // ...
  async update(table: string, values: Array<Record<string, cloudExtension.CloudType>>, extensions: Array<Record<string, cloudExtension.CloudType>>): Promise<Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>>> {
    console.info(`update, table: ${table}`);
    let updateRes: Array<cloudExtension.Result<Record<string, cloudExtension.CloudType>>> = [];
    // ...
    // 返回更新数据的结果
    return updateRes;
  }
  // ...
}

```

