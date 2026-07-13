# URI

构造一个URI对象，并提供判断两个URI是否相等、对URI路径部分进行编码规范化等方法。

**起始版本：** 8

**系统能力：** SystemCapability.Utils.Lang

## addEncodedSegment

```TypeScript
addEncodedSegment(pathSegment: string): URI
```

将已编码的字段追加到当前URI的path字段中，创建新URI对象并返回，保持原有URI对象不变。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathSegment | string | 是 | 需要追加到路径部分的编码字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回已追加字段的URI对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('http://www.test.com');
const uriWithEncodedSegment = uriInstance.addEncodedSegment('my%20image.jpg');
console.info(uriWithEncodedSegment.toString()); // http://www.test.com/my%20image.jpg

```

## addQueryValue

```TypeScript
addQueryValue(key: string, value: string): URI
```

在当前URI对象上添加查询参数后返回新的URI对象，保持原有URI对象不变。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 需要添加查询参数的名称。 |
| value | string | 是 | 需要添加查询参数的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回添加查询部分后的URI对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://www.test.com');
const newRoute = uriInstance.addQueryValue('param1', 'hello world');
console.info(newRoute.toString()); // https://www.test.com?param1=hello%20world

```

## addSegment

```TypeScript
addSegment(pathSegment: string): URI
```

对指定字段进行编码，并将其追加到当前URI对象的path中，创建并返回新的URI对象，保持原有URI对象不变。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pathSegment | string | 是 | 需要追加到路径部分的字段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回已追加字段的URI对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('http://www.test.com');
const uriWithSegment = uriInstance.addSegment('my image.jpg');
console.info(uriWithSegment.toString()); // http://www.test.com/my%20image.jpg

```

## checkHierarchical

```TypeScript
checkHierarchical(): boolean
```

判断此URI是否为分层的URI，方案特定部分以“/”开头的URI为分层的URI。相对URI也是分层的。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果是分层的URI返回true，否则返回false。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('http://www.test.com/images/pic.jpg');
console.info(`${uriInstance.checkHierarchical()}`); // true
const uriInstance1 = new uri.URI('mailto:user@example.com');
console.info(`${uriInstance1.checkHierarchical()}`); // false

```

## checkIsAbsolute

```TypeScript
checkIsAbsolute(): boolean
```

判断URI是否为绝对URI，即是否包含scheme组件。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果是绝对URI返回true，否则返回false。 |

**示例：**

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

判断此URI是否为不透明URI，方案特定部分不以“/”开头的URI为不透明的URI。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果是不透明的URI返回true，否则返回false。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('http://www.test.com/images/pic.jpg');
console.info(`${uriInstance.checkOpaque()}`); // false
const uriInstance1 = new uri.URI('mailto:user@example.com');
console.info(`${uriInstance1.checkOpaque()}`); // true

```

## checkRelative

```TypeScript
checkRelative(): boolean
```

判断此URI是否为相对URI，相对URI指的是不包含协议(scheme)部分的URI。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果是相对URI返回true，否则返回false。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080?query=p');
console.info(`${uriInstance.checkRelative()}`); // false
const uriInstance1 = new uri.URI('/images/pic.jpg');
console.info(`${uriInstance1.checkRelative()}`); // true

```

## clearQuery

```TypeScript
clearQuery(): URI
```

清除URI路径查询部分，并创建一个新的URI对象返回，同时保持原有URI对象不变。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回一个已被清除查询部分的URI对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://www.test.com?param1=value1');
console.info(uriInstance.clearQuery().toString()); // https://www.test.com

```

## constructor

```TypeScript
constructor(uri: string)
```

构造函数用于创建URI对象。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | 入参对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [10200002](../errorcode-utils.md#10200002-参数解析错误) | Invalid uri string. |

**示例：**

```TypeScript
let uriString = 'https://username:password@host:8080/directory/file?foo=1&bar=2#fragment';
new uri.URI(uriString);

```

```TypeScript
new uri.URI('https://username:password@host:8080');

