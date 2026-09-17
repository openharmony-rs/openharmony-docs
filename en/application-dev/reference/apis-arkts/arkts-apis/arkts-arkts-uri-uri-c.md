# URI

URI Represents a Uniform Resource Identifier (URI) reference.

**Since:** 8

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { uri } from '@kit.ArkTS';
```

## addEncodedSegment

```TypeScript
addEncodedSegment(pathSegment: string): URI
```

Appends an encoded field to the path component of this URI to create a new URI and returns the new URI, while keeping the existing URI unchanged.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathSegment | string | Yes | Encoding path segment to be added. |

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | After adding, return the URI object. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("http://www.test.com");
const newRoute = uriInstance.addEncodedSegment("my%20image.jpg");
console.info(newRoute.toString()); // http://www.test.com/my%20image.jpg
```

## addQueryValue

```TypeScript
addQueryValue(key: string, value: string): URI
```

Adds a query parameter to this URI to create a new URI, while keeping the existing URI unchanged.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the query parameter. |
| value | string | Yes | Value of the query parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | Return URI object. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://www.test.com");
const newRoute = uriInstance.addQueryValue("param1", "hello world");
console.info(newRoute.toString()); // https://www.test.com?param1=hello%20world
```

## addSegment

```TypeScript
addSegment(pathSegment: string): URI
```

Encodes a given field, appends it to the path component of this URI to create a new URI, and returns the new URI, while keeping the existing URI unchanged.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pathSegment | string | Yes | path segment to be added. |

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | After adding, return the URI object. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("http://www.test.com");
const newRoute = uriInstance.addSegment("my image.jpg");
console.info(newRoute.toString()); // http://www.test.com/my%20image.jpg
```

## checkHierarchical

```TypeScript
checkHierarchical(): boolean
```

Checks whether this URI is a hierarchical URI. The URI that starts with a slash (/) in scheme-specific-part is a hierarchical URI. Relative URIs are also hierarchical.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return true as Hierarchical, otherwise return false. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("http://www.test.com/images/pic.jpg");
console.info(`${uriInstance.checkHierarchical()}`); // true
const uriInstance1 = new uri.URI("mailto:user@example.com");
console.info(`${uriInstance1.checkHierarchical()}`); // false
```

## checkIsAbsolute

```TypeScript
checkIsAbsolute(): boolean
```

Checks whether this URI is an absolute URI (whether the scheme component is defined).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean Indicates whether the URI is an absolute URI (whether the scheme component is defined). |

**Examples**

```TypeScript
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080?query=pppppp');
console.info(`${uriInstance.checkIsAbsolute()}`); // true
const uriInstance1 = new uri.URI('xxx.com/suppliers.htm');
console.info(`${uriInstance1.checkIsAbsolute()}`); // false
```

## checkOpaque

```TypeScript
checkOpaque(): boolean
```

Checks whether this URI is an opaque URI. The URI that does not start with a slash (/) is an opaque URI.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return true as Opaque, otherwise return false. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("http://www.test.com/images/pic.jpg");
console.info(`${uriInstance.checkOpaque()}`); // false
const uriInstance1 = new uri.URI("mailto:user@example.com");
console.info(`${uriInstance1.checkOpaque()}`); // true
```

## checkRelative

```TypeScript
checkRelative(): boolean
```

Determine whether URI is Relative.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Return true as Relative, otherwise return false. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://username:password@www.qwer.com:8080?query=p");
console.info(`${uriInstance.checkRelative()}`); // false
const uriInstance1 = new uri.URI("/images/pic.jpg");
console.info(`${uriInstance1.checkRelative()}`); // true
```

## clearQuery

```TypeScript
clearQuery(): URI
```

Clears the query component of this URI to create a new URI, while keeping the existing URI object unchanged.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | After clearing, return the URI object. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://www.test.com?param1=value1");
console.info(uriInstance.clearQuery().toString()); // https://www.test.com
```

## constructor

```TypeScript
constructor(uri: string)
```

A constructor used to create a URI instance.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Input object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-parameter-parsing-error) | Invalid uri string. |

**Examples**

```TypeScript
let mm = 'https://username:password@host:8080/directory/file?foo=1&bar=2#fragment';
new uri.URI(mm);
```

```TypeScript
new uri.URI('https://username:password@host:8080');
```

## createFromParts

```TypeScript
static createFromParts(scheme: string, ssp: string, fragment: string): URI
```

Creates a URI based on the provided scheme, scheme-specific-part, and fragment components.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scheme | string | Yes | of the URI. |
| ssp | string | Yes | scheme-specific-part, everything between the scheme separator (':') and the fragment separator ('#'), which will get encoded. |
| fragment | string | Yes | fragment, everything after the '#', null if undefined, will get encoded. |

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | Return Uri consisting of a given scheme, SSP, and fragment. |

**Examples**

```TypeScript
const uriInstance = uri.URI.createFromParts("mailto", "no body", "top");
console.info(uriInstance.toString()); // mailto:no%20body#top
```

## equals

```TypeScript
equals(other: URI): boolean
```

