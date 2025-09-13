# @ohos.uri (URI String Parsing)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @yuanyao14-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

The uri module provides APIs for parsing URI strings that comply with the RFC3986 standard. This standard defines how to encode and parse network resource identifiers. The module does not support parsing of URIs in non-standard scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { uri } from '@kit.ArkTS';
```

## URI

Constructs a URI object, and provides methods for determining whether this URI is the same as another URI object and for normalizing URI paths.

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| scheme | string | No| No| Scheme in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| userInfo | string | No| No| User information in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| host | string | Yes| No| Host name (without the port number) in the URI. If this part does not exist, a null object is returned.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| port | string | Yes| No| Port number in the URI.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| path | string | No| No| Path in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| query | string | No| No| Query parameters in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| fragment | string | No| No| Fragments in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| authority | string | No| No| Authority in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| ssp | string | No| No| Scheme-specific part in the URI. It contains protocol-or scheme-specific information.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| encodedUserInfo<sup>12+</sup>  | string | No  | No  | Encoded user information in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| encodedPath<sup>12+</sup>      | string | No  | No  | Encoded path in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| encodedQuery<sup>12+</sup>     | string | No  | No  | Encoded query parameters in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| encodedFragment<sup>12+</sup>  | string | No  | No  | Encoded fragments in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| encodedAuthority<sup>12+</sup> | string | No  | No  | Encoded authority in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| encodedSSP<sup>12+</sup>       | string | No  | No  | Encoded scheme-specific part in the URI.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |

### Naming Rules

Naming format:

A standard URI mainly consists of three parts, as follows:
[scheme:]scheme-specific-part[#fragment]

Breaking down the URI format further, it can be divided into:
[scheme:][//authority][path][?query][#fragment]

Further refining the URI format, it can be detailed as:
[scheme:][//[user-info@]host[:port]][path][?query][#fragment]

- scheme: scheme name, which is separated from scheme-specific-part by a colon (:). The URI that contains the scheme component is an absolute URI, and the URI that does not contain the scheme component is a relative URI. Set this part as required. Example values: **http**, **https**, **ftp**, and **datashare**.
- scheme-specific-part: specific part of the URI decoding scheme. It is located between [scheme:] and [#fragment] and consists of [//][authority][path][?query]. The URI that starts with a slash (/) is a hierarchical URI, and the URI that does not start with a slash (/) is an opaque URI. Set this part as required.
    - authority: decoding authority component of the URI. The value consists of [userinfo@]host[:port]. Set this part as required.
        - userinfo: user information, which is separated from host by an at sign (@). Set this part as required.
        - host: host name of the server. This parameter is mandatory when authority exists.
        - port: port number of the server. The default value is **-1**. Set this part as required.
    - path: path information, which is located between host and query and separated by a slash (/). Set this part as required.
    - query: query component, which is located between path and fragment, indicated by the first question mark (?) character, and is in the format of key-value pairs. Multiple key-value pairs are separated by the at sign (&), and the key and value in a pair is separated by the equal sign (=). Set this part as required.
- fragment: fragment component, which is separated from scheme-specific-part by the pound key (#). Set this part as required.

**Example URIs**

```ts
const uriObj1 = new uri.URI("ftp://ftp.aaa.bbb.ccc/dddd/eee.txt");
console.info(uriObj1.host); // ftp.aaa.bbb.ccc
console.info(uriObj1.fragment); // null
console.info(uriObj1.path); // /dddd/eee.txt
console.info(uriObj1.scheme); // ftp
console.info(uriObj1.userInfo); // null
console.info(uriObj1.port); // -1
console.info(uriObj1.query); // null

const uriObj2 = new uri.URI("gopher://spinaltap.micro.umn.edu/00/Weather/California/Los%20Angeles#fragment");
console.info(uriObj2.host); // spinaltap.micro.umn.edu
console.info(uriObj2.fragment); // fragment
console.info(uriObj2.path); // /00/Weather/California/Los Angeles
console.info(uriObj2.scheme); // gopher
console.info(uriObj2.userInfo); // null
console.info(uriObj2.port); //-1
console.info(uriObj2.query); // null