```

## createFromParts

```TypeScript
static createFromParts(scheme: string, ssp: string, fragment: string): URI
```

根据提供的协议、方案以及片段创建一个新的URI对象。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scheme | string | 是 | 此URI协议部分。该参数需符合URI协议标准。 |
| ssp | string | 是 | 此URI的方案特定部分，即位于协议分隔符“:”和片段分隔符“#”之间的所有内容，这部分将被编码。 |
| fragment | string | 是 | 此URI的片段部分，即“#”符号后面的内容，如果未定义则为空，这部分也将被编码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回由给定协议、协议特定部分和片段创建的URI对象。 |

**示例：**

```TypeScript
const uriInstance = uri.URI.createFromParts('mailto', 'no body', 'top');
console.info(uriInstance.toString()); // mailto:no%20body#top

```

## equals

```TypeScript
equals(other: URI): boolean
```

判断此URI是否与其他URI对象相等。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** equalsTo

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | URI | 是 | 需要比较的URI对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示相等，否则返回false。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
uriInstance.equals(uriInstance1); // true

```

## equalsTo

```TypeScript
equalsTo(other: URI): boolean
```

判断此URI是否与其他URI对象相等。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| other | URI | 是 | 需要比较的URI对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回true表示相等，否则返回false。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
const uriInstance1 = new uri.URI('https://username:password@host:8080/directory/file?query=pppppp#qwer=da');
let result = uriInstance.equalsTo(uriInstance1); // true

```

## getBooleanQueryValue

```TypeScript
getBooleanQueryValue(key: string, defaultValue: boolean): boolean
```

根据指定键名，搜索此URI查询字符串并返回其对应的布尔类型值。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的查询参数的名称。 |
| defaultValue | boolean | 是 | 设置查询参数中未包含指定键时返回的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果指定的查询参数不存在，则返回defaultValue的值；查询参数对应第一个值为“false”或者“0”返回false，否则返回true。 |

**示例：**

```TypeScript
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

## getLastSegment

```TypeScript
getLastSegment(): string
```

获取此URI路径的最后一个段。每个段代表路径中的一个部分，通常通过“/”来进行分隔。对于以斜杠结尾的或者没有路径的部分不计入段。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回此URI路径中的最后一个段，如果路径为空则返回null。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('content://com.test.provider/files/image.jpg');
console.info(uriInstance.getLastSegment()); // image.jpg

```

## getQueryNames

```TypeScript
getQueryNames(): string[]
```

获取URI查询部分中所有不重复的键。查询参数出现在问号“?”之后，由键值对组成，键和值用等号“=”连接，键值对间用与号“&”分隔。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回URI查询部分中所有不重复的已解码参数名集合。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://www.test.com?param1=value1&param2=value2');
const paramNames = uriInstance.getQueryNames();
console.info(paramNames.toString()); // param1,param2

```

## getQueryValue

```TypeScript
getQueryValue(key: string): string
```

根据给定的查询关键词，从URI查询参数部分中提取出该关键词对应的第一个值，若查询参数中存在已编码过的内容，需将对应Key进行解码后获取Value。

查询参数在问号“?”后，由键值对组成。键和值用等号“=”连接，键值对用与号“&”分隔。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 此URI查询参数的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回经解码处理后的URI查询参数的第一个值，若未找到对应值则返回null对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://www.com?param1=value1&param2=value2');
console.info(uriInstance.getQueryValue('param1')); // value1
const uriInstance1 = new uri.URI('https://www.zyy.ss?sa%3D=po%7E');
console.info(uriInstance1.getQueryValue('sa=')) // po~
console.info(uriInstance1.getQueryValue('abc')) // null

```

## getQueryValues

```TypeScript
getQueryValues(key: string): string[]
```

获取URI中查询参数指定键的所有值。如果查询参数已编码，需先解码键再获取值。

查询参数是出现在问号“?”之后的部分，由键值对组成，键和值用等号“=”连接，键值对间用与号“&”分隔。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 指定键的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回此URI中查询参数内指定键对应所有值的集合，若没有找到则返回一个空字符串数组[]。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://www.test.com/search?query=name&query=my');
console.info(uriInstance.getQueryValues('query').toString()); // name,my
console.info(JSON.stringify(uriInstance.getQueryValues('abc'))); // []

```

