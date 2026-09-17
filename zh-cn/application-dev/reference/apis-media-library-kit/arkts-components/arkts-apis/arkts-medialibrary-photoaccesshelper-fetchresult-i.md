# FetchResult

文件检索结果集。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## close

```TypeScript
close(): void
```

释放FetchResult实例并使其失效，释放后无法再调用其他方法。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## contains

```TypeScript
contains(object: T): Promise<boolean>
```

判断文件检索结果中是否包含指定的文件资产。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | T | 是 | 指定的文件资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示指定的文件资产在文件检索结果中；返回false表示指定的文件资产不在文件检索结果中。 |

## getAllObjects

```TypeScript
getAllObjects(callback: AsyncCallback<Array<T>>): void
```

获取文件检索结果中的所有文件资产。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;T&gt;&gt; | 是 | 回调函数。当获取结果集中的所有文件资产成功，err为undefined，data为具体检索结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getAllObjects

```TypeScript
getAllObjects(): Promise<Array<T>>
```

获取文件检索结果中的所有文件资产。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;T&gt;&gt; | Promise对象，返回所有文件资产的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getCount

```TypeScript
getCount(): number
```

获取文件检索结果中的文件总数。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 检索到的文件总数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getFirstObject

```TypeScript
getFirstObject(callback: AsyncCallback<T>): void
```

获取文件检索结果中的第一个文件资产。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | 是 | 回调函数。当获取结果集中的第一个文件资产成功，err为undefined，data为具体检索结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getFirstObject

```TypeScript
getFirstObject(): Promise<T>
```

获取文件检索结果中的第一个文件资产。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | Promise对象，返回结果集中第一个对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getIndex

```TypeScript
getIndex(object: T): Promise<number>
```

获取指定文件资产在文件检索结果中的索引。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| object | T | 是 | 指定的文件资产。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象，返回查询结果。如果对象在文件检索结果中则返回对应的索引，不存在则返回-1。 |

## getLastObject

```TypeScript
getLastObject(callback: AsyncCallback<T>): void
```

获取文件检索结果中的最后一个文件资产。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | 是 | 回调函数。当获取结果集中的最后一个文件资产成功，err为undefined，data为具体检索结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getLastObject

```TypeScript
getLastObject(): Promise<T>
```

获取文件检索结果中的最后一个文件资产。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | Promise对象，返回结果集中的最后一个对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getNextObject

```TypeScript
getNextObject(callback: AsyncCallback<T>): void
```

获取文件检索结果中的下一个文件资产。使用callback异步回调。

在调用此方法之前，必须使用[isAfterLast()](#isafterlast)来检查当前位置是否为最后一行。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | 是 | 回调函数。当获取结果集中的下一个文件资产成功，err为undefined，data为具体检索结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getNextObject

```TypeScript
getNextObject(): Promise<T>
```

获取文件检索结果中的下一个文件资产。使用Promise异步回调。

在调用此方法之前，必须使用[isAfterLast()](#isafterlast)来检查当前位置是否为最后一行。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | Promise对象，返回结果集中下一个对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getObjectByPosition

```TypeScript
getObjectByPosition(index: number, callback: AsyncCallback<T>): void
```

获取文件检索结果中具有指定索引的文件资产。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要获取的文件的索引，从0开始。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | 是 | 回调函数。当获取结果集中指定索引的文件资产成功，err为undefined，data为具体检索结果；否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getObjectByPosition

```TypeScript
getObjectByPosition(index: number): Promise<T>
```

获取文件检索结果中指定索引的文件资产。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 要获取的文件的索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | Promise对象，返回结果集中指定索引的一个对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |

## getObjectsByIndexSet

```TypeScript
getObjectsByIndexSet(indexSet: number[]): Promise<T[]>
```

获取文件检索结果中指定索引集合对应的文件资产数组。使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indexSet | number[] | 是 | 指定的索引集合。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T[]&gt; | Promise对象，返回指定索引集合所对应的文件资产数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails. Possible causes:<br>1.The indexSet is null, undefined or empty. <br>2.The indexSet length is bigger than 500. <br>3.The max value of indexSet is equal or bigger than the fetch result length. <br>4.The min value of indexSet is less than 0. |

## getRangeObjects

```TypeScript
getRangeObjects(index: number, offset: number): Promise<T[]>
```

在文件检索结果中，从指定索引（第一个参数）开始，获取指定长度（第二个参数）的文件资产数组。使用Promise异步回调。

**起始版本：** 23

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 开始获取的文件资产索引，大于等于0，小于文件检索结果中对象数量。 |
| offset | number | 是 | 要获取的文件资产数量，大于0。<br>index和offset之和需要小于检索结果中的对象数量，否则抛出23800151错误码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T[]&gt; | 返回Promise异步回调数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Called by non-system application<br>**适用版本：** 21 - 22 |
| [23800151](../errorcode-medialibrary.md#23800151-场景参数校验不通过) | The scenario parameter verification fails.<br>Possible causes: index or offset validity check failed. |
| [23800301](../errorcode-medialibrary.md#23800301-系统内部错误) | Internal system error. You are advised to retry and check the logs.<br>Possible causes: <br>1. The database is corrupted. <br>2. The file system is abnormal. |

## isAfterLast

```TypeScript
isAfterLast(): boolean
```

检查结果集是否指向最后一行。

**起始版本：** 10

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 当结果集指向最后一行时返回true，否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 14000011 | System inner fail |
