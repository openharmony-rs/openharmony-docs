# @ohos.url (URL String Parsing)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-06T09:47:55.940Z pushedAt=2026-11-13T07:11:06.855Z nl=1 -->

A URL is a uniform resource locator. This module provides common utility functions for parsing URL strings, constructing URL objects, and parsing and manipulating URL query parameters. In addition, the URLUtil utility class provides the auxiliary capability of serializing a URLParams object into a string (with spaces percent-encoded as %20).<br>

The module mainly contains the following core classes:<br>

- [URL](#url): Used for parsing and constructing a complete URL. <br>

- [URLParams](#urlparams9): Used for manipulating URL query parameters. <br>

- [URLUtil](#urlutil): Used for serializing a URLParams object into a string, with spaces encoded as %20. <br>

- [URLSearchParams](#urlsearchparamsdeprecated): Deprecated since API version 9. It is recommended to use [URLParams](#urlparams9) instead. <br>

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { url } from '@kit.ArkTS';
```
## URLParams<sup>9+</sup>

URLParams is a utility class for parsing, constructing, and manipulating URL parameters. This class provides a unified interface for handling URL query parameters.

### constructor<sup>9+</sup>

constructor(init?: string[][] | Record&lt;string, string&gt; | string | URLParams)

The constructor of URLParams is used to create a URL parameter object, and is applicable to scenarios where URL query parameters need to be parsed, constructed, or manipulated.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
 | init | string[][] \| Record&lt;string, string&gt; \| string \| URLParams | No | Input parameter object.<br>- string[][]: two-dimensional string array.<br>- Record&lt;string, string&gt;: object list.<br>- string: URL query parameter string.<br>- URLParams: URLParams instance object.<br>- Default value: null. |

**Example**

```ts
// Construct a URLParams object in string[][] mode.
let objectParams = new url.URLParams([ ['user1', 'abc1'], ['query2', 'first2'], ['query3', 'second3'] ]);
// Construct a URLParams object in Record<string, string> mode.
let objectParams1 = new url.URLParams({'fod' : '1' , 'bard' : '2'});
// Construct a URLParams object in string mode.
let objectParams2 = new url.URLParams('?fod=1&bard=2');
// Construct a URLParams object using the search property of the url object.
let urlObject = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams3 = new url.URLParams(urlObject.search);
// Construct a URLParams object using the params property of the url object.
let secondUrlObj = url.URL.parseURL('https://developer.mozilla.org/?fod=1&bard=2');
let objectParams4 = secondUrlObj.params;
```


### append<sup>9+</sup>

append(name: string, value: string): void

Inserts a new key-value pair into the query string. Unlike the [set](#set9) method, append does not replace the value corresponding to an existing key name. Instead, it appends a new key-value pair, allowing multiple values to exist under the same key name. To replace an existing key value, use the set method.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key of the key-value pair to append.|
| value | string | Yes| Value of the key-value pair to append.|

**Example**

```ts
// Parse the URL string.
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// Construct a URLParams object.
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// Append a key-value pair.
paramsObject.append('fod', '3');
```


### delete<sup>9+</sup>

delete(name: string): void

Deletes all key-value pairs with the specified name. If the specified name does not exist, no operation is performed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Key name to delete. |

**Example**

```ts
// Parse the URL string
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// Construct a URLParams object
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// Delete the key-value pair with the specified name
paramsObject.delete('fod');
```


### getAll<sup>9+</sup>

getAll(name: string): string[]

Gets the set of all values corresponding to the specified name. If a key-value pair name that does not exist is searched for, the return value is an empty array.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Specified key name. |

**Return value**

| Type| Description|
| -------- | -------- |
| string[] | All the values obtained.|

**Example**

```ts
// Parse the URL and construct a URLParams object.
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLParams(urlObject.search.slice(1));
params.append('fod', '3'); // Append the second fod parameter value.
// Get all values of the specified name fod.
console.info(params.getAll('fod').toString()); // Output ["1","3"]
```


### entries<sup>9+</sup>

entries(): IterableIterator<[string, string]>

Returns an iterator, where each item of the iterator is an Array. The first item of the Array is name, and the second item of the Array is value. This method behaves the same as [Symbol.iterator], both returning an iterator of key-value pairs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[string, string]&gt; | Returns an iterator, where each item is a [string, string] array containing name and value. |

**Example**

```ts
// Construct a URLParams object.
let paramsObject = new url.URLParams('keyName1=valueName1&keyName2=valueName2');
// Obtain the entries iterator.
let pair = paramsObject.entries();
// Traverse the key-value pairs.
for (let item of pair) {
  console.info(item[0] + '=' + item[1]);
}
// keyName1=valueName1
// keyName2=valueName2
```


### forEach<sup>9+</sup>

forEach(callbackFn: (value: string, key: string, searchParams: URLParams) => void, thisArg?: Object): void

Traverses the key-value pairs on the URLParams instance object in insertion order through a callback function.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes | Callback function executed when traversing key-value pairs, called once for each key-value pair. |
| thisArg | Object | No| Value of **this** to use when **callbackFn** is invoked. The default value is this object.|

**Table 1** callbackFn parameter description

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string | Yes | Value of the current traversal. |
| key | string | Yes| Key that is currently traversed.|
| searchParams | [URLParams](#urlparams9) | Yes| Instance that invokes the **forEach** method.|

**Example**

```ts
// Parse the URL.
const myURLObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// Traverse the URLParams key-value pairs through the callback function.
myURLObject.params.forEach((value, name, searchParams) => {
    console.info(name, value, myURLObject.params === searchParams);
});
```


### get<sup>9+</sup>

get(name: string): string | null

Obtains the value of the first key-value pair based on the specified key.

> **NOTE**
>
> If the key-value pair does not exist, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Specifies the key name. |

**Return value**

| Type| Description|
| -------- | -------- |
| string \| null | The first value is returned. If no value is found, **null** is returned.|

**Example**

```ts
let paramsObject = new url.URLParams('name=Jonathan&age=18');
let name = paramsObject.get('name'); // is the string "Jonathan"
let age = paramsObject.get('age'); // is the string "18"
let absentValue = paramsObject.get('abc'); // undefined
```


### has<sup>9+</sup>

has(name: string): boolean

Checks whether a key has a value.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key specified to search for its value.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the value exists; otherwise, **false** is returned.|

**Example**

```ts
// Parse the URL string.
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// Construct a URLParams object.
let paramsObject = new url.URLParams(urlObject.search.slice(1));
// Check whether the key name bard exists.
let result = paramsObject.has('bard');
```


### set<sup>9+</sup>

set(name: string, value: string): void

Sets the value associated with name in the URLParams object to value.

If a key-value pair with the name name exists, set the value of the first key-value pair to value and delete all other values. If the key name does not exist, append the key-value pair to the query string.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Key name of the parameter to be set. |
| value | string | Yes| Value to set.|

**Example**

```ts
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.
```


### sort<sup>9+</sup>

sort(): void

Sorts all key-value pairs contained in this object, applicable to URL normalization scenarios (such as URL signing, cache key generation, and other scenarios that require consistent parameter order). The sort order is based on the Unicode code points of the keys. This method uses a stable sorting algorithm (preserving the relative order of key-value pairs with equal keys).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let paramsObject = new url.URLParams("c=3&a=9&b=4&d=2"); // Create a test URLParams object
paramsObject.sort(); // Sort the key/value pairs
console.info(paramsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2
```


### keys<sup>9+</sup>

keys(): IterableIterator&lt;string&gt;

Returns an iterator containing the name of all key-value pairs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;string&gt; | Returns an iterator containing the names of all key-value pairs. |

**Example**

```ts
// Construct a URLParams object.
let paramsObject = new url.URLParams("key1=value1&key2=value2");
// Obtain the iterator of all key names.
let keys = paramsObject.keys();
// Traverse and output the key names.
for (let key of keys) {
  console.info(key);
}
// key1
// key2
```


### values<sup>9+</sup>

values(): IterableIterator&lt;string&gt;

Returns an iterator containing the value of all key-value pairs.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;string&gt; | Returns an iterator containing the values of all key-value pairs. |

**Example**

```ts
// Construct a URLParams object.
let paramsObject = new url.URLParams("key1=value1&key2=value2");
// Obtain the iterator of all values.
let values = paramsObject.values();
// Traverse and output the values.
for (let value of values) {
  console.info(value);
}
// value1
// value2
```


### [Symbol.iterator]<sup>9+</sup>

[Symbol.iterator]\(): IterableIterator&lt;[string, string]&gt;

Returns an iterator, where each item of the iterator is an Array. The first item of the Array is name, and the second item of the Array is value.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[string, string]&gt; | Returns an iterator, where each item is a [string, string] array containing name and value. |

**Example**

```ts
// Construct a URLParams object.
const paramsObject = new url.URLParams('fod=bay&edg=bap');
// Obtain the Symbol.iterator iterator.
let iter = paramsObject[Symbol.iterator]();
// Traverse the key-value pairs.
for (let pair of iter) {
  console.info(pair[0] + ', ' + pair[1]);
}
// fod, bay
// edg, bap
```


### toString<sup>9+</sup>

toString(): string

Obtains search parameters that are serialized as a string and, if necessary, percent-encodes the characters in the string.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| string | String of serialized search parameters, which is percent-encoded if necessary.|

**Example**

```ts
// Parse the URL string.
let urlObject = url.URL.parseURL('https://developer.exampleUrl/?fod=1&bard=2');
// Construct a URLParams object.
let params = new url.URLParams(urlObject.search.slice(1));
// Append a parameter.
params.append('fod', '3');
// Serialize the parameters into a string.
console.info(params.toString()); // Output 'fod=1&bard=2&fod=3'
```

## URLUtil

URLUtil is a URL-related utility class that provides auxiliary capabilities for URL query parameter serialization. [URLParams.toString](#tostring9) follows the application/x-www-form-urlencoded specification and encodes spaces as '+'. In scenarios where spaces need to be encoded as %20 (such as re-parsing after URL parameter serialization or interfacing with other systems), you can use the serialization capability of URLUtil.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Utils.Lang

### toString

static toString(urlParams: URLParams): string

Serializes a URLParams object into a query string, where spaces are percent-encoded as %20 (instead of '+'). This interface does not modify the state of the input urlParams or the URL object it belongs to.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| urlParams | [URLParams](#urlparams9) | Yes | URLParams object to be serialized. It can be created through the constructor or obtained through the params property of a [URL](#url) object. |

**Return value**

| Type | Description |
| -------- | -------- |
| string | Returns the serialized query string, where spaces are percent-encoded as %20. When the URLParams object contains no key-value pairs, an empty string is returned. |

**Example**

```ts
// Serialize the URLParams object, encoding spaces as %20.
let params = new url.URLParams('detailAddress=a%20b');
let result = url.URLUtil.toString(params); // Output 'detailAddress=a%20b'
// Compare with URLParams.toString: follows the application/x-www-form-urlencoded specification, encoding spaces as '+'.
let result1 = params.toString(); // Output 'detailAddress=a+b'

// Perform percent encoding on special characters during serialization.
let params1 = new url.URLParams();
params1.append('k&y', 'v=l');
let result2 = url.URLUtil.toString(params1); // Output 'k%26y=v%3Dl'

// Obtain the URLParams object through the params property of the URL object and serialize it.
let urlObject = url.URL.parseURL('https://www.example.com/path?a=b c');
let result3 = url.URLUtil.toString(urlObject.params); // Output 'a=b%20c'
```

## URL

Used for parsing, constructing, normalizing, and encoding the corresponding URL string.

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| hash | string | No| No| String that contains a harsh mark (#) followed by the fragment identifier of a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| host | string | No| No| Host information in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| hostname | string | No| No| Hostname (without the port) in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| href | string | No| No| String that contains the whole URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| origin | string | Yes| No| Read-only string that contains the Unicode serialization of the origin of the represented URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| password | string | No| No| Password in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| pathname | string | No| No| Path in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| port | string | No | No | Get and set the port part of the URL. When port is the default port of the current protocol, port will be parsed as an empty string. **Atomic Service API**: Since API version 11, this interface supports use in atomic services. |
| protocol | string | No| No| Protocol in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| search | string | No| No| Serialized query string in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|
| searchParams<sup>(deprecated)</sup> | [URLSearchParams](#urlsearchparamsdeprecated) | Yes | No | Obtains the URLSearchParams object, used to access URL query parameters.<br>- **Note:** This attribute is supported since API version 7 and deprecated since API version 9. It is recommended to use params<sup>9+</sup> instead. |
| params<sup>9+</sup> | [URLParams](#urlparams9) | Yes | No | Obtains the URLParams object, used to access URL query parameters. **Atomic Service API**: Since API version 11, this interface supports use in atomic services. |
| username | string | No| No| Username in a URL. **Atomic service API**: This API can be used in atomic services since API version 11.|

> **NOTE**
>
> When parsing a URL string, if the port in the input is the default port of the current protocol, the port is parsed as an empty string. The default ports are:
>
> - http:  80
> - https:  443
> - ftp:  21
> - gopher:  70
> - ws:  80
> - wss:  443

**Example**

```ts
let parsedUrl = url.URL.parseURL('http://username:password@host:8080/directory/file?foo=1&bar=2#fragment');
console.info("hash " + parsedUrl.hash); // hash #fragment
console.info("host " + parsedUrl.host); // host host:8080
console.info("hostname " + parsedUrl.hostname); // hostname host
console.info("href " + parsedUrl.href); // href http://username:password@host:8080/directory/file?foo=1&bar=2#fragment
console.info("origin " + parsedUrl.origin); // origin http://host:8080
console.info("password " + parsedUrl.password); // password password
console.info("pathname " + parsedUrl.pathname); // pathname /directory/file
console.info("port " + parsedUrl.port); // port 8080
console.info("protocol " + parsedUrl.protocol); // protocol http:
console.info("search " + parsedUrl.search); // search ?foo=1&bar=2
console.info("username " + parsedUrl.username); // username username
// The return value of parsedUrl.params is a URLParams object.
console.info("params: foo " + parsedUrl.params.get("foo")); // params: foo 1

let urlObj = url.URL.parseURL('http://testhost:80/directory/file?foo=1');
console.info("port " + urlObj.port); // port 
console.info("toString " + urlObj.toString()); // toString http://testhost/directory/file?foo=1
```

### constructor<sup>(deprecated)</sup>

constructor(url: string, base?: string | URL)

Constructor of URL. It has the same functionality as the [parseURL](#parseurl9) method, but parseURL is a static factory method. You are advised to use parseURL to create a URL object.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [parseURL<sup>9+</sup>](#parseurl9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| url | string | Yes | A string representing an absolute URL or a relative URL. It must be in a valid URL format. <br>If url is a relative URL, base must be specified to resolve the final URL. <br>If url is an absolute URL, the given base will not take effect. |
| base | string \| URL |  No  | Input string or object. The default value is undefined.<br>- string: a string representing the base URL. When url is a relative URL, it must be in a valid URL format.<br>- URL: a parsed URL object, used as the base address for resolving a relative URL.|

**Example**

```ts
let baseUrl = 'https://username:password@host:8080';
let rootPathUrl = new url.URL("/", baseUrl); // Output 'https://username:password@host:8080/';
let absoluteUrl = new url.URL(baseUrl); // Output 'https://username:password@host:8080/';
new url.URL('path/path1', absoluteUrl); // Output 'https://username:password@host:8080/path/path1';
let relativePathUrl = new url.URL('/path/path1', absoluteUrl);  // Output 'https://username:password@host:8080/path/path1'; 
new url.URL('/path/path1', relativePathUrl); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', rootPathUrl); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', "https://www.exampleUrl/fr-FR/toot"); // Output https://www.exampleUrl/path/path1
new url.URL('/path/path1', ''); // Raises a TypeError exception as '' is not a valid URL
new url.URL('/path/path1'); // Raises a TypeError exception as '/path/path1' is not a valid URL
new url.URL('https://www.example.com', ); // Output https://www.example.com/
new url.URL('https://www.example.com', absoluteUrl); // Output https://www.example.com/
```

### constructor<sup>9+</sup>

constructor()

Parameterless constructor of URL. It is not recommended to call it directly. Use the [parseURL](#parseurl9) method to create a URL object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

### parseURL<sup>9+</sup>

static parseURL(url: string, base?: string | URL): URL

Parses a URL string and returns the parsed URL object. The object contains URL components such as the protocol, host, port, path, and query parameters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| url | string | Yes | A string representing an absolute URL or a relative URL. <br>If url is a relative URL, base must be specified to resolve the final URL. <br>If url is an absolute URL, the given base will not take effect. |
| base | string \| URL | No | Input parameter string or object. The default value is undefined.<br>- string: A string. When the first parameter is a relative URL, this parameter must conform to the URL standard.<br>- URL: A URL object.<br>- Used when url is a relative URL. This parameter does not take effect when url is an absolute URL. |

**Return value**

| Type| Description                                             |
| ---- | ------------------------------------------------- |
| [URL](#url)  | Returns the parsed URL object, containing the components of the URL (such as protocol, host, and path attributes). |

> **NOTE**
>
> If **url** is a relative URL, the URL parsed by calling this API is not merely a concatenation of **url** and **base**. When **url** is a relative path, it is parsed relative to the current directory of the passed **base**, taking into account all path segments before the last slash in the path of **base**, but excluding the following part (see example url1). When **url** points to a root directory, it is parsed relative to the origin of **base** (see example url2).

**Error codes**

For details about the following error codes, see [Language Basics Library Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid url string. |

**Example**

```ts
let baseUrl = 'https://username:password@host:8080/test/test1/test3';
let urlObject = url.URL.parseURL(baseUrl);
let result = urlObject.toString(); // Output 'https://username:password@host:8080/test/test1/test3'
// If url is a relative path, the path in the base parameter is test/test1, and the path of the parsed URL is /test/path2/path3.
let relativePathUrl = url.URL.parseURL('path2/path3', 'https://www.example.com/test/test1'); // Output 'https://www.example.com/test/path2/path3'
// If url is a root directory, the path in the base parameter is /test/test1/test3, and the path of the parsed URL is /path1/path2.
let rootPathUrl = url.URL.parseURL('/path1/path2', urlObject); // Output 'https://username:password@host:8080/path1/path2'
url.URL.parseURL('/path/path1', "https://www.exampleUrl/fr-FR/toot"); // Output 'https://www.exampleUrl/path/path1'
url.URL.parseURL('/path/path1', ''); // Raises a TypeError exception as '' is not a valid URL
url.URL.parseURL('/path/path1'); // Raises a TypeError exception as '/path/path1' is not a valid URL
url.URL.parseURL('https://www.example.com', ); // Output 'https://www.example.com/'
url.URL.parseURL('https://www.example.com', urlObject); // Output 'https://www.example.com/'
```

### toString

toString(): string

Converts the parsed URL to a string. The return value is the same as the value of the href attribute of the URL.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| string | Serialized string of the parsed URL. |

**Example**

```ts
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = urlObject.toString(); // Output 'https://username:password@host:8080/directory/file?query=pppppp#qwer=da'
```

### toJSON

toJSON(): string

Converts the parsed URL into a JSON string.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| string | JSON serialized string of the URL object. |

**Example**
```ts
// Parse the URL string.
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
// Convert the URL to a string.
let result = urlObject.toJSON();
```

## URLSearchParams<sup>(deprecated)</sup>

The URLSearchParams interface defines some utility methods for processing URL query strings.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams](#urlparams9) instead.

### constructor<sup>(deprecated)</sup>

constructor(init?: string[][] | Record&lt;string, string&gt; | string | URLSearchParams)

A constructor used to create a **URLSearchParams** instance.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.constructor<sup>9+</sup>](#constructor9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| init | string[][] \| Record&lt;string, string&gt; \| string \| URLSearchParams | No | Input parameter object.<br>- string[][]: a two-dimensional string array, where each inner array contains two elements, namely the key name and key value.<br>- Record&lt;string, string&gt;: object list.<br>- string: a string that must follow the URL query parameter format, such as 'key=value&key2=value2'.<br>- URLSearchParams: object.<br>- Default Value: undefined. |

**Example**

```ts
let objectParams = new url.URLSearchParams([ ['user1', 'abc1'], ['query2', 'first2'], ['query3', 'second3'] ]);
let objectParams1 = new url.URLSearchParams({"fod" : '1' , "bard" : '2'});
let objectParams2 = new url.URLSearchParams('?fod=1&bard=2');
let urlObject = new url.URL('https://developer.mozilla.org/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search);
```

### append<sup>(deprecated)</sup>

append(name: string, value: string): void

Appends a key-value pair into the query string.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.append<sup>9+</sup>](#append9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key of the key-value pair to append.|
| value | string | Yes| Value of the key-value pair to append.|

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.append('fod', '3');
```

### delete<sup>(deprecated)</sup>

delete(name: string): void

Deletes key-value pairs of the specified key.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.delete<sup>9+</sup>](#delete9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key of the key-value pairs to delete.|

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.delete('fod');
```

### getAll<sup>(deprecated)</sup>

getAll(name: string): string[]

Obtains the set of all values corresponding to the specified name.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.getAll<sup>9+</sup>](#getall9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Target key.|

**Return value**

| Type| Description|
| -------- | -------- |
| string[] | Returns the collection of values corresponding to all keys with the specified name. |

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search.slice(1));
params.append('fod', '3'); // Add a second value for the fod parameter.
console.info(params.getAll('fod').toString()) // Output ["1","3"].
```

### entries<sup>(deprecated)</sup>

entries(): IterableIterator<[string, string]>

Returns an iterator, each item of which is an Array. The first item of the Array is name, and the second item of the Array is value.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.entries<sup>9+</sup>](#entries9) instead.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[string, string]&gt; | Returns an iterator, where each item is a [string, string] array containing name and value. |

**Example**

```ts
let searchParamsObject = new url.URLSearchParams("keyName1=valueName1&keyName2=valueName2");
let iter = searchParamsObject.entries();
for (let pair of iter) {
  console.info(pair[0]+ ', '+ pair[1]);
}
// keyName1, valueName1
// keyName2, valueName2
```


### forEach<sup>(deprecated)</sup>

forEach(callbackFn: (value: string, key: string, searchParams: URLSearchParams) => void, thisArg?: Object): void

Traverses the key-value pairs in the **URLSearchParams** instance by using a callback.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.forEach<sup>9+</sup>](#foreach9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| callbackFn | function | Yes| Callback invoked to traverse the key-value pairs in the **URLSearchParams** instance.|
| thisArg | Object | No| Value of **this** to use when **callbackFn** is invoked. The default value is this object.|

**Table 1** callbackFn parameter description

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string | Yes| Value that is currently traversed.|
| key | string | Yes| Key that is currently traversed.|
| searchParams | [URLSearchParams](#urlsearchparamsdeprecated) | Yes| Instance that invokes the **forEach** method.|

**Example**

```ts
const myURLObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
myURLObject.searchParams.forEach((value, name, searchParams) => {
    console.info(name, value, myURLObject.searchParams === searchParams);
});
```


### get<sup>(deprecated)</sup>

get(name: string): string | null

Obtains the value of the first key-value pair based on the specified key.

> **NOTE**
>
> If a nonexistent key-value pair name is searched for, the return value is undefined. This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.get<sup>9+</sup>](#get9) instead.


**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key specified to obtain the value.|

**Return value**

| Type| Description|
| -------- | -------- |
| string \| null | The first value is returned. If no value is found, **null** is returned.|

**Example**

```ts
let paramsObject = new url.URLSearchParams('name=Jonathan&age=18');
let name = paramsObject.get("name"); // is the string "Jonathan"
let age = paramsObject.get("age"); // is the string '18'
let getObj = paramsObject.get("abc"); // undefined
```


### has<sup>(deprecated)</sup>

has(name: string): boolean

Checks whether a key has a value.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.has<sup>9+</sup>](#has9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key specified to search for its value.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Whether the corresponding key value exists. Returns true if it exists, and false otherwise. |

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.has('bard') === true;
```


### set<sup>(deprecated)</sup>

set(name: string, value: string): void

Sets the value for a key. If key-value pairs matching the specified key exist, the value of the first key-value pair will be set to the specified value and other key-value pairs will be deleted. Otherwise, the key-value pair will be appended to the query string.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.set<sup>9+</sup>](#set9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Key of the value to set.|
| value | string | Yes| Value to set.|

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let paramsObject = new url.URLSearchParams(urlObject.search.slice(1));
paramsObject.set('baz', '3'); // Add a third parameter.
```


### sort<sup>(deprecated)</sup>

sort(): void

Sorts all key-value pairs contained in this object. The sort order is based on the Unicode code points of the keys. This method uses a stable sorting algorithm (that is, the relative order between key-value pairs with equal keys will be preserved).

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.sort<sup>9+</sup>](#sort9) instead.

**System capability**: SystemCapability.Utils.Lang

**Example**

```ts
let searchParamsObject = new url.URLSearchParams("c=3&a=9&b=4&d=2"); // Create a test URLSearchParams object
searchParamsObject.sort(); // Sort the key/value pairs
console.info(searchParamsObject.toString()); // Display the sorted query string // Output a=9&b=4&c=3&d=2
```


### keys<sup>(deprecated)</sup>

keys(): IterableIterator&lt;string&gt;

Returns an iterator of the names of all key-value pairs.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.keys<sup>9+</sup>](#keys9) instead.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;string&gt; | Returns an iterator of the names of all key-value pairs. |

**Example**

```ts
let searchParamsObject = new url.URLSearchParams("key1=value1&key2=value2");
let keys = searchParamsObject.keys();
for (let key of keys) {
  console.info(key);
}
// key1
// key2
```


### values<sup>(deprecated)</sup>

values(): IterableIterator&lt;string&gt;

Returns an iterator of the values of all key-value pairs.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.values<sup>9+</sup>](#values9) instead.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;string&gt; | Returns an iterator of the values of all key-value pairs. |

**Example**

```ts
let searchParams = new url.URLSearchParams("key1=value1&key2=value2");
let values = searchParams.values();
for (let value of values) {
  console.info(value);
}
// value1
// value2
```


### [Symbol.iterator]<sup>(deprecated)</sup>

[Symbol.iterator]\(): IterableIterator&lt;[string, string]&gt;

Returns an iterator, each item of which is an Array. The first item of the Array is name, and the second item of the Array is value.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.[Symbol.iterator]<sup>9+</sup>](#symboliterator9) instead.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| IterableIterator&lt;[string, string]&gt; | Returns an iterator, where each item is a [string, string] array containing name and value. |

**Example**

```ts
const paramsObject = new url.URLSearchParams('fod=bay&edg=bap');
let pairs = paramsObject[Symbol.iterator]();
for (let pair of pairs) {
  console.info(pair[0] + ', ' + pair[1]);
}
// fod, bay
// edg, bap
```

### toString<sup>(deprecated)</sup>

toString(): string

Obtains search parameters that are serialized as a string and, if necessary, percent-encodes the characters in the string.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [URLParams.toString<sup>9+</sup>](#tostring9) instead.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| string | String of serialized search parameters, which is percent-encoded if necessary.|

**Example**

```ts
let urlObject = new url.URL('https://developer.exampleUrl/?fod=1&bard=2');
let params = new url.URLSearchParams(urlObject.search.slice(1));
params.append('fod', '3');
console.info(params.toString()); // Output 'fod=1&bard=2&fod=3'
```
<!--no_check-->