## getSegment

```TypeScript
getSegment(): string[]
```

获取此URI中已解码的所有路径段。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | 返回此URI中已解码的所有路径段，各段前后均不含 “/”。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('http://www.test.com/path/to/image.jpg');
console.info(uriInstance.getSegment().toString()); // path,to,image.jpg

```

## normalize

```TypeScript
normalize(): URI
```

规范化此URI的路径。

> **说明：**
>
> 如果此URI是不透明的，或者其路径已经是规范形式，则返回该URI。否则将构造一个新的URI，该URI与当前URI相同，唯一的区别是其路径通过规范化当前URI的路径来计算，具体规则如下：
>
> 1.移除所有的 .（点）段。
>
> 2.如果 ..（双点）段前面有一个非 .. 段，则将这两个段一起移除。重复此步骤，直到不再适用为止。
>
> 如果路径规范化后以 ..（双点）段开头，这表明之前没有足够的非 .. 段可以移除，因此路径将以 .. 段开始。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| URI | 返回一个path被规范化后的URI对象。 |

**示例：**

```TypeScript
const uriInstance = new uri.URI('https://username:password@www.qwer.com:8080/path/path1/../path2/./path3?query=pppppp');
console.info(uriInstance.path); // /path/path1/../path2/./path3
// 规范化path后，移除所有的.（点）段,如果 ..（双点）段前面有一个非 .. 段，则将这两个段一起移除。
const uriInstance1 = uriInstance.normalize();
console.info(uriInstance1.path); // /path/path2/path3
let uri1 = new uri.URI('http://www.test.com/../../patch/path1/../path2/path3/./path4/../');
console.info(uri1.path); // /../../patch/path1/../path2/path3/./path4/../
// 如果路径规范化后以 ..（双点）段开头，这表明之前没有足够的非 .. 段可以移除，因此路径将以 .. 段开始。
let uri2 = uri1.normalize();
console.info(uri2.path); // /../../patch/path2/path3

```

## toString

```TypeScript
toString(): string
```

将URI转化为编码后的字符串。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回URI的字符串序列化。 |

**示例：**

```TypeScript
const result = new uri.URI('https://username:password@host:8080/directory/file?ab=pppppp#qwer da');
let result1 = result.toString(); // https://username:password@host:8080/directory/file?ab=pppppp#qwer%20da

```

## authority

```TypeScript
authority: string
```

获取/设置 URI 的授权组件部分（已解码）。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedAuthority

```TypeScript
encodedAuthority: string
```

获取/设置 URI 的授权部分（已编码）。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedFragment

```TypeScript
encodedFragment: string
```

获取/设置 URI 的片段部分（已编码），即 '#' 之后的所有内容。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedPath

```TypeScript
encodedPath: string
```

获取/设置 URI 的路径部分（已编码）。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedQuery

```TypeScript
encodedQuery: string
```

获取/设置 URI 的查询组件部分（已编码）。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedSSP

```TypeScript
encodedSSP: string
```

获取/设置 URI 的协议特定部分（已编码），即协议分隔符 ':' 与片段分隔符 '#' 之间的所有内容。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## encodedUserInfo

```TypeScript
encodedUserInfo: string
```

获取/设置 URI 的用户信息部分（已编码）。

**类型：** string

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## fragment

```TypeScript
fragment: string
```

获取/设置 URI 的片段部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## host

```TypeScript
host: string
```

获取 URI 的主机名部分（不含端口）。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## path

```TypeScript
path: string
```

获取/设置 URI 的路径部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## port

```TypeScript
port: string
```

获取URI的端口部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## query

```TypeScript
query: string
```

获取/设置 URI 的查询部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## scheme

```TypeScript
scheme: string
```

获取/设置 URI 的协议部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## ssp

```TypeScript
ssp: string
```

获取/设置 URI 的协议特定部分（已解码）。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

## userInfo

```TypeScript
userInfo: string
```

获取/设置 URI 的用户信息部分。

**类型：** string

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

