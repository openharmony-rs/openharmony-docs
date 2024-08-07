# @ohos.util.json (JSON解析与生成)

本模块提供了将JSON文本转换为JSON对应对象或值，以及将对象转换为JSON字符串等功能。

>**说明：**
>
>本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```ts
import { JSON } from '@kit.ArkTS';
```

## Transformer

type Transformer = (this: Object, key: string, value: Object) => Object | undefined | null

用于转换结果函数的类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| this   | Object | 是 | 在解析的键值对所属的对象。|
| key  | string | 是 | 属性名。|
| value  | Object | 是 | 在解析的键值对的值。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Object \| undefined \| null | 返回修改后的对象或undefined或null。|

## BigIntMode

定义处理BigInt的模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 值| 说明            |
| ------ | ------ | --------------- |
| DEFAULT   | 0 |不支持BigInt。|
| PARSE_AS_BIGINT   | 1 |当整数小于-(2^53-1)或大于(2^53-1)时，解析为BigInt。|
| ALWAYS_PARSE_AS_BIGINT   | 2 |所有整数都解析为BigInt。|

## ParseOptions

解析的选项，可定义处理BigInt的模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 类型| 必填 |说明            |
| ------ | ------ | ---- | --------------- |
| bigIntMode   | [BigIntMode](#bigintmode) | 是 |定义处理BigInt的模式。|

## JSON.parse

parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null

用于解析JSON字符串生成对应ArkTS对象或null。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| text   | string | 是 | 有效的JSON字符串。|
| reviver  | [Transformer](#transformer) | 否 | 转换函数，传入该参数，可以用来修改解析生成的原始值。默认值是undefined。|
| options   | [ParseOptions](#parseoptions) | 否 | 解析的配置，传入该参数，可以用来控制解析生成的类型。默认值是undefined。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Object \| null | 返回ArkTS对象或null。当入参是null时，返回null。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
let jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let obj = JSON.parse(jsonText);

let options: JSON.ParseOptions = {
  bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT,
}
let numberText = '{"largeNumber":112233445566778899}';
let numberObj = JSON.parse(numberText,(key: string, value: Object | undefined | null): Object | undefined | null => {
  if(key === "largeNumber") return value;
  return value;
},options) as Object;

console.info((numberObj as object)?.["largeNumber"]);
// 期望输出: 112233445566778899
```


## JSON.stringify

stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string

该方法将一个ArkTS对象或数组转换为JSON字符串。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | Object | 是 | ArkTS对象或数组。|
| replacer | number[] \| string[] \| null | 否 | 当参数是数组时，只有包含在这个数组中的属性名才会被序列化到最终的JSON字符串中；当参数为null或者未提供时，则对象所有的属性都会被序列化。默认值是undefined。|
| space | string \| number | 否 | 指定缩进用的空格或字符串或空字符串，用于美化输出。当参数是数字时表示有多少个空格；当参数是字符串时，该字符串被当作空格；当参数没有提供时，将没有空格。默认值是空字符串。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 转换后的JSON字符串。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
interface Person {
  name: string;
  age: number;
  city: string;
}
let obj = {"name": "John", "age": 30, "city": "ChongQing"} as Person;
let str1 = JSON.stringify(obj, ["name"]);
```


## JSON.stringify

stringify(value: Object, replacer?: Transformer, space?: string | number): string

该方法将一个ArkTS对象或数组转换为JSON字符串。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | Object | 是 | ArkTS对象或数组。|
| replacer | [Transformer](#transformer) | 否 | 在序列化过程中，被序列化的值的每个属性都会经过该函数的转换和处理。默认值是undefined。|
| space | string \| number | 否 | 指定缩进用的空格或字符串或空字符串，用于美化输出。当参数是数字时表示有多少个空格；当参数是字符串时，该字符串被当作空格；当参数没有提供时，将没有空格。默认值是空字符串。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 转换后的JSON字符串。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```ts
function replacer(key: string, value: Object): Object {
  if (typeof value === "string") {
    return value.toUpperCase();
  }
  return value;
}
interface Person {
  name: string;
  age: number;
  city: string;
}

let obj = {"name": "John", "age": 30, "city": "ChongQing"} as Person;
let str2 = JSON.stringify(obj, replacer);
```


## JSON.has

has(obj: object, property: string): boolean

检查ArkTS对象是否包含某种属性，可用于[JSON.parse](#jsonparse)解析JSON字符串之后的相关操作。has接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法json串。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| obj | object | 是 | ArkTS对象。|
| property | string | 是 | 属性名。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| boolean | 返回ArkTS对象是否包含某种属性结果，true表示包含，false表示不包含。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let obj = JSON.parse(jsonText);
let rst = JSON.has(obj, "name");
```


## JSON.remove

remove(obj: object, property: string): void

从ArkTS对象中删除某种属性，可用于[JSON.parse](#jsonparse)解析JSON字符串之后的相关操作。remove接口仅支持最外层为字典形式（即大括号而非中括号包围）的合法json串。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| obj | object | 是 | ArkTS对象。|
| property | string | 是 | 属性名。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**示例：**

```ts
const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let obj = JSON.parse(jsonText);
let rst = JSON.remove(obj, "name");
```