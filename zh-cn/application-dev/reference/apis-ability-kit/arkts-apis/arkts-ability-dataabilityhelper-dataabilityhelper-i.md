# DataAbilityHelper

可以通过[acquireDataAbilityHelper](arkts-ability-featureability-acquiredataabilityhelper-f.md#acquiredataabilityhelper-1)接口获取DataAbilityHelper对象。

**起始版本：** 7

<!--Device-unnamed-export interface DataAbilityHelper--><!--Device-unnamed-export interface DataAbilityHelper-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

<a id="batchinsert"></a>
## batchInsert

```TypeScript
batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>, callback: AsyncCallback<number>): void
```

将多个数据记录插入数据库。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要插入数据的uri。 |
| valuesBuckets | Array&lt;rdb.ValuesBucket&gt; | 是 | 表示要插入的数据记录数组。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回插入的数据记录数。 |

<a id="batchinsert-1"></a>
## batchInsert

```TypeScript
batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>): Promise<number>
```

将多个数据记录插入数据库。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>): Promise<number>--><!--Device-DataAbilityHelper-batchInsert(uri: string, valuesBuckets: Array<rdb.ValuesBucket>): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要插入数据的uri。 |
| valuesBuckets | Array&lt;rdb.ValuesBucket&gt; | 是 | 表示要插入的数据记录数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回插入的数据记录数。 |

<a id="call"></a>
## call

```TypeScript
call(uri: string, method: string, arg: string, extras: PacMap, callback: AsyncCallback<PacMap>): void
```

