# @ohos.util.json (JSON Parsing and Generation)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong-->
<!--Designer: @Malzahar-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=0ca267adc0edf5d3b32e822276f56aef26b71514 translatedAt=2026-11-06T09:24:37.169Z pushedAt=2026-11-13T06:41:18.345Z nl=1 -->

This module provides functions such as converting JSON text into JSON objects or values, and converting objects into JSON text. The module implements parsing and serialization based on the standard JSON specification, supports custom conversion through the Transformer mechanism, resolves BigInt compatibility issues through the BigIntMode policy, and provides has/remove operations for querying and deleting properties of parsing results. It also provides the parseSendable API to parse JSON text into Sendable objects that can be shared across threads.

>**NOTE**
>
> The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { JSON } from '@kit.ArkTS';
```

## Transformer

type Transformer = (this: Object, key: string, value: Object) => Object | undefined | null

Function type used to transform results.<br>
When used as a parameter of the [JSON.parse](#jsonparse) function, this function is called for each key-value pair in the parsing result in depth-first order (starting from the innermost node and proceeding outward layer by layer). this points to the object to which the current key-value pair belongs, and the return value replaces the original value. If undefined is returned, the property is deleted.<br>
When used as a parameter of the [JSON.stringify](#jsonstringify-1) function, the serialization engine calls this function for each property in an outside-in order. this points to the object to which the current property belongs, and the return value is used as the serialization result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| this   | Object | Yes | The object to which the key-value pair being parsed or serialized belongs. |
| key  | string | Yes | The property name of the object member currently being handled, used to identify the key being parsed or serialized in the transform function. |
| value  | Object | Yes | The value of the key-value pair being parsed or serialized. |

**Returns**

| Type| Description|
| -------- | -------- |
| Object \| undefined \| null | Returns the property value after conversion; when undefined is returned, the property is removed from the result; when null is returned, the property value is set to null. |

## BigIntMode

Defines the mode for handling BigInt. Because the JSON specification does not support the BigInt type and the Number precision range is from -(2^53-1) to (2^53-1), this module provides three modes to meet the integer precision requirements of different scenarios.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Value| Description           |
| ------ | ------ | --------------- |
| DEFAULT   | 0 | BigInt is not supported, and extremely large integers may lose precision. This mode is suitable for regular JSON parsing scenarios that do not need to handle extremely large integers.|
| PARSE_AS_BIGINT   | 1 | When an integer is less than -(2^53-1) or greater than (2^53-1), it is parsed as BigInt; ordinary integers are still handled as number. This mode is suitable for scenarios where JSON may contain large integers beyond the safe integer range, but ordinary integers do not need BigInt.|
| ALWAYS_PARSE_AS_BIGINT   | 2 | All integers are parsed as BigInt. This mode is suitable for scenarios where all integers need to preserve precision in BigInt form, such as high-precision numerical computation.|

## ParseOptions

Describes the parsing options, which define the BigInt processing mode and the return type of the parsing result.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional|Description           |
| ------ | ------ | ---- | ---- | --------------- |
| bigIntMode   | [BigIntMode](#bigintmode) | No| No| Mode for processing BigInt.|
| parseReturnType   | [ParseReturnType](#parsereturntype) | No | Yes | Defines the type of the parsing result. When omitted, the default is OBJECT. It takes effect only for [JSON.parseSendable](#jsonparsesendable); [JSON.parse](#jsonparse) ignores this field.<br>**Since:** 26.0.1<br>**Model Constraint:** This API can be used only in the stage model.<br>**Atomic Service API:** Since API version 26.0.1, this API is supported in atomic services.|

## JSON.parse

parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null

Parses a JSON string to generate an ArkTS object or null. During parsing, each key-value pair is processed by the reviver function in order from the innermost to the outermost layer, and the return value replaces the original value. When ParseOptions is passed to specify BigIntMode, integers that meet the condition are parsed as BigInt. When the input string is 'null', null is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description           |
| ------ | ------ | ---- | --------------- |
| text   | string | Yes | A valid JSON string that complies with the JSON syntax specification. |
| reviver  | [Transformer](#transformer) | No | Transformer function used to modify the original value generated by parsing; used when custom transformation of the parsing result is required. The default value is undefined. |
| options   | [ParseOptions](#parseoptions) | No | Parsing configuration options used to control the type generated by parsing. The default value is undefined. |

**Returns**

| Type| Description|
| -------- | -------- |
| Object \| null | When the input string is 'null', null is returned. |

**Example**

```ts
import { JSON } from '@kit.ArkTS';

