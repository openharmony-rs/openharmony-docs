# URLParams

URLParams是一个用于解析、构造和操作URL参数的实用类。该类提供了统一的接口来处理参数维度（如查询参数、路径参数等）。

**起始版本：** 9

<!--Device-url-class URLParams--><!--Device-url-class URLParams-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[string, string]>
```

获取一个ES6迭代器。迭代器的每一项都是一个JavaScript数组，数组的第一项和第二项分别是键和值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-[Symbol.iterator](): IterableIterator<[string, string]>--><!--Device-URLParams-[Symbol.iterator](): IterableIterator<[string, string]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[string, string]&gt; | 返回一个ES6迭代器。迭代器的每一项都是一个JavaScript Array。Array的第一项是name，第二项是value。 |

**示例：**

```TypeScript
// 构造URLParams对象
const paramsObject = new url.URLParams('fod=bay&edg=bap');
// 获取Symbol.iterator迭代器
let iter = paramsObject[Symbol.iterator]();
// 遍历键值对
for (let pair of iter) {
  console.info(pair[0] + ', ' + pair[1]);
}
// fod, bay
// edg, bap

```

## append

```TypeScript
append(name: string, value: string): void
```

将新的键值对插入到查询字符串。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-append(name: string, value: string): void--><!--Device-URLParams-append(name: string, value: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要插入搜索参数的键名。 |
| value | string | 是 | 需要插入搜索参数的值。 |

**示例：**

```TypeScript
// 解析URL字符串
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// 构造URLParams对象
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// 追加键值对
paramsObject.append('fod', '3');

```

## constructor

```TypeScript
constructor(init?: string[][] | Record<string, string> | string | URLParams)
```

ArkTS-Sta: constructor(init?: [string, string][] | Record&lt;string, string&gt; | string | URLParams)

URLParams的构造函数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-constructor(init?: string[][] | Record<string, string> | string | URLParams)--><!--Device-URLParams-constructor(init?: string[][] | Record<string, string> | string | URLParams)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| init | string[][] \| Record&lt;string, string&gt; \| string \| URLParams | 否 | 入参对象。<br/>- string[][]：字符串二维数组。<br/>- Record&lt;string, string&gt;：对象列表。<br/>- string：字符串。<br/>- URLParams：对象。<br/>- 默认值：null。 |

**示例：**

```TypeScript
// 通过string[][]方式构造URLParams对象：
let objectParams = new url.URLParams([ ['user1', 'abc1'], ['query2', 'first2'], ['query3', 'second3'] ]);
// 通过Record<string, string>方式构造URLParams对象：
let objectParams1 = new url.URLParams({'fod' : '1' , 'bard' : '2'});
// 通过string方式构造URLParams对象：
let objectParams2 = new url.URLParams('?fod=1&bard=2');
// 通过url对象的search属性构造URLParams对象：
let urlObject = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams3 = new url.URLParams(urlObject.search);
// 通过url对象的params属性获取URLParams对象：
let secondUrlObj = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams4 = secondUrlObj.params;

```

## delete

```TypeScript
delete(name: string): void
```

删除指定名称的键值对。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-delete(name: string): void--><!--Device-URLParams-delete(name: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要删除的键值名称。 |

**示例：**

```TypeScript
// 解析URL字符串
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// 构造URLParams对象
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// 删除指定名称的键值对
paramsObject.delete('fod');

```

## entries

```TypeScript
entries(): IterableIterator<[string, string]>
```

返回一个ES6的迭代器，迭代器的每一项都是一个Array。Array的第一项是name，Array的第二项是value。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-entries(): IterableIterator<[string, string]>--><!--Device-URLParams-entries(): IterableIterator<[string, string]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[string, string]&gt; | 返回一个ES6的迭代器。 |

**示例：**

```TypeScript
// 构造URLParams对象
let paramsObject = new url.URLParams('keyName1=valueName1&keyName2=valueName2');
// 获取entries迭代器
let pair = paramsObject.entries();
// 遍历键值对
for (let item of pair) {
  console.info(item[0] + '=' + item[1]);
}
// keyName1=valueName1
// keyName2=valueName2

```

## forEach

```TypeScript
forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void
```

通过回调函数来遍历URLParams实例对象上的键值对。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void--><!--Device-URLParams-forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: string, key: string, searchParams: URLParams) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值是本对象。 |

**示例：**

```TypeScript
// 解析URL
const myURLObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// 通过回调函数遍历URLParams键值对
myURLObject.params.forEach((value, name, searchParams) => {
    console.info(name, value, myURLObject.params === searchParams);
});

