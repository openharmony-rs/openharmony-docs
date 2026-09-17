# getHash

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## getHash

```TypeScript
function getHash(object: object): number
```

Obtains the hash value of an object. If no hash value has been obtained, a random hash value is generated, saved to the **hash** field of the object, and returned. If a hash value has been obtained, the hash value saved in the **hash** field is returned (the same value is returned for the same object).

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| object | object | Yes | Object whose hash value is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Hash value. |

**Examples**

```TypeScript
interface Person {
  name: string,
  age: number
}
let obj: Person = { name: 'Jack', age: 20 };
let result1 = util.getHash(obj);
console.info('result1 is ' + result1);
let result2 = util.getHash(obj);
console.info('result2 is ' + result2);
// Output: The values of result1 and result2 are the same and are a random hash value.
```
