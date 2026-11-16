# @ohos.uri (URI String Parsing)
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @wang_zhaoyong; @lijin1039-->
<!--Designer: @Malzahar; @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=e8fa04a9bb7e2314faecbcf7e8c1aa9c09ae033c translatedAt=2026-11-16T05:55:58.622Z pushedAt=2026-11-16T06:31:14.279Z nl=1 -->

This module provides URI string parsing capabilities, supporting the extraction and setting of URI components (scheme, host, port, path, query parameters, fragment, and so on), as well as URI encoding/decoding, comparison, path normalization, and query parameter operations.

It is applicable to scenarios such as network request URL processing, deep link parsing, and data sharing URI processing.

URI complies with the RFC3986 specification and does not support parsing of non-standard scenarios.

> **NOTE**
>
> The initial APIs of this module are supported since API version 8. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { uri } from '@kit.ArkTS';
```

## URI

Constructs a URI object and provides methods for URI comparison, path normalization, query parameter operations, path segment appending, and URI type determination.

### Properties

**System capability**: SystemCapability.Utils.Lang

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| scheme | string | No | No | Obtains and sets the scheme part of the URI. If this part does not exist, a null object is returned. The scheme name starts with a letter and can contain only letters, digits, plus sign (+), hyphen (-), and period (.). <br/>Before API version 19, this property is read-only and cannot be written; modifying this property reports an error. <br/>**Atomic Service API:** Since API version 11, this API is supported in atomic services.|
| userInfo | string | No| No| User information in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| host | string | Yes| No| Host name (without the port number) in the URI. If this part does not exist, a null object is returned.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| port | string | Yes | No | Obtains the port part of the URI. If this part does not exist, -1 is returned. <br/>**Atomic Service API:** Since API version 11, this API is supported in atomic services. |
| path | string | No| No| Path in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| query | string | No| No| Query parameters in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| fragment | string | No| No| Fragments in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| authority | string | No | No | Obtains and sets the decoded authority component of this URI. If this part does not exist, a null object is returned. <br/>Before API version 19, this property is read-only and cannot be written; modifying this property reports an error. <br/>**Atomic Service API:** Since API version 11, this API is supported in atomic services. |
| ssp | string | No| No| Scheme-specific part in the URI. It contains protocol-or scheme-specific information.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| encodedUserInfo<sup>12+</sup>  | string | No  | No  | Encoded user information in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.  |
| encodedPath<sup>12+</sup>      | string | No  | No  | Encoded path in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| encodedQuery<sup>12+</sup>     | string | No  | No  | Encoded query parameters in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| encodedFragment<sup>12+</sup>  | string | No  | No  | Encoded fragments in the URI. If this part does not exist, a null object is returned.<br>This property was read-only and not writable prior to API version 19; attempting to modify it would throw an error.<br>**Atomic service API**: This API can be used in atomic services since API version 12.     |
| encodedAuthority<sup>12+</sup> | string | No   | No   | Obtains and sets the encoded authority component of the URI. If this part does not exist, a null object is returned. <br/>Before API version 19, this property is read-only and cannot be written; modifying this property reports an error. <br/>**Atomic Service API:** Since API version 12, this API is supported in atomic services.   |
| encodedSSP<sup>12+</sup>       | string | No   | No   | Obtains and sets the encoded scheme-specific part of the URI. If this part does not exist, a null object is returned. <br/>Before API version 19, this property is read-only and cannot be written; modifying this property reports an error. <br/>**Atomic Service API:** Since API version 12, this API is supported in atomic services.   |

### Naming Rules

Naming format:

A standard URI mainly consists of **[scheme:]scheme-specific-part[#fragment]**.

An elaborated URI consists of **[scheme:][//authority][path][?query][#fragment]**.

A further refined URI consists of **[scheme:][//[user-info@]host[:port]][path][?query][#fragment]**.

- scheme: scheme name, which is separated from scheme-specific-part by a colon (:). A URI that contains the scheme part is an absolute URI, and a URI that does not contain the scheme part is a relative URI. Set this part as required. For example, http, https, ftp, datashare, and so on.
- scheme-specific-part: decoded scheme-specific part of the URI, which is located between [scheme:] and [#fragment] and consists of [//][authority][path][?query]. If this part starts with a slash (/), the URI is a hierarchical URI; otherwise, it is an opaque URI. Set this part as required.
    - authority: decoded authority component of the URI. It consists of [userinfo@]host[:port]. Set this part as required.
        - userinfo: user information, which is separated from host by an at sign (@). Set this part as required.
        - host: host name of the server. This parameter is mandatory when authority exists.
        - port: port number of the server. The default value is **-1**. Set this part as required.
    - path: path information, which is located after authority or after host (when authority does not exist), starts with a slash (/), and precedes query. Set this part as required.
    - query: query part, which is located between path and fragment, in the key-value pair format starting with a question mark (?), with key-value pairs separated by an ampersand (&) and keys and values separated by an equals sign (=). Set this part as required.
- fragment: fragment component, which is separated from scheme-specific-part by the pound key (#). Set this part as required.

**Example URIs**

```ts
const uriObj1 = new uri.URI('ftp://ftp.aaa.bbb.ccc/dddd/eee.txt');
console.info(uriObj1.host); // ftp.aaa.bbb.ccc
console.info(uriObj1.fragment); // null
console.info(uriObj1.path); // /dddd/eee.txt
console.info(uriObj1.scheme); // ftp
console.info(uriObj1.userInfo); // null
console.info(uriObj1.port); // -1
console.info(uriObj1.query); // null