const uriObj3 = new uri.URI("datashare:///com.samples.datasharetest.DataShare/DB00/TBL00");
console.info(uriObj3.host); // null
console.info(uriObj3.fragment); // null
console.info(uriObj3.path); // /com.samples.datasharetest.DataShare/DB00/TBL00
console.info(uriObj3.scheme); // datashare
console.info(uriObj3.userInfo); // null
console.info(uriObj3.port); // -1
console.info(uriObj3.query); // null

const uriObj4 = new uri.URI("https://username:password@host:8080/directory/file?foo=1&bar=2#fragment");
console.info(uriObj4.host); // host
console.info(uriObj4.fragment); // fragment
console.info(uriObj4.path); // /directory/file
console.info(uriObj4.scheme); // https
console.info(uriObj4.userInfo); // username:password
console.info(uriObj4.port); // 8080
console.info(uriObj4.query); // foo=1&bar=2

const uriObj5 = new uri.URI("dataability:///com.example.DataAbility");
console.info(uriObj5.host); // null
console.info(uriObj5.fragment); // null
console.info(uriObj5.path); // /com.example.DataAbility:
console.info(uriObj5.scheme); // dataability
console.info(uriObj5.userInfo); // null
console.info(uriObj5.port); // -1
console.info(uriObj5.query); // null

const uriObj6 = new uri.URI("https://username:my+name@host:8080/directory/my+file?foo=1&bar=2#fragment");
console.info(uriObj6.encodedUserInfo); // username:my+name
console.info(uriObj6.encodedPath); // /directory/my+file
console.info(uriObj6.encodedQuery); // foo=1&bar=2
console.info(uriObj6.encodedFragment); // fragment
console.info(uriObj6.encodedAuthority); // username:my+name@host:8080
console.info(uriObj6.encodedSSP); // //username:my+name@host:8080/directory/my+file?foo=1&bar=2

let uriObj7 = new uri.URI("www.abc.com:8080/directory/file?ab=pppppp#qwer=da");
console.info(uriObj7.scheme); // www.abc.com
console.info(uriObj7.host); // null
console.info(uriObj7.port); // -1
console.info(uriObj7.path); // null
console.info(uriObj7.query); // null
console.info(uriObj7.authority); // null
console.info(uriObj7.fragment); // qwer=da
console.info(uriObj7.ssp); // 8080/directory/file?ab=pppppp
console.info("result:", uriObj7.checkIsAbsolute()); // result: true
```

### constructor

constructor(uri: string)

A constructor used to create a URI.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes| Input object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 10200002 | Invalid uri string. |

**Example**

```ts
let mm = 'https://username:password@host:8080/directory/file?foo=1&bar=2#fragment';
new uri.URI(mm);
```
```ts
new uri.URI('https://username:password@host:8080');
```


### toString

toString(): string

Converts this URI into an encoded string.

**System capability**: SystemCapability.Utils.Lang

**Atomic service API**: This API can be used in atomic services since API version 11.

**Return value**

| Type| Description|
| -------- | -------- |
| string | URI in a serialized string.|

**Example**

```ts
const result = new uri.URI('https://username:password@host:8080/directory/file?ab=pppppp#qwer da');
let result1 = result.toString(); // https://username:password@host:8080/directory/file?ab=pppppp#qwer%20da
```

### equalsTo<sup>9+</sup>

equalsTo(other: URI): boolean

Checks whether this URI is the same as another URI object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| other | [URI](#uri) | Yes| URI object to compare.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the two URIs are the same; otherwise, **false** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = uriInstance.equalsTo(uriInstance1); // true
```

### checkIsAbsolute

checkIsAbsolute(): boolean

Checks whether the URI is an absolute URI, that is, whether the URI contains the scheme component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | **true**: The URI is an absolute URI.<br>**false**: The URI is not an absolute URI.|

**Example**

