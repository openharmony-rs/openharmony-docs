# URLSearchParams

URLSearchParams接口定义了一些处理URL查询字符串的实用方法，从API version 9开始废弃，建议使用[URLParams](arkts-arkts-url-urlparams-c.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** URLParams

<!--Device-url-class URLSearchParams--><!--Device-url-class URLSearchParams-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[string, string]>
```

返回一个迭代器，允许遍历此对象中包含的所有键值对。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** iterator]

<!--Device-URLSearchParams-[Symbol.iterator](): IterableIterator<[string, string]>--><!--Device-URLSearchParams-[Symbol.iterator](): IterableIterator<[string, string]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[string, string]&gt; | 返回一个ES6迭代器。迭代器的每一项都是一个JavaScript Array。Array的第一项是name，第二项是value。 |

**示例：**

```TypeScript
const paramsObject = new url.URLSearchParams('fod=bay&edg=bap');
let pairs = paramsObject[Symbol.iterator]();
for (let pair of pairs) {
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

**起始版本：** 7

**废弃版本：** 9

**替代接口：** append

<!--Device-URLSearchParams-append(name: string, value: string): void--><!--Device-URLSearchParams-append(name: string, value: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要插入搜索参数的键名。 |
| value | string | 是 | 需要插入搜索参数的值。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.append('fod', '3');

```

## constructor

```TypeScript
constructor(init?: string[][] | Record<string, string> | string | URLSearchParams)
```

URLSearchParams的构造函数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** constructor

<!--Device-URLSearchParams-constructor(init?: string[][] | Record<string, string> | string | URLSearchParams)--><!--Device-URLSearchParams-constructor(init?: string[][] | Record<string, string> | string | URLSearchParams)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| init | string[][] \| Record&lt;string, string&gt; \| string \| URLSearchParams | 否 | 入参对象。<br/>- string[][]：字符串二维数组。<br/>- Record&lt;string, string&gt;：对象列表。<br/>- string：字符串。<br/>- URLSearchParams：对象。<br/>- 默认值：undefined。 |

**示例：**

```TypeScript
let objectParams = new url.URLSearchParams([ ['user1', 'abc1'], ['query2', 'first2'], ['query3', 'second3'] ]);
let objectParams1 = new url.URLSearchParams({"fod" : '1' , "bard" : '2'});
let objectParams2 = new url.URLSearchParams('?fod=1&bard=2');
let urlObject = new url.URL('https://developer.mozilla.org/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search);

```

## delete

```TypeScript
delete(name: string): void
```

删除指定名称的键值对。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** delete

<!--Device-URLSearchParams-delete(name: string): void--><!--Device-URLSearchParams-delete(name: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 需要删除的键值名称。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.delete('fod');

```

## entries

```TypeScript
entries(): IterableIterator<[string, string]>
```

返回一个ES6的迭代器，迭代器的每一项都是一个Array。Array的第一项是name，Array的第二项是value。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** entries

<!--Device-URLSearchParams-entries(): IterableIterator<[string, string]>--><!--Device-URLSearchParams-entries(): IterableIterator<[string, string]>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;[string, string]&gt; | 返回一个ES6的迭代器。 |

**示例：**

```TypeScript
let searchParamsObject = new url.URLSearchParams("keyName1=valueName1&keyName2=valueName2");
let iter = searchParamsObject.entries();
for (let pair of iter) {
  console.info(pair[0]+ ', '+ pair[1]);
}
// keyName1, valueName1
// keyName2, valueName2

```

## forEach

```TypeScript
forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void
```

通过回调函数来遍历URLSearchParams实例对象上的键值对。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** forEach

<!--Device-URLSearchParams-forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void--><!--Device-URLSearchParams-forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callbackFn | (value: string, key: string, searchParams: URLSearchParams) =&gt; void | 是 | 回调函数。 |
| thisArg | Object | 否 | callbackFn被调用时用作this值，默认值是本对象。 |

**示例：**

```TypeScript
const myURLObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
myURLObject.searchParams.forEach((value, name, searchParams) => {
    console.info(name, value, myURLObject.searchParams === searchParams);
});

```

## get

```TypeScript
get(name: string): string | null
```

获取指定名称对应的第一个值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** get

<!--Device-URLSearchParams-get(name: string): string | null--><!--Device-URLSearchParams-get(name: string): string | null-End-->

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
let paramsObject = new url.URLSearchParams('name=Jonathan&age=18');
let name = paramsObject.get("name"); // is the string "Jonathan"
let age = paramsObject.get("age"); // is the string '18'
let getObj = paramsObject.get("abc"); // undefined

```

## getAll

```TypeScript
getAll(name: string): string[]
```

获取指定名称的所有键值对。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getAll

<!--Device-URLSearchParams-getAll(name: string): string[]--><!--Device-URLSearchParams-getAll(name: string): string[]-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 指定的键值名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回指定名称的所有键值对。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search.slice(1));
params.append('fod', '3'); // Add a second value for the fod parameter.
console.info(params.getAll('fod').toString()) // Output ["1","3"].

```

## has

```TypeScript
has(name: string): boolean
```

判断一个指定的键名对应的值是否存在。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** has

<!--Device-URLSearchParams-has(name: string): boolean--><!--Device-URLSearchParams-has(name: string): boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 要查找的参数的键名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 是否存在相对应的key值。存在返回true，否则返回false。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.has('bard') === true;

```

## keys

```TypeScript
keys(): IterableIterator<string>
```

返回一个所有键值对的name的ES6迭代器。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** keys

<!--Device-URLSearchParams-keys(): IterableIterator<string>--><!--Device-URLSearchParams-keys(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | 返回一个所有键值对的name的ES6迭代器。 |

**示例：**

```TypeScript
let searchParamsObject = new url.URLSearchParams("key1=value1&key2=value2");
let keys = searchParamsObject.keys();
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

将与name关联的URLSearchParams对象中的值设置为value。如果存在名称为name的键值对，请将第一个键值对的值设置为value并删除所有其他值。如果不是，则将键值对附加到查询字符串。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** set

<!--Device-URLSearchParams-set(name: string, value: string): void--><!--Device-URLSearchParams-set(name: string, value: string): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| name | string | 是 | 将要设置的参数的键值名。 |
| value | string | 是 | 所要设置的参数值。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.

```

## sort

```TypeScript
sort(): void
```

对包含在此对象中的所有键值对进行排序，并返回undefined。排序顺序是根据键的Unicode代码点。该方法使用稳定的排序算法 （即，将保留具有相等键的键值对之间的相对顺序）。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sort

<!--Device-URLSearchParams-sort(): void--><!--Device-URLSearchParams-sort(): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例：**

```TypeScript
let searchParamsObject = new url.URLSearchParams("c=3&a=9&b=4&d=2"); // Create a test URLSearchParams object
searchParamsObject.sort(); // Sort the key/value pairs
console.info(searchParamsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2

```

## toString

```TypeScript
toString(): string
```

返回序列化为字符串的搜索参数，必要时对字符进行百分比编码。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** toString

<!--Device-URLSearchParams-toString(): string--><!--Device-URLSearchParams-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回序列化为字符串的搜索参数，必要时对字符进行百分比编码。 |

**示例：**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search.slice(1));
params.append('fod', '3');
console.info(params.toString()); // Output 'fod=1&bard=2&fod=3'

```

## values

```TypeScript
values(): IterableIterator<string>
```

返回一个所有键值对的value的ES6迭代器。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** values

<!--Device-URLSearchParams-values(): IterableIterator<string>--><!--Device-URLSearchParams-values(): IterableIterator<string>-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IterableIterator&lt;string&gt; | 返回一个所有键值对的value的ES6迭代器。 |

**示例：**

```TypeScript
let searchParams = new url.URLSearchParams("key1=value1&key2=value2");
let values = searchParams.values();
for (let value of values) {
  console.info(value);
}
// value1
// value2

```