const uriObj2 = new uri.URI('gopher://spinaltap.micro.umn.edu/00/Weather/California/Los%20Angeles#fragment');
console.info(uriObj2.host); // spinaltap.micro.umn.edu
console.info(uriObj2.fragment); // fragment
console.info(uriObj2.path); // /00/Weather/California/Los Angeles
console.info(uriObj2.scheme); // gopher
console.info(uriObj2.userInfo); // null
console.info(uriObj2.port); // -1
console.info(uriObj2.query); // null

const uriObj3 = new uri.URI('datashare:///com.samples.datasharetest.DataShare/DB00/TBL00');
console.info(uriObj3.host); // null
console.info(uriObj3.fragment); // null
console.info(uriObj3.path); // /com.samples.datasharetest.DataShare/DB00/TBL00
console.info(uriObj3.scheme); // datashare
console.info(uriObj3.userInfo); // null
console.info(uriObj3.port); // -1
console.info(uriObj3.query); // null

const uriObj4 = new uri.URI('https://username:password@host:8080/directory/file?foo=1&bar=2#fragment');
console.info(uriObj4.host); // host
console.info(uriObj4.fragment); // fragment
console.info(uriObj4.path); // /directory/file
console.info(uriObj4.scheme); // https
console.info(uriObj4.userInfo); // username:password
console.info(uriObj4.port); // 8080
console.info(uriObj4.query); // foo=1&bar=2

const uriObj5 = new uri.URI('dataability:///com.example.DataAbility');
console.info(uriObj5.host); // null
console.info(uriObj5.fragment); // null
console.info(uriObj5.path); // /com.example.DataAbility
console.info(uriObj5.scheme); // dataability
console.info(uriObj5.userInfo); // null
console.info(uriObj5.port); // -1
console.info(uriObj5.query); // null

const uriObj6 = new uri.URI('https://username:my+name@host:8080/directory/my+file?foo=1&bar=2#fragment');
console.info(uriObj6.encodedUserInfo); // username:my+name
console.info(uriObj6.encodedPath); // /directory/my+file
console.info(uriObj6.encodedQuery); // foo=1&bar=2
console.info(uriObj6.encodedFragment); // fragment
console.info(uriObj6.encodedAuthority); // username:my+name@host:8080
console.info(uriObj6.encodedSSP); // //username:my+name@host:8080/directory/my+file?foo=1&bar=2

const uriObj7 = new uri.URI('www.abc.com:8080/directory/file?ab=pppppp#qwer=da');
console.info(uriObj7.scheme); // www.abc.com
console.info(uriObj7.host); // null
console.info(uriObj7.port); // -1
console.info(uriObj7.path); // null
console.info(uriObj7.query); // null
console.info(uriObj7.authority); // null
console.info(uriObj7.fragment); // qwer=da
console.info(uriObj7.ssp); // 8080/directory/file?ab=pppppp
console.info('result:', uriObj7.checkIsAbsolute()); // result: true
```

### constructor

constructor(uri: string)

The constructor is used to create a URI object. It parses the input URI string according to the RFC3986 specification and decomposes it into components such as scheme, userInfo, host, port, path, query, and fragment. For details about the URI string format, see [Naming Rules](#naming-rules).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| uri | string | Yes | URI string to be parsed, which must comply with RFC 3986. |

**Error codes**

For details about the error codes, see [Utils Error Codes](errorcode-utils.md).

| ID| Error Message|
| -------- | -------- |
| 10200002 | Invalid uri string. |

**Example**

```ts
let uriString = 'https://username:password@host:8080/directory/file?foo=1&bar=2#fragment';
new uri.URI(uriString);
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

