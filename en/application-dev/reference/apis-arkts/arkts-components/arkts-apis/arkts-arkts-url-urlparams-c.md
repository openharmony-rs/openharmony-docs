# URLParams

The URLParams interface defines some practical methods to process URL query strings.

**Since:** 9

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { url } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[string, string]>
```

Obtains an ES6 iterator. Each item of the iterator is a JavaScript array, and the first and second fields ofeach array are the key and value respectively.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[string, string]&gt; | Returns an ES6 iterator. Each item of the iterator is a JavaScript Array. The first item of Array is name, and the second item of Array is value. |

**Examples**

```TypeScript
const paramsObject = new url.URLParams('fod=bay&edg=bap');
let iter = paramsObject[Symbol.iterator]();
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

Appends a key-value pair into the query string.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key of the key-value pair to append. |
| value | string | Yes | Value of the key-value pair to append. |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
paramsObject.append('fod', '3');
```

## constructor

```TypeScript
constructor(init?: string[][] | Record<string, string> | string | URLParams)
```

A constructor used to create a URLParams instance.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| init | string[][] &#124; Record&lt;string, string&gt; &#124; string &#124; [URLParams](arkts-arkts-url-urlparams-c.md) | No | Input parameter objects, which include the following:   - string[][]: two-dimensional string array.   - Record&lt;string, string&gt;: list of objects.   - string: string.   - URLParams: object.   The default value is null. |

**Examples**

```TypeScript
// Construct a URLParams object in string[][] mode.
let objectParams = new url.URLParams([ ['user1', 'abc1'], ['query2', 'first2'], ['query3', 'second3'] ]);
// Construct a URLParams object in Record<string, string> mode.
let objectParams1 = new url.URLParams({"fod" : '1' , "bard" : '2'});
// Construct a URLParams object in string mode.
let objectParams2 = new url.URLParams('?fod=1&bard=2');
// Construct a URLParams object using the search property of the url object.
let urlObject = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams3 = new url.URLParams(urlObject.search);
// Construct a URLParams object using the params property of the url object.
let urlObject1 = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams4 = urlObject1.params;
```

## delete

```TypeScript
delete(name: string): void
```

Deletes key-value pairs of the specified key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key of the key-value pairs to delete. |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
paramsObject.delete('fod');
```

## entries

```TypeScript
entries(): IterableIterator<[string, string]>
```

Obtains an ES6 iterator. Each item of the iterator is a JavaScript array, and the first and second fields of each array are the key and value respectively.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[string, string]&gt; | Returns an iterator for ES6. |

**Examples**

```TypeScript
let paramsObject = new url.URLParams("keyName1=valueName1&keyName2=valueName2");
let pair = paramsObject.entries();
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

Callback functions are used to traverse key-value pairs on the URLParams instance object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: string, key: string, searchParams: URLParams) =&gt; void | Yes | callbackFn value Current traversal key value, key Indicates the name of the key that is traversed. |
| thisArg | Object | No | thisArg to be used as this value for when callbackFn is called |

**Examples**

```TypeScript
const myURLObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
myURLObject.params.forEach((value, name, searchParams) => {
    console.info(name, value, myURLObject.params === searchParams);
});
```

## get

```TypeScript
get(name: string): string | null
```

Obtains the value of the first key-value pair based on the specified key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key specified to obtain the value. |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Returns the first value found by name. If no value is found, null is returned. |

**Examples**

```TypeScript
let paramsObject = new url.URLParams('name=Jonathan&age=18');
let name = paramsObject.get("name"); // is the string "Jonathan"
let age = paramsObject.get("age"); // is the string "18"
let getObj = paramsObject.get("abc"); // undefined
```

## getAll

```TypeScript
getAll(name: string): string[]
```

Obtains all the values based on the specified key.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Target key. |

**Return value:**

| Type | Description |
| --- | --- |
| string[] | string[] Returns all key-value pairs with the specified name. |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLParams(urlObject.search.slice(1));
params.append('fod', '3'); // Add a second value for the fod parameter.
console.info(params.getAll('fod').toString()) // Output ["1","3"].
```

## has

```TypeScript
has(name: string): boolean
```

Checks whether a key has a value.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key specified to search for its value. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns a Boolean value that indicates whether a found |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
let result = paramsObject.has('bard');
```

## keys

```TypeScript
keys(): IterableIterator<string>
```

Obtains an ES6 iterator that contains the keys of all the key-value pairs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | Returns an ES6 Iterator over the names of each name-value pair. |

**Examples**

```TypeScript
let paramsObject = new url.URLParams("key1=value1&key2=value2");
let keys = paramsObject.keys();
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

Sets the value for a key. If key-value pairs matching the specified key exist, the value of the first key- value pair will be set to the specified value and other key-value pairs will be deleted. Otherwise, the key-value pair will be appended to the query string.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Key of the value to set. |
| value | string | Yes | Value to set. |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.
```

## sort

```TypeScript
sort(): void
```

Sorts all key-value pairs contained in this object based on the Unicode code points of the keys and returns undefined. This method uses a stable sorting algorithm, that is, the relative order between key-value pairs with equal keys is retained.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let paramsObject = new url.URLParams("c=3&a=9&b=4&d=2"); // Create a test URLParams object
paramsObject.sort(); // Sort the key/value pairs
console.info(paramsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2
```

## toString

```TypeScript
toString(): string
```

Obtains search parameters that are serialized as a string and, if necessary, percent-encodes the characters in the string.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns a search parameter serialized as a string, percent-encoded if necessary. |

**Examples**

```TypeScript
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLParams(urlObject.search.slice(1));
params.append('fod', '3');
console.info(params.toString()); // Output 'fod=1&bard=2&fod=3'
```

## values

```TypeScript
values(): IterableIterator<string>
```

Obtains an ES6 iterator that contains the values of all the key-value pairs.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | Returns an ES6 Iterator over the values of each name-value pair. |

**Examples**

```TypeScript
let paramsObject = new url.URLParams("key1=value1&key2=value2");
let values = paramsObject.values();
for (let value of values) {
  console.info(value);
}
// value1
// value2
```
