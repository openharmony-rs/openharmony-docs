# URL

用于解析、构造、规范、编码对应的URL字符串。

**起始版本：** 7

<!--Device-url-class URL--><!--Device-url-class URL-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { url } from '@kit.ArkTS';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor(url: string, base?: string | URL)
```

URL的构造函数。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** parseURL

<!--Device-URL-constructor(url: string, base?: string | URL)--><!--Device-URL-constructor(url: string, base?: string | URL)-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 一个表示绝对URL或相对URL的字符串。 <br/>如果 url 是相对URL，则需要指定 base，用于解析最终的URL。 <br/>如果 url 是绝对URL，则给定的 base 将不会生效。 |
| base | string \| URL | 否 | 入参字符串或者对象，默认值是undefined。<br/>- string：字符串。<br/>- URL：URL对象。 |

<a id="constructor-1"></a>
## constructor

```TypeScript
constructor()
```

URL的无参构造函数。parseURL调用后返回一个URL对象，不单独使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-constructor()--><!--Device-URL-constructor()-End-->

**系统能力：** SystemCapability.Utils.Lang

<a id="parseurl"></a>
## parseURL

```TypeScript
static parseURL(url: string, base?: string | URL): URL
```

解析URL。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-static parseURL(url: string, base?: string | URL): URL--><!--Device-URL-static parseURL(url: string, base?: string | URL): URL-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| url | string | 是 | 一个表示绝对URL或相对URL的字符串。 <br/>如果 url 是相对URL，则需要指定 base，用于解析最终的URL。 <br/>如果 url 是绝对URL，则给定的 base 将不会生效。 |
| base | string \| URL | 否 | 入参字符串或者对象，默认值是undefined。<br/>- string：字符串。当第一个参数是相对URL时，该参数需符合URL标准。<br/>-URL：URL对象。<br/>- 在url是相对URL时使用。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [URL](arkts-arkts-url-url-c.md) | 返回创建的URL对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid url string. |

**示例：**

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

<a id="tojson"></a>
## toJSON

```TypeScript
toJSON(): string
```

将解析过后的URL转化为JSON字符串。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-toJSON(): string--><!--Device-URL-toJSON(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转化后的JSON字符串。 |

**示例：**

```TypeScript
// 解析URL字符串
const urlObject = url.URL.parseURL('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
// 将URL转化为字符串
let result = urlObject.toJSON();

```

<a id="tostring"></a>
## toString

```TypeScript
toString(): string
```

将解析过后的URL转化为字符串。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-URL-toString(): string--><!--Device-URL-toString(): string-End-->

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 转化后的字符串。 |

**示例：**

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

**类型：** URLParams

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

获取和设置URL的端口部分。

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

**类型：** URLSearchParams

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [null]

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