function reviverFunc(key: string, value: Object): Object | undefined | null {
  if (key === "age" && typeof value === 'number') {
    return value + 1;
  }
  return value;
}

const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let parsedObj = JSON.parse(jsonText);
console.info((parsedObj as object)?.["name"]);
// Output: John

const jsonTextStr = '{"name": "John", "age": 30}';
let objRst = JSON.parse(jsonTextStr, reviverFunc);
console.info((objRst as object)?.["age"]);
// Output: 31

const numberText = '{"number": 10, "largeNumber": 112233445566778899}';
let options: JSON.ParseOptions = { bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT };
let numberObj = JSON.parse(numberText, null, options) as Object;

console.info(typeof (numberObj as object)?.["number"]);
// Print result: number
console.info((numberObj as object)?.["number"]);
// Print result: 10

console.info(typeof (numberObj as object)?.["largeNumber"]);
// Print result: bigint
console.info((numberObj as object)?.["largeNumber"]);
// Print result: 112233445566778899
```

## JSON.stringify

stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string

This method converts an ArkTS object or array into a JSON string. It supports the conversion of linear containers but does not support nonlinear containers (nonlinear containers cannot be serialized correctly when passed in).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | Object | Yes | ArkTS object or array. Supports conversion of linear containers, but does not support nonlinear containers. |
| replacer | number[] \| string[] \| null | No | Used to filter the properties to be serialized. When the parameter is string[], only the object property names contained in the array are serialized; when the parameter is number[], only the array elements at the corresponding indexes are serialized; when the parameter is null or not provided, all properties of the object are serialized. The default value is undefined. |
| space | string \| number | No | Specifies the spaces or string used for indentation to beautify the output. When the parameter is a number, it indicates the number of indentation spaces and must be a non-negative integer; when the parameter is a string, it indicates the indentation character; if no parameter is provided, there is no indentation. The default value is an empty string. |

**Returns**

| Type| Description|
| -------- | -------- |
| string | Represents a JSON-format text string generated after an Object or Array is serialized. |

**Example**

```ts
import { JSON } from '@kit.ArkTS';

interface Person {
  name: string;
  age: number;
  city: string;
}

let person: Person = { name: "John", age: 30, city: "New York" };

let rstArrStr = JSON.stringify(person, ["name", "age"]);
console.info(rstArrStr);
// Output: {"name":"John","age":30}

let rstStrSpace = JSON.stringify(person, ["name", "age"], '  ');
console.info(rstStrSpace);
/*
Output:
{
  "name": "John",
  "age": 30
}
 */

let rstStrStar = JSON.stringify(person, ["name", "age"], '  &&');
console.info(rstStrStar);
/*
Output:
{
  &&"name": "John",
  &&"age": 30
}
 */

let bigIntObj = BigInt(112233445566778899n);
console.info(JSON.stringify(bigIntObj));
// Output: 112233445566778899
```

## JSON.stringify

stringify(value: Object, replacer?: Transformer, space?: string | number): string

Converts an ArkTS object or array into a JSON string. In the case of a container, linear containers are supported, but non-linear containers are not.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | Object | Yes| ArkTS object or array. In the case of a container, linear containers are supported, but non-linear containers are not.|
| replacer | [Transformer](#transformer) | No | During serialization, each property of the value being serialized is transformed and handled by this function. If this parameter is not provided, all properties of the object are serialized directly without transformation. The default value is undefined. |
| space | string \| number | No | Specifies the spaces or string used for indentation to beautify the output. If this parameter is a number, it indicates the number of indentation spaces. If this parameter is a string, it indicates the indentation characters. If no parameter is provided, there is no indentation. The default value is an empty string. |

**Returns**

| Type| Description|
| -------- | -------- |
| string | Represents a JSON-format text string generated after an Object or Array is serialized. |

**Example**

```ts
import { JSON } from '@kit.ArkTS';

function replacer(key: string, value: Object): Object {
  if (typeof value === 'string') {
    return value.toUpperCase();
  }
  return value;
}

interface Person {
  name: string;
  age: number;
  city: string;
}
let inputObj = {"name": "John", "age": 30, "city": "ChongQing"} as Person;