Check whether this URI is equivalent to other URI objects.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [equalsTo](#equalsto)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [URI](arkts-arkts-uri-uri-c.md) | Yes | other other URI object to be compared |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean Tests whether this URI is equivalent to other URI objects. |

**Examples**

```TypeScript
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
uriInstance.equals(uriInstance1); // true
```

## equalsTo

```TypeScript
equalsTo(other: URI): boolean
```

Checks whether this URI is the same as another URI object.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| other | [URI](arkts-arkts-uri-uri-c.md) | Yes | URI object to compare. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | boolean Tests whether this URI is equivalent to other URI objects. |

**Examples**

```TypeScript
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = uriInstance.equalsTo(uriInstance1); // true
```

## getBooleanQueryValue

```TypeScript
getBooleanQueryValue(key: string, defaultValue: boolean): boolean
```

Obtains the value of the Boolean type of a query parameter in this URI.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Indicates the key value to be queried. |
| defaultValue | boolean | Yes | The default value returned when the key has no query parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Query returns defaultValue if the key does not exist. Query returns false if the value of the key is "false" or "0", otherwise returns true. |

**Examples**

```TypeScript
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

## getLastSegment

```TypeScript
getLastSegment(): string
```

Obtains the last segment of this URI.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the last decoded segment, or null if the path is empty. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("content://com.test.provider/files/image.jpg");
console.info(uriInstance.getLastSegment()); // image.jpg
```

## getQueryNames

```TypeScript
getQueryNames(): string[]
```

Obtains all non-repeated keys in the query component of this URI.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Return a set of decoded names. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://www.test.com?param1=value1&param2=value2");
const paramNames = uriInstance.getQueryNames();
console.info(paramNames.toString()); // param1,param2
```

## getQueryValue

```TypeScript
getQueryValue(key: string): string
```

Obtains the first value of a given key from the query component of this URI. If the query component contains encoded content, this API decodes the key before obtaining the value.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the query parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Return decoded value. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://www.com?param1=value1&param2=value2");
console.info(uriInstance.getQueryValue("param1")); // value1
let uriInstance1 = new uri.URI('https://www.zyy.ss?sa%3D=po%7E');
console.info(uriInstance1.getQueryValue('sa=')) // po~
console.info(uriInstance1.getQueryValue('abc')) // null
```

## getQueryValues

```TypeScript
getQueryValues(key: string): string[]
```

Obtains the values of a given key from the query component of this URI.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the URI query parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Return a set of decoded values. |

**Examples**

```TypeScript
const uriInstance = new uri.URI("https://www.test.com/search?query=name&query=my");
console.info(uriInstance.getQueryValues("query").toString()); // name,my
console.info(JSON.stringify(uriInstance.getQueryValues("abc"))); // []
```

## getSegment

```TypeScript
getSegment(): string[]
```

Gets the decoded path segments.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string[] | Return decoded path segments, each without a leading or trailing "/". |

**Examples**

```TypeScript
const uriInstance = new uri.URI("http://www.test.com/path/to/image.jpg");
console.info(uriInstance.getSegment().toString()); // path,to,image.jpg
```

## normalize

```TypeScript
normalize(): URI
```

Normalizes the path of this URI.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| [URI](arkts-arkts-uri-uri-c.md) | URI Used to normalize the path of this URI and return a URI object whose path has been normalized. |

**Examples**

```TypeScript
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

## toString

```TypeScript
toString(): string
```

Converts this URI into an encoded string.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | URI in a serialized string. |

**Examples**

```TypeScript
const result = new uri.URI('https://username:password@host:8080/directory/file?ab=pppppp#qwer da');
let result1 = result.toString(); // https://username:password@host:8080/directory/file?ab=pppppp#qwer%20da
```

## authority

```TypeScript
authority: string
```

Gets/Sets the decoding permission component part of this URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## encodedAuthority

```TypeScript
encodedAuthority: string
```

Gets/Sets the encoded authority part of this URI.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## encodedFragment

```TypeScript
encodedFragment: string
```

Gets/Sets the encoded fragment part of this URI, everything after the '#'.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## encodedPath

```TypeScript
encodedPath: string
```

Gets/Sets the encoded path portion of the URI.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## encodedQuery

```TypeScript
encodedQuery: string
```

Gets/Sets the encoded query component from this URI.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## encodedSSP

```TypeScript
encodedSSP: string
```

Gets/Sets the scheme-specific part of this URI, i.e. everything between the scheme separator ':' and the fragment separator '#'.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## encodedUserInfo

```TypeScript
encodedUserInfo: string
```

Gets/Sets Obtains the encoded user information part of the URI.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

## fragment

```TypeScript
fragment: string
```

Gets/Sets the fragment part of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## host

```TypeScript
host: string
```

Gets the hostname portion of the URI without a port.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## path

```TypeScript
path: string
```

Gets/Sets the path portion of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## port

```TypeScript
port: string
```

Gets the port portion of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## query

```TypeScript
query: string
```

Gets/Sets the query portion of the URI

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## scheme

```TypeScript
scheme: string
```

Gets/Sets the protocol part of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## ssp

```TypeScript
ssp: string
```

Gets/Sets the decoding scheme-specific part of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## userInfo

```TypeScript
userInfo: string
```

Gets/Sets Obtains the user information part of the URI.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