Determines whether this URI is equal to another URI object by comparing the scheme, authority, path, query, and fragment components one by one to determine whether the two URIs are equivalent.

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

Normalizes the path of this URI, which is applicable to scenarios where the path contains dot segments (. or ..).

> **Description**
>
> If this URI is opaque, or if its path is already in normal form, this URI is returned. Otherwise, a new URI is constructed that is identical to this URI, except that its path is computed by normalizing the path of this URI, according to the following rules:
>
>  1. Remove all . (dot) segments.
>
>  2. If a .. (double dot) segment is preceded by a non-.. segment, both segments are removed together. This step is repeated until it is no longer applicable.
>
> If the path begins with a .. (double dot) segment after normalization, this indicates that there was not enough non-.. segments to remove before, therefore the path will start with a .. segment.


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
const uriInstance1 = uriInstance.normalize();
console.info(uriInstance1.path); // /path/path2/path3
let uri1 = new uri.URI('http://www.test.com/../../patch/path1/../path2/path3/./path4/../');
console.info(uri1.path); // /../../patch/path1/../path2/path3/./path4/../
// If normalization result in a path starting with a .. (double-dot) segment, it indicates that there were insufficient preceding non-.. segments for removal. As a result, the path will start with a .. segment.
let uri2 = uri1.normalize();
console.info(uri2.path); // /../../patch/path2/path3
```

### checkRelative<sup>12+</sup>

checkRelative(): boolean

Determines whether this URI is a relative URI. A relative URI is a URI that does not contain a scheme component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type   | Description                                      |
| ------- | ------------------------------------------ |
| boolean | **true**: The URI is a relative URI.<br>**false**: The URI is not a relative URI.|

**Example**

```ts
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080?query=p');
console.info(`${uriInstance.checkRelative()}`); // false
const uriInstance1 = new uri.URI('/images/pic.jpg');
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
const uriInstance = new uri.URI('http://www.test.com/images/pic.jpg');
console.info(`${uriInstance.checkOpaque()}`); // false
const uriInstance1 = new uri.URI('mailto:user@example.com');
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
const uriInstance = new uri.URI('http://www.test.com/images/pic.jpg');
console.info(`${uriInstance.checkHierarchical()}`); // true
const uriInstance1 = new uri.URI('mailto:user@example.com');
console.info(`${uriInstance1.checkHierarchical()}`); // false
```

### getQueryValue<sup>12+</sup>

getQueryValue(key: string): string

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
| string | Value of the first URI query parameter after decoding. If no value is found, a null object is returned.|

**Example**

```ts
const uriInstance = new uri.URI('https://www.com?param1=value1&param2=value2');
console.info(uriInstance.getQueryValue('param1')); // value1
const uriInstance1 = new uri.URI('https://www.zyy.ss?sa%3D=po%7E');
console.info(uriInstance1.getQueryValue('sa=')) // po~
console.info(uriInstance1.getQueryValue('abc')) // null
```

### addQueryValue<sup>12+</sup>

addQueryValue(key: string, value: string): URI

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

**Example**

```ts
const uriInstance = new uri.URI('https://www.test.com');
const newRoute = uriInstance.addQueryValue('param1', 'hello world');
console.info(newRoute.toString()); // https://www.test.com?param1=hello%20world
```

### addSegment<sup>12+</sup>

addSegment(pathSegment: string): URI

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

**Example**

```ts
const uriInstance = new uri.URI('http://www.test.com');
const uriWithSegment = uriInstance.addSegment('my image.jpg');
console.info(uriWithSegment.toString()); // http://www.test.com/my%20image.jpg
```

### addEncodedSegment<sup>12+</sup>

addEncodedSegment(pathSegment: string): URI

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

**Example**

```ts
const uriInstance = new uri.URI('http://www.test.com');
const uriWithEncodedSegment = uriInstance.addEncodedSegment('my%20image.jpg');
console.info(uriWithEncodedSegment.toString()); // http://www.test.com/my%20image.jpg
```

### getQueryNames<sup>12+</sup>

getQueryNames(): string[]

Obtains all non-repeated keys in the query component of this URI. The query component follows the question mark (?) and consists of key-value pairs, separated by the at sign (&). In each key-value pair, the equal sign (=) is used to connect the key and value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type       | Description                               |
| ----------- | ----------------------------------- |
| string[] | A set of all non-repeated parameter names after decoding in the query component of this URI.|

**Example**

```ts
const uriInstance = new uri.URI('https://www.test.com?param1=value1&param2=value2');
const paramNames = uriInstance.getQueryNames();
console.info(paramNames.toString()); // param1,param2
```

### getQueryValues<sup>12+</sup>

getQueryValues(key: string): string[]

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

**Example**

```ts
const uriInstance = new uri.URI('https://www.test.com/search?query=name&query=my');
console.info(uriInstance.getQueryValues('query').toString()); // name,my
console.info(JSON.stringify(uriInstance.getQueryValues('abc'))); // []
```

### getBooleanQueryValue<sup>12+</sup>

getBooleanQueryValue(key: string, defaultValue: boolean): boolean

Queries the URI query string for the specified key name and returns the corresponding Boolean value.

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

**Example**

```ts
const uriInstance = new uri.URI('https://www.test.com/search?active=true');
console.info(`${uriInstance.getBooleanQueryValue('active', false)}`); // true
const uriInstance1 = new uri.URI('https://www.test.com/search');
console.info(`${uriInstance1.getBooleanQueryValue('active', false)}`); // false
const uriInstance2 = new uri.URI('https://www.test.com/search?active=aa&active=false');
console.info(`${uriInstance2.getBooleanQueryValue('active', false)}`); // true
const uriInstance3 = new uri.URI('https://www.test.com/search?active=0');
console.info(`${uriInstance3.getBooleanQueryValue('active', true)}`); // false
const uriInstance4 = new uri.URI('https://www.test.com/search');
console.info(`${uriInstance4.getBooleanQueryValue('active', true)}`); // true
```

### clearQuery<sup>12+</sup>

clearQuery(): URI

Clears the query part of the URI and creates a new URI object to return, while keeping the original URI object unchanged.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description                                 |
| ---- | ------------------------------------- |
| [URI](#uri)  | URI object whose query component has been cleared.|

**Example**

```ts
const uriInstance = new uri.URI('https://www.test.com?param1=value1');
console.info(uriInstance.clearQuery().toString()); // https://www.test.com
```

### getLastSegment<sup>12+</sup>

getLastSegment(): string

Obtains the last segment of the path of this URI. Each segment represents a part of the path, usually separated by "/". A path segment ending with a slash is not counted as a segment, and no segment is counted when there is no path.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type| Description                         |
| ---- | ----------------------------- |
| string  | The last segment of this URI. If the URI is empty, a null object is returned.|

**Example**

```ts
const uriInstance = new uri.URI('content://com.test.provider/files/image.jpg');
console.info(uriInstance.getLastSegment()); // image.jpg
```

### getSegment<sup>12+</sup>

getSegment(): string[]

Obtains all decoded segments in this URI.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Return value**

| Type    | Description                       |
| -------- | --------------------------- |
| string[] | All decoded segments in this URI, each of which does not contain a slash (/) before or after the segment.|

**Example**

```ts
const uriInstance = new uri.URI('http://www.test.com/path/to/image.jpg');
console.info(uriInstance.getSegment().toString()); // path,to,image.jpg
```

### createFromParts<sup>12+</sup>

static createFromParts(scheme: string, ssp: string, fragment: string): URI

Creates a new URI object based on the provided scheme, scheme-specific part (ssp), and fragment.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Utils.Lang

**Parameters**

| Name  | Type  | Mandatory| Description                           |
| -------- | ------ | ---- | ------------------------------- |
| scheme   | string | Yes   | Scheme part of this URI. This parameter must comply with the URI protocol standard. |
| ssp      | string | Yes  | Scheme-specific part of the URI, that is, all content between the protocol separator ":" and the fragment separator "#". This part will be encoded.|
| fragment | string | Yes  | Fragment component of the URI, that is, the content following the number sign (#). If the fragment is not defined, the fragment is empty. This part will also be encoded.|

**Return value**

| Type| Description                                             |
| ---- | ------------------------------------------------- |
| [URI](#uri)  | Returns a URI object created from the given scheme, scheme-specific part, and fragment. |

**Example**

```ts
const uriInstance = uri.URI.createFromParts('mailto', 'no body', 'top');
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