console.info(JSON.stringify(inputObj, replacer));
// Output: {"name":"JOHN","age":30,"city":"CHONGQING"}

console.info(JSON.stringify(inputObj, replacer, '  '));
/*
Output:
{
  "name": "JOHN",
  "age": 30,
  "city": "CHONGQING"
}
 */
```

## JSON.has

has(obj: object, property: string): boolean

Checks whether an ArkTS object contains a certain property. It can be used after [JSON.parse](#jsonparse) parses a JSON string. The has API supports only valid JSON strings whose outermost layer is in dictionary form (that is, enclosed in braces rather than brackets). When an object in non-dictionary form is passed in, whether the property exists cannot be correctly determined.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | object | Yes | ArkTS object. Only objects parsed from valid JSON strings whose outermost layer is in dictionary form (that is, enclosed in braces rather than brackets) are supported. |
| property | string | Yes | Name of the property to check, used to specify the property whose existence in the ArkTS object is to be determined. |

**Returns**

| Type| Description|
| -------- | -------- |
| boolean | Returns whether the ArkTS object contains the specified property. true indicates that the object contains the specified property; false indicates that the object does not contain the specified property. |

**Example**

```ts
import { JSON } from '@kit.ArkTS';

const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let inputObj = JSON.parse(jsonText);
let hasNameResult = JSON.has(inputObj, "name");
console.info("hasNameResult = " + hasNameResult);
// Print result: hasNameResult = true
```


## JSON.remove

remove(obj: object, property: string): void

Deletes a certain property from an ArkTS object. It can be used after [JSON.parse](#jsonparse) parses a JSON string, for example, to clean up sensitive fields and remove redundant data. The JSON.remove API supports only valid JSON strings whose outermost layer is in dictionary form (that is, enclosed in braces rather than brackets).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| obj | object | Yes | ArkTS object. Only objects parsed from valid JSON strings whose outermost layer is in dictionary form (that is, enclosed in braces rather than brackets) are supported. |
| property | string | Yes | Name of the property to delete, used to specify the property to remove from the ArkTS object. |

**Example**

```ts
import { JSON } from '@kit.ArkTS';

const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let inputObj = JSON.parse(jsonText);
JSON.remove(inputObj, "name");
let result = JSON.has(inputObj, "name");
console.info("result = " + result);
// Print result: result = false.
```

## JSON.parseSendable

parseSendable(text: string, reviver?: SendableTransformer, options?: ParseOptions): ISendable | null

Parses a JSON string to generate a Sendable object that can be shared across threads.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| text | string | Yes | Valid JSON string that conforms to the JSON syntax specification. |
| reviver | [SendableTransformer](#sendabletransformer) | No | Function used to transform the result. Currently only undefined is accepted; passing a function throws a TypeError (consistent with [ArkTSUtils.ASON.parse](arkts-apis-arkts-utils-ASON.md#parse)). The default value is undefined. |
| options | [ParseOptions](#parseoptions) | No | Parsing configuration options, used to control the mode for handling BigInt and the type of the parsing result. A ParseOptions object containing only bigIntMode can also be passed, in which case parseReturnType defaults to OBJECT. The default value is undefined. |

**Return value**

| Type | Description |
| -------- | -------- |
| [ISendable](#isendable) \| null | Returns the Sendable object corresponding to the JSON string; returns null when the JSON string is 'null'; returns collections.Map when options.parseReturnType is [ParseReturnType.MAP](#parsereturntype). |

> **Numeric key storage rules:**
> - Numeric string keys in the range from "0" to "4294967294" are stored as element indexes, and all key-value pairs can be fully accessed and enumerated regardless of the number of properties.
> - Keys with leading zeros (such as "00" and "01"), signs (such as "-0" and "+1"), decimal or exponent forms (such as "1.0" and "1e2"), or those exceeding the array index range (such as "4294967295") are stored as ordinary property names.
> - For duplicate keys, the later value takes precedence, and the enumeration position remains at the first occurrence.
> 
> **OBJECT and MAP return description:**
> - [ParseReturnType.OBJECT](#parsereturntype) (default): Returns a non-extensible Sendable object whose existing properties can be updated but cannot be added or deleted.
> - [ParseReturnType.MAP](#parsereturntype): Returns collections.Map, which supports adding and deleting any number of entries. Keys are always strings ("1" is not converted to a numeric key).

**Example**

```ts
import { JSON, collections, lang } from '@kit.ArkTS';