```ts
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080?query=pppppp');
console.info(`${uriInstance.checkIsAbsolute()}`); // true
const uriInstance1 = new uri.URI('xxx.com/suppliers.htm');
console.info(`${uriInstance1.checkIsAbsolute()}`); // false
```


### normalize

normalize(): URI

Normalizes the path of this URI.

> **NOTE**
>
> If the URI is opaque or its path is already in normalized, the URI is directly returned. Otherwise, a new URI is created. The new URI is similar to the current URI. The only difference relies on its path, which is determined by normalizing the path of the current URI according to the following guidelines:
>
>  1. All . (dot) segments are removed.
>
>  2. For any .. (double-dot) segment that is immediately preceded by a segment that is not .., both segments are removed. This process is iterated until no further removals can be made.
>
>If normalization results in a path starting with a .. (double-dot) segment, it indicates that there were insufficient preceding non-.. segments for removal. As a result, the path will start with a .. segment.


**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description|
| -------- | -------- |
| [URI](#uri) | URI with the normalized path.|

**Example**

```ts
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080/path/path1/../path2/./path3?query=pppppp');
console.info(uriInstance.path); // /path/path1/../path2/./path3
// Following path normalization, all . (dot) segments are removed. If a .. (double-dot) segment is immediately preceded by a segment that is not .., both segments are removed.
let uriInstance1 = uriInstance.normalize();
console.info(uriInstance1.path); // /path/path2/path3
let uri1 = new uri.URI('http://www.test.com/../../patch/path1/../path2/path3/./path4/../');
console.info(uri1.path); // /../../patch/path1/../path2/path3/./path4/../
// If normalization result in a path starting with a .. (double-dot) segment, it indicates that there were insufficient preceding non-.. segments for removal. As a result, the path will start with a .. segment.
let uri2 = uri1.normalize();
console.info(uri2.path); // /../../patch/path2/path3
```

### checkRelative<sup>12+</sup>

checkRelative(): boolean

Checks whether this URI is a relative URI. A relative URI does not contain the scheme component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                      |
| ------- | ------------------------------------------ |
| boolean | **true**: The URI is a relative URI.<br>**false**: The URI is not a relative URI.|

**Example**

```ts
const uriInstance = new uri.URI("https://username:password@www.qwer.com:8080?query=p");
console.info(`${uriInstance.checkRelative()}`); // false
const uriInstance1 = new uri.URI("/images/pic.jpg");
console.info(`${uriInstance1.checkRelative()}`); // true
```

### checkOpaque<sup>12+</sup>

checkOpaque(): boolean

Checks whether this URI is an opaque URI. The URI that does not start with a slash (/) is an opaque URI.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                          |
| ------- | ---------------------------------------------- |
| boolean | **true**: The URI is an opaque URI.<br>**false**: The URI is not an opaque URI.|

**Example**

```ts
const uriInstance = new uri.URI("http://www.test.com/images/pic.jpg");
console.info(`${uriInstance.checkOpaque()}`); // false
const uriInstance1 = new uri.URI("mailto:user@example.com");
console.info(`${uriInstance1.checkOpaque()}`); // true
```

### checkHierarchical<sup>12+</sup>

checkHierarchical(): boolean

Checks whether this URI is a hierarchical URI. The URI that starts with a slash (/) in scheme-specific-part is a hierarchical URI. Relative URIs are also hierarchical.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                        |
| ------- | -------------------------------------------- |
| boolean | **true**: The URI is a hierarchical URI.<br>**false**: The URI is not a hierarchical URI.|

**Example**

```ts
const uriInstance = new uri.URI("http://www.test.com/images/pic.jpg");
console.info(`${uriInstance.checkHierarchical()}`); // true
const uriInstance1 = new uri.URI("mailto:user@example.com");
console.info(`${uriInstance1.checkHierarchical()}`); // false
```

### getQueryValue<sup>12+</sup>

getQueryValue(key:string): string

Obtains the first value of a given key from the query component of this URI. If the query component contains encoded content, this API decodes the key before obtaining the value.

The query component follows the question mark (?) and consists of key-value pairs, separated by the at sign (&). In each key-value pair, the equal sign (=) is used to connect the key and value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| key    | string | Yes  | Key of the URI query parameter.|

**Return value**

| Type  | Description                         |
| ------ | ----------------------------- |
| string | First value obtained. If no value is found, a null object is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("https://www.com?param1=value1&param2=value2");
console.info(uriInstance.getQueryValue("param1")); // value1
let uriInstance1 = new uri.URI('https://www.zyy.ss?sa%3D=po%7E');
console.info(uriInstance1.getQueryValue('sa=')) // po~
console.info(uriInstance1.getQueryValue('abc')) // null
```

### addQueryValue<sup>12+</sup>

addQueryValue(key:string, value:string): URI

Adds a query parameter to this URI to create a new URI, while keeping the existing URI unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                    |
| ------ | ------ | ---- | ------------------------ |
| key    | string | Yes  | Key of the query parameter.|
| value  | string | Yes  | Value of the query parameter.  |

**Return value**

| Type| Description                            |
| ---- | -------------------------------- |
| [URI](#uri)  | URI object with the query parameter.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("https://www.test.com");
const newRoute = uriInstance.addQueryValue("param1", "hello world");
console.info(newRoute.toString()); // https://www.test.com?param1=hello%20world
```

### addSegment<sup>12+</sup>

addSegment(pathSegment:string): URI

Encodes a given field, appends it to the path component of this URI to create a new URI, and returns the new URI, while keeping the existing URI unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name     | Type  | Mandatory| Description              |
| ----------- | ------ | ---- | ------------------ |
| pathSegment | string | Yes  | Field to be appended to the path component.|

**Return value**

| Type| Description                            |
| ---- | -------------------------------- |
| [URI](#uri)  | URI object with the appended field.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("http://www.test.com");
const newRoute = uriInstance.addSegment("my image.jpg");
console.info(newRoute.toString()); // http://www.test.com/my%20image.jpg
```

### addEncodedSegment<sup>12+</sup>

addEncodedSegment(pathSegment:string): URI

Appends an encoded field to the path component of this URI to create a new URI and returns the new URI, while keeping the existing URI unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name     | Type  | Mandatory| Description              |
| ----------- | ------ | ---- | ------------------ |
| pathSegment | string | Yes  | Encoded field to be appended to the path component.|

**Return value**

| Type| Description                            |
| ---- | -------------------------------- |
| [URI](#uri)  | URI object with the appended field.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("http://www.test.com");
const newRoute = uriInstance.addEncodedSegment("my%20image.jpg");
console.info(newRoute.toString()); // http://www.test.com/my%20image.jpg
```

### getQueryNames<sup>12+</sup>

getQueryNames(): string[]

Obtains all non-repeated keys in the query component of this URI. The query component follows the question mark (?) and consists of key-value pairs, separated by the at sign (&). In each key-value pair, the equal sign (=) is used to connect the key and value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type       | Description                               |
| ----------- | ----------------------------------- |
| string[] | Non-repeated keys in the query component.|

**Example**

```ts
const uriInstance = new uri.URI("https://www.test.com?param1=value1&param2=value2");
const paramNames = uriInstance.getQueryNames();
console.info(paramNames.toString()); // param1,param2
```

### getQueryValues<sup>12+</sup>

getQueryValues(key:string): string[]

Obtains all the values of a given key from the query component of this URI. If the query component is encoded, this API decodes the keys before obtaining the values.

The query component follows the question mark (?) and consists of key-value pairs, separated by the at sign (&). In each key-value pair, the equal sign (=) is used to connect the key and value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type  | Mandatory| Description                   |
| ------ | ------ | ---- | ----------------------- |
| key    | string | Yes  | Key of the URI query parameter.|

**Return value**

| Type    | Description                               |
| -------- | ----------------------------------- |
| string[] | Array of values obtained. If no value is found, an empty string array [] is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("https://www.test.com/search?query=name&query=my");
console.info(uriInstance.getQueryValues("query").toString()); // name,my
console.info(JSON.stringify(uriInstance.getQueryValues("abc"))); // []
```

### getBooleanQueryValue<sup>12+</sup>

getBooleanQueryValue(key:string,defaultValue:boolean): boolean

Searches for the first value associated with the given key in the query string and converts it to a boolean value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name      | Type   | Mandatory| Description                                 |
| ------------ | ------- | ---- | ------------------------------------- |
| key          | string  | Yes  | Name of the query parameter.              |
| defaultValue | boolean | Yes  | Value returned when the query parameter does not contain the specified key.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | If the specified query parameter does not exist, the default value is returned. If the first value of the query parameter is **false** or **0**, **false** is returned. Otherwise, **true** is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = new uri.URI("https://www.test.com/search?active=true");
console.info(`${uriInstance.getBooleanQueryValue("active", false)}`); // true
const uriInstance1 = new uri.URI("https://www.test.com/search");
console.info(`${uriInstance1.getBooleanQueryValue("active", false)}`); // false
const uriInstance2 = new uri.URI("https://www.test.com/search?active=aa&active=false");
console.info(`${uriInstance2.getBooleanQueryValue("active", false)}`); // true
const uriInstance3 = new uri.URI("https://www.test.com/search?active=0");
console.info(`${uriInstance3.getBooleanQueryValue("active", true)}`); // false
const uriInstance4 = new uri.URI("https://www.test.com/search");
console.info(`${uriInstance4.getBooleanQueryValue("active", true)}`); // true
```

### clearQuery<sup>12+</sup>

clearQuery(): URI

Clears the query component of this URI to create a new URI, while keeping the existing URI object unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description                                 |
| ---- | ------------------------------------- |
| [URI](#uri)  | URI object whose query component has been cleared.|

**Example**

```ts
const uriInstance = new uri.URI("https://www.test.com?param1=value1");
console.info(uriInstance.clearQuery().toString()); // https://www.test.com
```

### getLastSegment<sup>12+</sup>

getLastSegment(): string

Obtains the last segment of this URI. A path includes multiple segments, separated by slashes (/). The part that ends with a slash is not a segment.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description                         |
| ---- | ----------------------------- |
| string  | Last segment of the URI.|

**Example**

```ts
const uriInstance = new uri.URI("content://com.test.provider/files/image.jpg");
console.info(uriInstance.getLastSegment()); // image.jpg
```

### getSegment<sup>12+</sup>

getSegment(): string[]

Obtains all segments of this URI.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type    | Description                       |
| -------- | --------------------------- |
| string[] | All segments of this URI.|

**Example**

```ts
const uriInstance = new uri.URI("http://www.test.com/path/to/image.jpg");
console.info(uriInstance.getSegment().toString()); // path,to,image.jpg
```

### createFromParts<sup>12+</sup>

createFromParts(scheme: string, ssp: string, fragment: string): URI

Creates a URI based on the provided scheme, scheme-specific-part, and fragment components.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type  | Mandatory| Description                           |
| -------- | ------ | ---- | ------------------------------- |
| scheme   | string | Yes  | Scheme of the URI. This parameter must comply with the URI standard.|
| ssp      | string | Yes  | Scheme-specific-part of the URI.|
| fragment | string | Yes  | Fragment component of the URI, that is, the content following the number sign (#).|

**Return value**

| Type| Description                                             |
| ---- | ------------------------------------------------- |
| [URI](#uri)  | URI object obtained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| -------- | -------- |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Example**

```ts
const uriInstance = uri.URI.createFromParts("mailto", "no body", "top");
console.info(uriInstance.toString()); // mailto:no%20body#top
```

### equals<sup>(deprecated)</sup>

equals(other: URI): boolean

Checks whether this URI is the same as another URI object.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use [equalsTo<sup>9+</sup>](#equalsto9) instead.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| other | [URI](#uri) | Yes| URI object to compare.|

**Return value**

| Type| Description|
| -------- | -------- |
| boolean | Check result. The value **true** is returned if the two URIs are the same; otherwise, **false** is returned.|

**Example**

```ts
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
uriInstance.equals(uriInstance1); // true
```
