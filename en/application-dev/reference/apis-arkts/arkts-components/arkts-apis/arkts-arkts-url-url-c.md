# URL

```TypeScript
class URL
```

The interface of URL is used to parse, construct, normalize, and encode URLs.

**Since:** 7

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { url } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(url: string, base?: string | URL)
```

URL constructor, which is used to instantiate a URL object. url: Absolute or relative input URL to resolve. Base is required if input is relative. If input is an absolute value, base ignores the value. base: Base URL to parse if input is not absolute.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [parseURL](#parseurl)

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | url url |
| base | string &#124; URL | No | base base |

**Examples**

```TypeScript
let mm = 'https://username:password@host:8080';
let a = new url.URL("/", mm); // Output 'https://username:password@host:8080/';
let b = new url.URL(mm); // Output 'https://username:password@host:8080/';
new url.URL('path/path1', b); // Output 'https://username:password@host:8080/path/path1';
let c = new url.URL('/path/path1', b);  // Output 'https://username:password@host:8080/path/path1'; 
new url.URL('/path/path1', c); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', a); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', "https://www.exampleUrl/fr-FR/toot"); // Output https://www.exampleUrl/path/path1
new url.URL('/path/path1', ''); // Raises a TypeError exception as '' is not a valid URL
new url.URL('/path/path1'); // Raises a TypeError exception as '/path/path1' is not a valid URL
new url.URL('https://www.example.com', ); // Output https://www.example.com/
new url.URL('https://www.example.com', b); // Output https://www.example.com/
```

<a id="constructor-1"></a>

## constructor

```TypeScript
constructor()
```

A no-argument constructor used to create a URL. It returns a URL object after parseURL is called. It is not used independently.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
let mm = 'https://username:password@host:8080';
let a = new url.URL("/", mm); // Output 'https://username:password@host:8080/';
let b = new url.URL(mm); // Output 'https://username:password@host:8080/';
new url.URL('path/path1', b); // Output 'https://username:password@host:8080/path/path1';
let c = new url.URL('/path/path1', b);  // Output 'https://username:password@host:8080/path/path1'; 
new url.URL('/path/path1', c); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', a); // Output 'https://username:password@host:8080/path/path1';
new url.URL('/path/path1', "https://www.exampleUrl/fr-FR/toot"); // Output https://www.exampleUrl/path/path1
new url.URL('/path/path1', ''); // Raises a TypeError exception as '' is not a valid URL
new url.URL('/path/path1'); // Raises a TypeError exception as '/path/path1' is not a valid URL
new url.URL('https://www.example.com', ); // Output https://www.example.com/
new url.URL('https://www.example.com', b); // Output https://www.example.com/
```

## parseURL

```TypeScript
static parseURL(url: string, base?: string | URL): URL
```

Parses a URL.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| url | string | Yes | A string representing an absolute or a relative URL. In the case of a relative URL, you must specify base to parse the final URL. In the case of an absolute URL, the passed base will be ignored. |
| base | string &#124; URL | No | Either a string or an object. The default value is undefined.   - string: string.   - URL: URL object.   This parameter is used when url is a relative URL. |

**Return value:**

| Type | Description |
| --- | --- |
| URL |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-parameter-parsing-error) | Invalid url string. |

**Examples**

```TypeScript
let mm = 'https://username:password@host:8080/test/test1/test3';
let urlObject = url.URL.parseURL(mm);
let result = urlObject.toString(); // Output 'https://username:password@host:8080/test/test1/test3'
// If url is a relative path, the path in the base parameter is test/test1, and the path of the parsed URL is /test/path2/path3.
let url1 = url.URL.parseURL('path2/path3', 'https://www.example.com/test/test1'); // Output 'https://www.example.com/test/path2/path3'
// If url is a root directory, the path in the base parameter is /test/test1/test3, and the path of the parsed URL is /path1/path2.
let url2 = url.URL.parseURL('/path1/path2', urlObject); // Output 'https://username:password@host:8080/path1/path2'
url.URL.parseURL('/path/path1', "https://www.exampleUrl/fr-FR/toot"); // Output 'https://www.exampleUrl/path/path1'
url.URL.parseURL('/path/path1', ''); // Raises a TypeError exception as '' is not a valid URL
url.URL.parseURL('/path/path1'); // Raises a TypeError exception as '/path/path1' is not a valid URL
url.URL.parseURL('https://www.example.com', ); // Output 'https://www.example.com/'
url.URL.parseURL('https://www.example.com', urlObject); // Output 'https://www.example.com/'
```

## toJSON

```TypeScript
toJSON(): string
```

Converts the parsed URL into a JSON string.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the serialized URL as a string. |

**Examples**

```TypeScript
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = urlObject.toJSON();
```

## toString

```TypeScript
toString(): string
```

Converts the parsed URL into a string.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the serialized URL as a string. |

**Examples**

```TypeScript
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = urlObject.toString(); // Output 'https://username:password@host:8080/directory/file?query=pppppp#qwer=da'
```

## hash

```TypeScript
hash: string
```

Gets and sets the fragment portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## host

```TypeScript
host: string
```

Gets and sets the host portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## hostname

```TypeScript
hostname: string
```

Gets and sets the host name portion of the URL，not include the port.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## href

```TypeScript
href: string
```

Gets and sets the serialized URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## origin

```TypeScript
readonly origin: string
```

Gets the read-only serialization of the URL's origin.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## params

```TypeScript
readonly params: URLParams
```

Gets the URLParams object that represents the URL query parameter. This property is read-only, but URLParams provides an object that can be used to change the URL instance. To replace the entire query parameter for a URL, use url.searchsetter.

**Type:** [URLParams](arkts-arkts-url-urlparams-c.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## password

```TypeScript
password: string
```

Gets and sets the password portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## pathname

```TypeScript
pathname: string
```

Gets and sets the path portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## port

```TypeScript
port: string
```

Gets and sets the port portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## protocol

```TypeScript
protocol: string
```

Gets and sets the protocol portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## search

```TypeScript
search: string
```

Gets and sets the serialized query portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## searchParams

```TypeScript
readonly searchParams: URLSearchParams
```

Gets the URLSearchParams object that represents the URL query parameter. This property is read-only, but URLSearchParams provides an object that can be used to change the URL instance. To replace the entire query parameter for a URL, use url.searchsetter.

**Type:** URLSearchParams

**Since:** 7

**Deprecated since:** 9

**Substitutes:** params

**System capability:** SystemCapability.Utils.Lang

## username

```TypeScript
username: string
```

Gets and sets the username portion of the URL.

**Type:** string

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
