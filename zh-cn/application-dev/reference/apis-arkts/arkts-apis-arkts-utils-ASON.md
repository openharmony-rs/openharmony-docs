# ArkTSUtils.ASON
<!--Kit: ArkTS-->
<!--Subsystem: commonlibrary-->
<!--Owner: @lijiamin2025-->
<!--SE: @weng-changcheng-->
<!--TSE: @kirl75; @zsw_zhushiwei-->

为支持将JSON字符串解析为共享数据，即[Sendable支持的数据类型](../../arkts-utils/arkts-sendable.md#sendable支持的数据类型)，ArkTS语言基础库新增了ASON工具。ASON工具支持解析JSON字符串并生成共享数据，用于跨并发实例引用传递，同时也支持将共享数据转换为JSON字符串。

> **说明：**
>
> 本模块首批接口从API version 12开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 此模块仅支持在ArkTS文件（文件后缀为.ets）中导入使用。

## 导入模块

```ts
import { ArkTSUtils } from '@kit.ArkTS'
```

## ISendable

type ISendable = lang.ISendable

ISendable是所有Sendable类型（除`null`和`undefined`）的父类型。自身没有任何必须的方法和属性。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 类型 | 说明   |
| ------ | ------ |
| [lang.ISendable](js-apis-arkts-lang.md#langisendable)   | 所有Sendable类型的父类型。 |

## Transformer

type Transformer = (this: ISendable, key: string, value: ISendable | undefined | null) => ISendable | undefined | null

用于转换结果函数的类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| this   | [ISendable](#isendable) | 是 | 在解析的键值对所属的对象。|
| key  | string | 是 | 属性名。|
| value  | [ISendable](#isendable) \| undefined \| null| 是 | 在解析的键值对的值。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ISendable](#isendable) \| undefined \| null | 返回转换结果后的ISendable对象或undefined或null。|

## BigIntMode

定义处理BigInt的模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 值| 说明            |
| ------ | ------ | --------------- |
| DEFAULT   | 0 |不支持BigInt。|
| PARSE_AS_BIGINT   | 1 |当整数小于-(2^53-1)或大于(2^53-1)时，解析为BigInt。|
| ALWAYS_PARSE_AS_BIGINT   | 2 |所有整数都解析为BigInt。|

## ParseReturnType

定义解析结果的返回类型。

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 值| 说明            |
| ------ | ------ | --------------- |
| OBJECT   | 0 |返回 SendableObject 对象。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| MAP<sup>13+</sup>   | 1 |返回 SendableMap 对象。<br>**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。|

## ParseOptions

解析的选项，可定义处理BigInt的模式和解析结果的返回类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

| 名称 | 类型| 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| bigIntMode   | [BigIntMode](#bigintmode) | 是 |定义处理BigInt的模式。|
| parseReturnType   | [ParseReturnType](#parsereturntype) | 是 |定义解析结果的返回类型。|

## parse

parse(text: string, reviver?: Transformer, options?: ParseOptions): ISendable | null

用于解析JSON字符串生成ISendable数据或null。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填 | 说明            |
| ------ | ------ | ---- | --------------- |
| text   | string | 是 | 有效的JSON字符串。|
| reviver   | [Transformer](#transformer) | 否 | 转换函数，传入该参数，可以用来修改解析生成的原始值。默认值是undefined。目前只支持传入undefined。|
| options   | [ParseOptions](#parseoptions) | 否 | 解析的配置，传入该参数，可以用来控制解析生成的结果类型。默认值是undefined。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| [ISendable](#isendable) \| null | 返回ISendable数据或null。入参为null时，返回null。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 401      | Parameter error. Invalid JSON string. |

**示例：**

```ts
import { lang } from '@kit.ArkTS';
import { collections } from '@kit.ArkTS';

type ISendable = lang.ISendable;
let jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let obj = ArkTSUtils.ASON.parse(jsonText) as ISendable;
console.info((obj as object)?.["name"]);
// 期望输出: 'John'
console.info((obj as object)?.["age"]);
// 期望输出: 30
console.info((obj as object)?.["city"]);
// 期望输出: 'ChongQing'

let options: ArkTSUtils.ASON.ParseOptions = {
  bigIntMode: ArkTSUtils.ASON.BigIntMode.PARSE_AS_BIGINT,
  parseReturnType: ArkTSUtils.ASON.ParseReturnType.OBJECT,
}
let numberText = '{"largeNumber":112233445566778899}';
let numberObj = ArkTSUtils.ASON.parse(numberText,undefined,options) as ISendable;

console.info((numberObj as object)?.["largeNumber"]);
// 期望输出: 112233445566778899

let options2: ArkTSUtils.ASON.ParseOptions = {
    bigIntMode: ArkTSUtils.ASON.BigIntMode.PARSE_AS_BIGINT,
    parseReturnType: ArkTSUtils.ASON.ParseReturnType.MAP,
  }
let mapText = '{"largeNumber":112233445566778899}';
let map  = ArkTSUtils.ASON.parse(mapText,undefined,options2);
console.info("map is " + map);
// 期望输出: map is [object SendableMap]
console.info("largeNumber is " + (map as collections.Map<string,bigint>).get("largeNumber"));
// 期望输出: largeNumber is 112233445566778899
```

## stringify

stringify(value: Object | null | undefined): string

该方法将ArkTS对象数据转换为JSON字符串，额外支持Map和Set相关类型。

> **说明：**
>
> 从API 18开始参数修改为Object类型，API 18之前参数只支持ISendable类型（除[collections.TypedArray](js-apis-arkts-collections.md#collectionstypedarray)外）。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| value | Object \| null \| undefined  | 是 | ArkTS对象数据。|

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| string | 转换后的JSON字符串。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 401      | Parameter error. Invalid ArkTS value. |

**示例：**

```ts
import { ArkTSUtils, collections, HashMap, HashSet } from '@kit.ArkTS';

let hashMap = new HashMap<string,string>();
hashMap.set("ha","a");
hashMap.set("sh","b");
hashMap.set("map","c");
let str1 = ArkTSUtils.ASON.stringify(hashMap);
console.info(str1);
//期望输出：'{"sh":"b","ha":"a","map":"c"}'
let hashSet = new HashSet<string>();
hashSet.add("ha");
hashSet.add("sh");
hashSet.add("set");
let str2 = ArkTSUtils.ASON.stringify(hashSet);
console.info(str2);
//期望输出：'["set","sh","ha"]'
let map = new Map<string,string>();
map.set("m","a");
map.set("a","b");
map.set("p","c");
let str3 = ArkTSUtils.ASON.stringify(map);
console.info(str3);
//期望输出：'{"m":"a","a":"b","p":"c"}'
let set = new Set<string>();
set.add("s");
set.add("e");
set.add("t");
let str4 = ArkTSUtils.ASON.stringify(set);
console.info(str4);
//期望输出：'["s","e","t"]'
let sendableMap = new collections.Map<string,string>();
sendableMap.set("send","a");
sendableMap.set("able","b");
sendableMap.set("map","c");
let str5 = ArkTSUtils.ASON.stringify(sendableMap);
console.info(str5);
//期望输出：'{"send":"a","able":"b","map":"c"}'
let sendableSet = new collections.Set<string>();
sendableSet.add("send");
sendableSet.add("able");
sendableSet.add("set");
let str6 = ArkTSUtils.ASON.stringify(sendableSet);
console.info(str6);
//期望输出：'["send","able","set"]'
```