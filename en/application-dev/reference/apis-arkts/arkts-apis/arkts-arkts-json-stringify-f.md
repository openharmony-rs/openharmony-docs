# stringify

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## stringify

```TypeScript
function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string
```

Converts an ArkTS object or array into a JSON string. In the case of a container, linear containers are supported, but non-linear containers are not.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: (number | string)[] | null, space?: string | number): string-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | ArkTS object or array. In the case of a container, linear containers are supported, but non-linear containers are not. |
| replacer | (number &#124; string)[] &#124; null | No | If an array is passed in, only the keys in the array are serialized to the final JSON string. If null is passed in, all keys of the object are serialized. The default value is undefined. |
| space | string &#124; number | No | White spaces or strings inserted into the output JSON string for readability purposes. If the parameter is a number, it represents the number of indentation spaces; if it is a string, it represents the indentation characters. If no parameter is provided, there will be no indentation. The default value is an empty string. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return a JSON text. |

**Examples**

```TypeScript
import { JSON } from '@kit.ArkTS';

interface Person {
  name: string;
  age: number;
  city: string;
}

let person: Person = {name: "John",age: 30, city: "New York"};

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


## stringify

```TypeScript
function stringify(value: Object, replacer?: Transformer, space?: string | number): string
```

Converts an ArkTS object or array into a JSON string. In the case of a container, linear containers are supported, but non-linear containers are not.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string--><!--Device-json-function stringify(value: Object, replacer?: Transformer, space?: string | number): string-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Object | Yes | ArkTS object or array. In the case of a container, linear containers are supported, but non-linear containers are not. |
| replacer | [Transformer](arkts-arkts-json-transformer-t.md) | No | During serialization, each key of the serialized value is converted and processed by this function. The default value is undefined. |
| space | string &#124; number | No | Indentation, white space, or line break characters inserted into the output JSON string for readability purposes. If a number is passed in, it indicates the number of space characters to be used as indentation. If a string is passed in, the string is inserted before the output JSON string. If null is passed in, no white space is used. The default value is an empty string. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return a JSON text. |

**Examples**

```TypeScript
import { JSON } from '@kit.ArkTS';

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