// Basic usage: Parse into a Sendable object that can be passed directly across Worker/TaskPool
let sendableObj: lang.ISendable | null = JSON.parseSendable('{"name": "John", "age": 30}');
console.info(`result: ${(sendableObj as object)?.["name"]}`); // Print result: result: John

// 86 numeric keys: all numeric keys are accessible regardless of quantity
let parts86: string[] = [];
for (let i = 0; i < 86; i++) {
  parts86.push('"' + i + '": ' + i * 2);
}
let numericObj86: lang.ISendable | null = JSON.parseSendable('{' + parts86.join(',') + '}');
console.info(`result: ${(numericObj86 as object)?.[84]}`); // Print result: result: 168
console.info(`result: ${(numericObj86 as object)?.[85]}`); // Print result: result: 170

// 1021 numeric keys: all remain accessible when the property count exceeds 1020
let parts1021: string[] = [];
for (let i = 0; i < 1021; i++) {
  parts1021.push('"' + i + '": ' + i);
}
let numericObj1021: lang.ISendable | null = JSON.parseSendable('{' + parts1021.join(',') + '}');
console.info(`result: ${(numericObj1021 as object)?.[0]}`); // Print result: result: 0
console.info(`result: ${(numericObj1021 as object)?.[1020]}`); // Print result: result: 1020

// MAP return type: any number of entries can be added or removed, with string keys
let mapOptions: JSON.ParseOptions = {
  bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT,
  parseReturnType: JSON.ParseReturnType.MAP
};
let sendableMap: lang.ISendable | null = JSON.parseSendable('{"a": 1, "b": 2}', undefined, mapOptions);
console.info(`result: ${(sendableMap as collections.Map<string, number>).get("a")}`); // Print result: result: 1

// You can also pass a ParseOptions object containing only bigIntMode (parseReturnType defaults to OBJECT)
let bigOptions: JSON.ParseOptions = {
  bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT
};
let bigObj: lang.ISendable | null = JSON.parseSendable('{"largeNumber":112233445566778899}', undefined, bigOptions);
console.info(`result: ${(bigObj as object)?.["largeNumber"]}`); // Print result: result: 112233445566778899

// reviver currently accepts only undefined
try {
  JSON.parseSendable('{"a": 1}', (key: string, value: lang.ISendable): lang.ISendable | undefined => {
    return value;
  });
} catch (e) {
  console.error(`error: ${(e as Error).message}`);
  // Print result: error: Parameter error. Reviver only supports undefined currently.
}
```

## ParseReturnType

Defines the type of the Sendable parsing result. It takes effect only for [JSON.parseSendable](#jsonparsesendable); [JSON.parse](#jsonparse) ignores this field.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

| Name | Value | Description |
| ------ | ------ | --------------- |
| OBJECT | 0 | The parsing result is a non-extensible Sendable object. Its existing properties can be updated, but cannot be added or deleted. |
| MAP | 1 | The parsing result is a collections.Map, which supports adding and deleting any number of entries. |

## ISendable

type ISendable = lang.ISendable

**ISendable** is the parent type of all sendable types except `null` and `undefined`. It does not define any methods or properties.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

| Type | Description |
| ------ | ------ |
| [lang.ISendable](js-apis-arkts-lang.md#isendable) | The parent type of all Sendable types. |

## SendableTransformer

type SendableTransformer = (this: ISendable, key: string, value: ISendable | undefined | null) => ISendable | undefined | null

Function type used to transform the parsing result of Sendable JSON. It is consistent with [ArkTSUtils.ASON.Transformer](arkts-apis-arkts-utils-ASON.md#transformer): this, value, and the return value are all ISendable (rather than Object), because the product of parseSendable is a Sendable object that can be shared across threads.

**Since:** 26.0.1

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type   | Mandatory | Description            |
| ------ | ------ | ---- | --------------- |
| this   | [ISendable](#isendable) | Yes | The Sendable object to which the parsed key-value pair belongs.|
| key  | string | Yes | Key to parse.|
| value  | [ISendable](#isendable) \| undefined \| null| Yes | The value of the parsed key-value pair.|

**Return value**

| Type | Description |
| -------- | -------- |
| [ISendable](#isendable) \| undefined \| null | Returns the transformed ISendable object, undefined, or null.|
