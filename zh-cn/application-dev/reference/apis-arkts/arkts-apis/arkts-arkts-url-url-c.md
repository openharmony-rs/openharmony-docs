# URL(URL字符串解析)

用于解析和构造完整URL。

**起始版本：** 23

<!--Device-url-class URL--><!--Device-url-class URL-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

## constructor

```TypeScript
constructor(url: string, base?: string | URL)
```

URL的构造函数。与parseURL方法功能相同，但parseURL为静态工厂方法，推荐使用parseURL来创建URL对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [parseURL](#parseurl)

<!--Device-URL-constructor(url: string, base?: string | URL)--><!--Device-URL-constructor(url: string, base?: string | URL)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 一个表示绝对URL或相对URL的字符串，必须是合法的URL格式。 <br/>如果url是相对URL，则需要指定base，用于解析最终的URL。 <br/>如果 url是绝对URL，则给定的base将不会生效。 |
| base | string \| URL | 否 | 入参字符串或者对象，默认值是undefined。<br>- string：表示基础URL的字符串， 当url为相对URL时需为合法URL格式。<br>- URL：已解析的URL对象，用作相对URL解析的基础地址。 |

**示例**

```TypeScript
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

## constructor

```TypeScript
constructor()
```

URL的无参构造函数，不建议直接调用。请使用parseURL方法创建URL对象。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-constructor()--><!--Device-URL-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

**示例**

```TypeScript
let a = new url.URL();
```

## parseURL

```TypeScript
static parseURL(url: string, base?: string | URL): URL
```

解析URL字符串，返回解析后的URL对象。该对象包含协议、主机、端口、路径和查询参数等URL组成部分。 > **说明：** > > 当入参url是相对URL时，调用该接口解析后的URL并不是简单地将入参url和base直接拼接。 > url内容为相对路径格式时，会相对于base的当前目录进行解析，包括base中path字段最后一个斜杠前的所有路径片段， > 但不包括其后的部分（参照示例中url1）。url内容为指向根目录的格式时，会相对于base的原始地址（origin）进行解析（参照示例中url2）。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-static parseURL(url: string, base?: string | URL): URL--><!--Device-URL-static parseURL(url: string, base?: string | URL): URL-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 一个表示绝对URL或相对URL的字符串。 <br/>如果 url 是相对URL，则需要指定 base，用于解析最终的URL。 <br/>如果 url 是绝对URL，则给定的 base 将不会生效。 |
| base | string \| URL | 否 | 入参字符串或者对象，默认值是undefined。<br/>- string：字符串。当第一个参数是相对URL时，该参数需符合URL标准。<br/>- URL：URL对象。<br/>- 在url是相对URL时使用，url为绝对URL时此参数不会生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URL | 返回解析后的URL对象，包含URL的各组成部分（如协议、主机和路径等属性）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid url string. |

**示例**

```TypeScript
let baseUrl = 'https://username:password@host:8080/test/test1/test3';
let urlObject = url.URL.parseURL(baseUrl);
let result = urlObject.toString(); // Output 'https://username:password@host:8080/test/test1/test3'
// url内容为相对路径格式时，此时base参数的path为test/test1,解析后的URL的path为/test/path2/path3
let relativePathUrl = url.URL.parseURL('path2/path3', 'https://www.example.com/test/test1'); // Output 'https://www.example.com/test/path2/path3'
// url内容为指向根目录的格式时，此时base参数的path为/test/test1/test3，解析后的URL的path为/path1/path2
let rootPathUrl = url.URL.parseURL('/path1/path2', urlObject); // Output 'https://username:password@host:8080/path1/path2'
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

将解析过后的URL转化为JSON字符串。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-toJSON(): string--><!--Device-URL-toJSON(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | URL对象的JSON序列化字符串。 |

**示例**

```TypeScript
// 解析URL字符串
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
// 将URL转化为字符串
let result = urlObject.toJSON();
```

## toString

```TypeScript
toString(): string
```

将解析过后的URL转化为字符串，返回值与URL的href属性值相同。

**起始版本：** 23

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-toString(): string--><!--Device-URL-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 解析后的URL序列化字符串。 |

**示例**

```TypeScript
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = urlObject.toString(); // Output 'https://username:password@host:8080/directory/file?query=pppppp#qwer=da'
```

## hash

```TypeScript
hash: string
```

获取和设置URL的片段部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-hash: string--><!--Device-URL-hash: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## host

```TypeScript
host: string
```

获取和设置URL的主机部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-host: string--><!--Device-URL-host: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## hostname

```TypeScript
hostname: string
```

获取和设置URL的主机名部分，不带端口。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-hostname: string--><!--Device-URL-hostname: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## href

```TypeScript
href: string
```

获取和设置序列化的URL。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-href: string--><!--Device-URL-href: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## origin

```TypeScript
readonly origin: string
```

获取URL源的只读序列化。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-readonly origin: string--><!--Device-URL-readonly origin: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## params

```TypeScript
readonly params: URLParams
```

获取URLParams表示URL查询参数的对象。

**类型：** [URLParams](arkts-arkts-url-urlparams-c.md)

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-readonly params: URLParams--><!--Device-URL-readonly params: URLParams-End-->

**系统能力：** SystemCapability.Utils.Lang

## password

```TypeScript
password: string
```

获取和设置URL的密码部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-password: string--><!--Device-URL-password: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## pathname

```TypeScript
pathname: string
```

获取和设置URL的路径部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-pathname: string--><!--Device-URL-pathname: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## port

```TypeScript
port: string
```

获取和设置URL的端口部分。当port为当前protocol的默认端口时，port将被解析为空字符串。 > **说明：** > > 在解析URL字符串时，如果入参中的port内容是当前protocol的默认端口，那么port将被解析为空字符串。默认端口为：http为80，https为443，ftp为21，gopher为70，ws为80， > wss为443。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-port: string--><!--Device-URL-port: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## protocol

```TypeScript
protocol: string
```

获取和设置URL的协议部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-protocol: string--><!--Device-URL-protocol: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## search

```TypeScript
search: string
```

获取和设置URL的序列化查询部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-search: string--><!--Device-URL-search: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## searchParams

```TypeScript
readonly searchParams: URLSearchParams
```

获取URLSearchParams表示URL查询参数的对象。

**类型：** [URLSearchParams](arkts-arkts-url-urlsearchparams-c.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [URLParams](arkts-arkts-url-urlparams-c.md)

<!--Device-URL-readonly searchParams: URLSearchParams--><!--Device-URL-readonly searchParams: URLSearchParams-End-->

**系统能力：** SystemCapability.Utils.Lang

## username

```TypeScript
username: string
```

获取和设置URL的用户名部分。

**类型：** string

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-username: string--><!--Device-URL-username: string-End-->

**系统能力：** SystemCapability.Utils.Lang