```

## get

```TypeScript
get(name: string): string | null
```

获取指定名称对应的第一个值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-get(name: string): string | null--><!--Device-URLParams-get(name: string): string | null-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 指定键值对的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回第一个值，如果没找到，返回 null。 |

**示例：**

```TypeScript
let paramsObject = new url.URLParams('name=Jonathan&age=18');
let name = paramsObject.get('name'); // is the string "Jonathan"
let age = paramsObject.get('age'); // is the string "18"
let absentValue = paramsObject.get('abc'); // undefined

```

## getAll

```TypeScript
getAll(name: string): string[]
```

获取指定名称的所有键对应值的集合。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-getAll(name: string): string[]--><!--Device-URLParams-getAll(name: string): string[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 指定的键值名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回指定名称的所有键对应值的集合。 |

**示例：**

```TypeScript
// 解析URL并构造URLParams对象
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLParams(urlObject.search.slice(1));
params.append('fod', '3'); // 追加第二个fod参数值
// 获取指定名称fod的所有值
console.info(params.getAll('fod').toString()); // Output ["1","3"]

```

## has

```TypeScript
has(name: string): boolean
```

判断一个指定的键名对应的值是否存在。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-has(name: string): boolean--><!--Device-URLParams-has(name: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要查找的参数的键名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否存在相对应的key值，存在返回true，否则返回false。 |

**示例：**

```TypeScript
// 解析URL字符串
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// 构造URLParams对象
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// 判断键名bard是否存在
let result = paramsObject.has('bard');

```

## keys

```TypeScript
keys(): IterableIterator<string>
```

返回一个包含所有键值对的name的ES6迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-keys(): IterableIterator<string>--><!--Device-URLParams-keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | 返回一个包含所有键值对的name的ES6迭代器。 |

**示例：**

```TypeScript
// 构造URLParams对象
let paramsObject = new url.URLParams("key1=value1&key2=value2");
// 获取所有键名的迭代器
let keys = paramsObject.keys();
// 遍历输出键名
for (let key of keys) {
  console.info(key);
}
// key1
// key2

```

## set

```TypeScript
set(name: string, value: string): void
```

将与name关联的URLSearchParams对象中的值设置为value。

如果存在名称为name的键值对，请将第一个键值对的值设置为value并删除所有其他值。如果不是，则将键值对附加到查询字符串。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-set(name: string, value: string): void--><!--Device-URLParams-set(name: string, value: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 将要设置的参数的键值名。 |
| value | string | 是 | 所要设置的参数值。 |

**示例：**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.

```

## sort

```TypeScript
sort(): void
```

对包含在此对象中的所有键值对进行排序。排序顺序是根据键的Unicode代码点。该方法使用稳定的排序算法（保留具有相等键的键值对之间的相对顺序）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-sort(): void--><!--Device-URLParams-sort(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let paramsObject = new url.URLParams("c=3&a=9&b=4&d=2"); // Create a test URLParams object
paramsObject.sort(); // Sort the key/value pairs
console.info(paramsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2

```

## toString

```TypeScript
toString(): string
```

返回序列化为字符串的搜索参数，必要时对字符进行百分比编码。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-toString(): string--><!--Device-URLParams-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回序列化为字符串的搜索参数，必要时对字符进行百分比编码。 |

**示例：**

```TypeScript
// 解析URL字符串
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// 构造URLParams对象
let params = new url.URLParams(urlObject.search.slice(1));
// 追加参数
params.append('fod', '3');
// 将参数序列化为字符串
console.info(params.toString()); // Output 'fod=1&bard=2&fod=3'

```

## values

```TypeScript
values(): IterableIterator<string>
```

返回一个包含所有键值对的value的ES6迭代器。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URLParams-values(): IterableIterator<string>--><!--Device-URLParams-values(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | 返回一个包含所有键值对的value的ES6迭代器。 |

**示例：**

```TypeScript
// 构造URLParams对象
let paramsObject = new url.URLParams("key1=value1&key2=value2");
// 获取所有值的迭代器
let values = paramsObject.values();
// 遍历输出值
for (let value of values) {
  console.info(value);
}
// value1
// value2

```

