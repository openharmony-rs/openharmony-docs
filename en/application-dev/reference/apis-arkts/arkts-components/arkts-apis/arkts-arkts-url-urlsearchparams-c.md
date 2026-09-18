# URLSearchParams

The URLSearchParams interface defines some practical methods to process URL query strings.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [URLParams](arkts-arkts-url-urlparams-c.md)

**System capability:** SystemCapability.Utils.Lang @name URLSearchParams

## Modules to Import

```TypeScript
import { url } from '@kit.ArkTS';
```

## [Symbol.iterator]

```TypeScript
[Symbol.iterator](): IterableIterator<[string, string]>
```

Returns an iterator allowing to go through all key/value pairs contained in this object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [Symbol.iterator]

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[string, string]&gt; | Returns an ES6 iterator. Each item of the iterator is a JavaScript Array. The first item of Array is name, and the second item of Array is value. |

**Examples**

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

Appends a specified key/value pair as a new search parameter.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** append

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The key name of the search parameter to insert |
| value | string | Yes | The value of the search parameter to insert |

**Examples**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.append('fod', '3');
```

## constructor

```TypeScript
constructor(init?: string[][] | Record<string, string> | string | URLSearchParams)
```

A parameterized constructor used to create an URLSearchParams instance. As the input parameter of the constructor function, init supports four types. The input parameter is a character string two-dimensional array. The input parameter is the object list. The input parameter is a character string. The input parameter is the URLSearchParams object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| init | string[][] &#124; Record&lt;string, string&gt; &#124; string &#124; URLSearchParams | No | init init |

**Examples**

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

Deletes the given search parameter and its associated value,from the list of all search parameters.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** delete

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The name of the key-value pair to delete |

**Examples**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.delete('fod');
```

## entries

```TypeScript
entries(): IterableIterator<[string, string]>
```

Returns an ES6 iterator. Each item of the iterator is a JavaScript Array. The first item of Array is name, and the second item of Array is value.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** entries

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;[string, string]&gt; | Returns an iterator for ES6. |

**Examples**

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

Callback functions are used to traverse key-value pairs on the URLSearchParams instance object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** forEach

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callbackFn | (value: string, key: string, searchParams: URLSearchParams) =&gt; void | Yes | The callback function to execute for each key-value pair |
| thisArg | Object | No | The value to use as this when executing callbackFn |

**Examples**

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

Returns the first value associated to the given search parameter.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** get

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The name of the key-value pair to get |

**Return value:**

| Type | Description |
| --- | --- |
| string &#124; null | Returns the first value found by name. If no value is found, null is returned. |

**Examples**

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

Returns all key-value pairs associated with a given search parameter as an array.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getAll

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The name of the key-value pairs to retrieve |

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Returns all key-value pairs with the specified name |

**Examples**

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

Returns a Boolean that indicates whether a parameter with the specified name exists.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** has

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The name of the key-value pair to check |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns a Boolean value that indicates whether a found |

**Examples**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.has('bard') === true;
```

## keys

```TypeScript
keys(): IterableIterator<string>
```

Returns an iterator allowing to go through all keys contained in this object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** keys

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | Returns an ES6 Iterator over the names of each name-value pair. |

**Examples**

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

Sets the value associated with a given search parameter to the given value. If there were several matching values, this method deletes the others. If the search parameter doesn't exist, this method creates it.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** set

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | The key name of the parameter to set |
| value | string | Yes | The value to set for the parameter |

**Examples**

```TypeScript
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.
```

## sort

```TypeScript
sort(): void
```

Sort all key/value pairs contained in this object in place and return undefined.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** sort

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let searchParamsObject = new url.URLSearchParams("c=3&a=9&b=4&d=2"); // Create a test URLSearchParams object
searchParamsObject.sort(); // Sort the key/value pairs
console.info(searchParamsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2
```

## toString

```TypeScript
toString(): string
```

Returns a query string suitable for use in a URL.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** toString

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns a search parameter serialized as a string, percent-encoded if necessary. |

**Examples**

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

Returns an iterator allowing to go through all values contained in this object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** values

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [IterableIterator](../../apis-default/arkts-apis/arkts-lib-es2015-iterable-iterableiterator-i.md)&lt;string&gt; | Returns an ES6 Iterator over the values of each name-value pair. |

**Examples**

```TypeScript
let searchParams = new url.URLSearchParams("key1=value1&key2=value2");
let values = searchParams.values();
for (let value of values) {
  console.info(value);
}
// value1
// value2
```