调用DataAbility的扩展接口。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-call(uri: string, method: string, arg: string, extras: PacMap, callback: AsyncCallback<PacMap>): void--><!--Device-DataAbilityHelper-call(uri: string, method: string, arg: string, extras: PacMap, callback: AsyncCallback<PacMap>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。 |
| method | string | 是 | 表示被调用的方法名。 |
| arg | string | 是 | 表示需传入的参数。 |
| extras | [PacMap](arkts-ability-dataabilityhelper-pacmap-i.md) | 是 | 表示扩展的键值对参数。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;PacMap&gt; | 是 | 回调函数，返回扩展的键值对参数。 |

<a id="call-1"></a>
## call

```TypeScript
call(uri: string, method: string, arg: string, extras: PacMap): Promise<PacMap>
```

调用DataAbility的扩展接口。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-call(uri: string, method: string, arg: string, extras: PacMap): Promise<PacMap>--><!--Device-DataAbilityHelper-call(uri: string, method: string, arg: string, extras: PacMap): Promise<PacMap>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。 |
| method | string | 是 | 表示被调用的方法名。 |
| arg | string | 是 | 表示需传入的参数。 |
| extras | [PacMap](arkts-ability-dataabilityhelper-pacmap-i.md) | 是 | 表示扩展的键值对参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;PacMap&gt; | Promise对象，返回扩展的键值对参数。 |

<a id="delete"></a>
## delete

```TypeScript
delete(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<number>): void
```

从数据库中删除一个或多个数据记录。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-delete(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-delete(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要删除数据的uri。 |
| predicates | dataAbility.DataAbilityPredicates | 是 | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回已删除的数据记录数。 |

<a id="delete-1"></a>
## delete

```TypeScript
delete(uri: string, predicates?: dataAbility.DataAbilityPredicates): Promise<number>
```

从数据库中删除一个或多个数据记录。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-delete(uri: string, predicates?: dataAbility.DataAbilityPredicates): Promise<number>--><!--Device-DataAbilityHelper-delete(uri: string, predicates?: dataAbility.DataAbilityPredicates): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要删除数据的uri。 |
| predicates | dataAbility.DataAbilityPredicates | 否 | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Returns the number of data records deleted. |

<a id="delete-2"></a>
## delete

```TypeScript
delete(uri: string, callback: AsyncCallback<number>): void
```

predicates筛选条件为空，自定义数据库删除数据记录的处理逻辑。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-delete(uri: string, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-delete(uri: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要删除数据的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回已删除的数据记录数。 |

<a id="denormalizeuri"></a>
## denormalizeUri

```TypeScript
denormalizeUri(uri: string, callback: AsyncCallback<string>): void
```

将由normalizeUri（uri）生成的给定规范化uri转换为非规范化uri。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-denormalizeUri(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataAbilityHelper-denormalizeUri(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要反规范化的uri对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回反规范化uri对象。 |

<a id="denormalizeuri-1"></a>
## denormalizeUri

```TypeScript
denormalizeUri(uri: string): Promise<string>
```

将由normalizeUri（uri）生成的给定规范化uri转换为非规范化uri。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-denormalizeUri(uri: string): Promise<string>--><!--Device-DataAbilityHelper-denormalizeUri(uri: string): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要规范化的uri对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回反规范化uri对象。 |

<a id="executebatch"></a>
## executeBatch

```TypeScript
executeBatch(
    uri: string,
    operations: Array<DataAbilityOperation>,
    callback: AsyncCallback<Array<DataAbilityResult>>
  ): void
```

批量操作数据库中的数据。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-executeBatch(
    uri: string,
    operations: Array<DataAbilityOperation>,
    callback: AsyncCallback<Array<DataAbilityResult>>
  ): void--><!--Device-DataAbilityHelper-executeBatch(
    uri: string,
    operations: Array<DataAbilityOperation>,
    callback: AsyncCallback<Array<DataAbilityResult>>
  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。 |
| operations | Array&lt;DataAbilityOperation&gt; | 是 | 表示数据操作数组，其中可以包含对数据库的多个不同操作。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;DataAbilityResult&gt;&gt; | 是 | 回调函数，在DataAbilityResult数组中返回每个操作的结果。 |

<a id="executebatch-1"></a>
## executeBatch

```TypeScript
executeBatch(uri: string, operations: Array<DataAbilityOperation>): Promise<Array<DataAbilityResult>>
```

批量操作数据库中的数据。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-executeBatch(uri: string, operations: Array<DataAbilityOperation>): Promise<Array<DataAbilityResult>>--><!--Device-DataAbilityHelper-executeBatch(uri: string, operations: Array<DataAbilityOperation>): Promise<Array<DataAbilityResult>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待处理的DataAbility。例：'dataability:///com.example.xxx.xxxx'。 |
| operations | Array&lt;DataAbilityOperation&gt; | 是 | 表示数据操作数组，其中可以包含对数据库的多个不同操作。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;DataAbilityResult&gt;&gt; | Promise对象，在DataAbilityResult数组中返回每个操作的结果。 |

<a id="getfiletypes"></a>
## getFileTypes

```TypeScript
getFileTypes(uri: string, mimeTypeFilter: string, callback: AsyncCallback<Array<string>>): void
```

获取支持的文件媒体资源类型。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-getFileTypes(uri: string, mimeTypeFilter: string, callback: AsyncCallback<Array<string>>): void--><!--Device-DataAbilityHelper-getFileTypes(uri: string, mimeTypeFilter: string, callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待获取文件的uri。 |
| mimeTypeFilter | string | 是 | 表示待获取文件的媒体资源类型。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数，返回匹配的媒体资源类型数组。 |

<a id="getfiletypes-1"></a>
## getFileTypes

```TypeScript
getFileTypes(uri: string, mimeTypeFilter: string): Promise<Array<string>>
```

获取支持的文件媒体资源类型。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-getFileTypes(uri: string, mimeTypeFilter: string): Promise<Array<string>>--><!--Device-DataAbilityHelper-getFileTypes(uri: string, mimeTypeFilter: string): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待获取文件的uri。 |
| mimeTypeFilter | string | 是 | 表示待获取文件的媒体资源类型。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回匹配的媒体资源类型数组。 |

<a id="gettype"></a>
## getType

```TypeScript
getType(uri: string, callback: AsyncCallback<string>): void
```

获取给定uri指向数据的媒体资源类型。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-getType(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataAbilityHelper-getType(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待获取数据的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，返回与uri指向数据匹配的媒体资源类型。 |

<a id="gettype-1"></a>
## getType

```TypeScript
getType(uri: string): Promise<string>
```

获取给定uri指向数据的媒体资源类型。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-getType(uri: string): Promise<string>--><!--Device-DataAbilityHelper-getType(uri: string): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待获取数据的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，返回与uri指向数据匹配的媒体资源类型。 |

<a id="insert"></a>
## insert

```TypeScript
insert(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void
```

将单个数据记录插入数据库。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-insert(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-insert(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要插入数据的uri。 |
| valuesBucket | rdb.ValuesBucket | 是 | 表示要插入的数据记录。如果此参数为空，将插入一个空行。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回插入数据记录的索引。 |

<a id="insert-1"></a>
## insert

```TypeScript
insert(uri: string, valuesBucket: rdb.ValuesBucket): Promise<number>
```

将单个数据记录插入数据库。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-insert(uri: string, valuesBucket: rdb.ValuesBucket): Promise<number>--><!--Device-DataAbilityHelper-insert(uri: string, valuesBucket: rdb.ValuesBucket): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要插入数据的uri。 |
| valuesBucket | rdb.ValuesBucket | 是 | 表示要插入的数据记录。如果此参数为空，将插入一个空行。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回插入数据记录的索引。 |

<a id="normalizeuri"></a>
## normalizeUri

```TypeScript
normalizeUri(uri: string, callback: AsyncCallback<string>): void
```

将引用数据功能的给定uri转换为规范化uri。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-normalizeUri(uri: string, callback: AsyncCallback<string>): void--><!--Device-DataAbilityHelper-normalizeUri(uri: string, callback: AsyncCallback<string>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要规范化的uri对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | 是 | 回调函数，如果数据功能支持uri规范化，则返回规范化uri对象；否则返回null。 |

<a id="normalizeuri-1"></a>
## normalizeUri

```TypeScript
normalizeUri(uri: string): Promise<string>
```

将引用数据功能的给定uri转换为规范化uri。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-normalizeUri(uri: string): Promise<string>--><!--Device-DataAbilityHelper-normalizeUri(uri: string): Promise<string>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要规范化的uri对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象，如果数据功能支持uri规范化，则返回规范化uri对象；否则返回null。 |

<a id="notifychange"></a>
## notifyChange

```TypeScript
notifyChange(uri: string, callback: AsyncCallback<void>): void
```

通知注册的观察者，uri指定数据的数据变化。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-notifyChange(uri: string, callback: AsyncCallback<void>): void--><!--Device-DataAbilityHelper-notifyChange(uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示数据变化的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当通知注册的观察者成功，err为undefined，否则为错误对象。 |

<a id="notifychange-1"></a>
## notifyChange

```TypeScript
notifyChange(uri: string): Promise<void>
```

通知注册的观察者，uri指定数据的数据变化。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-notifyChange(uri: string): Promise<void>--><!--Device-DataAbilityHelper-notifyChange(uri: string): Promise<void>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示数据变化的uri。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

<a id="off"></a>
## off('dataChange')

```TypeScript
off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void
```

注销观察者以停止监听uri指定数据的数据变化通知。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void--><!--Device-DataAbilityHelper-off(type: 'dataChange', uri: string, callback?: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 表示监听操作类型，'dataChange'表示数据变化操作。 |
| uri | string | 是 | 表示待取消监听数据变化的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 否 | 回调函数。当注销观察者以停止监听uri指定数据的数据变化通知成功，err为undefined，否则为错误对象。 |

<a id="on"></a>
## on('dataChange')

```TypeScript
on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void
```

注册观察者以监听uri指定数据的数据变化通知。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void--><!--Device-DataAbilityHelper-on(type: 'dataChange', uri: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'dataChange' | 是 | 表示监听操作类型，'dataChange'表示数据变化操作。 |
| uri | string | 是 | 表示待监听数据变化的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。当注册观察者以监听uri指定数据的数据变化通知成功，err为undefined，否则为错误对象。 |

<a id="openfile"></a>
## openFile

```TypeScript
openFile(uri: string, mode: string, callback: AsyncCallback<number>): void
```

打开指定uri对应的文件，返回文件描述符。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-openFile(uri: string, mode: string, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-openFile(uri: string, mode: string, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待打开文件的uri。 |
| mode | string | 是 | 表示文件打开模式，可以设置为‘r’表示只读访问，‘w’表示只写访问，‘rw’表示读写访问等。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回文件描述符。 |

<a id="openfile-1"></a>
## openFile

```TypeScript
openFile(uri: string, mode: string): Promise<number>
```

打开指定uri对应的文件，返回文件描述符。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-openFile(uri: string, mode: string): Promise<number>--><!--Device-DataAbilityHelper-openFile(uri: string, mode: string): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示待打开文件的uri |
| mode | string | 是 | 表示文件打开模式，可以设置为‘r’表示只读访问，‘w’表示只写访问，‘rw’表示读写访问等。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回文件说明符。 |

<a id="query"></a>
## query

```TypeScript
query(
    uri: string,
    columns: Array<string>,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<ResultSet>
  ): void
```

查询数据库中的数据。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-query(
    uri: string,
    columns: Array<string>,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<ResultSet>
  ): void--><!--Device-DataAbilityHelper-query(
    uri: string,
    columns: Array<string>,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<ResultSet>
  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要查询数据的uri。 |
| columns | Array&lt;string&gt; | 是 | 表示要查询的列。如果此参数为空，则查询所有列。 |
| predicates | dataAbility.DataAbilityPredicates | 是 | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数，返回查询结果。 |

<a id="query-1"></a>
## query

```TypeScript
query(uri: string, callback: AsyncCallback<ResultSet>): void
```

查询数据库中的数据。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-query(uri: string, callback: AsyncCallback<ResultSet>): void--><!--Device-DataAbilityHelper-query(uri: string, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要查询数据的uri。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数，返回查询结果。 |

<a id="query-2"></a>
## query

```TypeScript
query(uri: string, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

查询数据库中的数据。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-query(uri: string, columns: Array<string>, callback: AsyncCallback<ResultSet>): void--><!--Device-DataAbilityHelper-query(uri: string, columns: Array<string>, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要查询数据的uri。 |
| columns | Array&lt;string&gt; | 是 | 表示要查询的列。如果此参数为空，则查询所有列。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数，返回查询结果。 |

<a id="query-3"></a>
## query

```TypeScript
query(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<ResultSet>): void
```

查询数据库中的数据。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-query(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<ResultSet>): void--><!--Device-DataAbilityHelper-query(uri: string, predicates: dataAbility.DataAbilityPredicates, callback: AsyncCallback<ResultSet>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要查询数据的uri。 |
| predicates | dataAbility.DataAbilityPredicates | 是 | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ResultSet&gt; | 是 | 回调函数，返回查询结果。 |

<a id="query-4"></a>
## query

```TypeScript
query(uri: string, columns?: Array<string>, predicates?: dataAbility.DataAbilityPredicates): Promise<ResultSet>
```

查询数据库中的数据。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-query(uri: string, columns?: Array<string>, predicates?: dataAbility.DataAbilityPredicates): Promise<ResultSet>--><!--Device-DataAbilityHelper-query(uri: string, columns?: Array<string>, predicates?: dataAbility.DataAbilityPredicates): Promise<ResultSet>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要查询数据的uri。 |
| columns | Array&lt;string&gt; | 否 | 表示要查询的列。如果此参数为空，则查询所有列。 |
| predicates | dataAbility.DataAbilityPredicates | 否 | 表示筛选条件。当此参数为null时，自定义查询数据库中数据的处理逻辑。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ResultSet&gt; | Promise对象，返回查询结果。 |

<a id="update"></a>
## update

```TypeScript
update(
    uri: string,
    valuesBucket: rdb.ValuesBucket,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<number>
  ): void
```

更新数据库中的数据记录。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-update(
    uri: string,
    valuesBucket: rdb.ValuesBucket,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<number>
  ): void--><!--Device-DataAbilityHelper-update(
    uri: string,
    valuesBucket: rdb.ValuesBucket,
    predicates: dataAbility.DataAbilityPredicates,
    callback: AsyncCallback<number>
  ): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要更新数据的uri。 |
| valuesBucket | rdb.ValuesBucket | 是 | 表示要更新的数据。 |
| predicates | dataAbility.DataAbilityPredicates | 是 | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回更新的数据记录数。 |

<a id="update-1"></a>
## update

```TypeScript
update(uri: string, valuesBucket: rdb.ValuesBucket, predicates?: dataAbility.DataAbilityPredicates): Promise<number>
```

更新数据库中的数据记录。使用Promise异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-update(uri: string, valuesBucket: rdb.ValuesBucket, predicates?: dataAbility.DataAbilityPredicates): Promise<number>--><!--Device-DataAbilityHelper-update(uri: string, valuesBucket: rdb.ValuesBucket, predicates?: dataAbility.DataAbilityPredicates): Promise<number>-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要更新数据的uri。 |
| valuesBucket | rdb.ValuesBucket | 是 | 表示要更新的数据。 |
| predicates | dataAbility.DataAbilityPredicates | 否 | 表示筛选条件。当此参数为null时，应定义处理逻辑。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Returns the number of data records updated. |

<a id="update-2"></a>
## update

```TypeScript
update(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void
```

predicates筛选条件为空，自定义更新数据库的处理逻辑。使用callback异步回调。

**起始版本：** 7

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-DataAbilityHelper-update(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void--><!--Device-DataAbilityHelper-update(uri: string, valuesBucket: rdb.ValuesBucket, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.FAModel

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 表示要更新数据的uri。 |
| valuesBucket | rdb.ValuesBucket | 是 | 表示要更新的数据。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回更新的数据记录数。 |

