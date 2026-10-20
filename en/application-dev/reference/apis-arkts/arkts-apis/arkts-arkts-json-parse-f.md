# parse

## Modules to Import

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## parse

```TypeScript
function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null
```

Parses a JSON string into an ArkTS object or null.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null--><!--Device-json-function parse(text: string, reviver?: Transformer, options?: ParseOptions): Object | null-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Valid JSON string. |
| reviver | [Transformer](arkts-arkts-json-transformer-t.md) | No | Conversion function. This parameter can be used to modify the value generated after parsing. The default value is undefined. |
| options | [ParseOptions](arkts-arkts-json-parseoptions-i.md) | No | Parsing options. This parameter is used to control the type of the parsing result. The default value is undefined. |

**Return value:**

| Type | Description |
| --- | --- |
| Object &#124; null | Return an Object, array, string, number, boolean, or null value corresponding to JSON text. |

**Examples**

```TypeScript
import { JSON } from '@kit.ArkTS';

function reviverFunc(key: string, value: Object): Object | undefined | null {
  if (key === "age" && typeof value === 'number') {
    return value + 1;
  }
  return value;
}

const jsonText = '{"name": "John", "age": 30, "city": "ChongQing"}';
let obj = JSON.parse(jsonText);
console.info((obj as object)?.["name"]);
// Output: John

const jsonTextStr = '{"name": "John", "age": 30}';
let objRst = JSON.parse(jsonTextStr, reviverFunc);
console.info((objRst as object)?.["age"]);
// Output: 31

const numberText = '{"number": 10, "largeNumber": 112233445566778899}';
let options: JSON.ParseOptions = { bigIntMode: JSON.BigIntMode.PARSE_AS_BIGINT }
let numberObj = JSON.parse(numberText, null, options) as Object;

console.info(typeof (numberObj as object)?.["number"]);
// Output: number
console.info((numberObj as object)?.["number"]);
// Output: 10

console.info(typeof (numberObj as object)?.["largeNumber"]);
// Output: bigint
console.info((numberObj as object)?.["largeNumber"]);
// Output: 112233445566778899
```
