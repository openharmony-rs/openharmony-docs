# JSON
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供JSON基础操作。开发者可以使用本模块的功能，将对象转换成JSON格式的字符串或者将JSON格式的字符串转换成对象。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。

## JsonRecordType

type JsonRecordType = boolean | bigint | String | undefined | null | Double | Long | Record\<string, JsonRecordType> | Array\<JsonRecordType>

JsonRecordType表示`JSON.parseJsonRecord`可解析出的值类型，可用于描述JSON对象中的基础值、嵌套对象和数组。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 类型 | 说明 |
| :--- | :--- |
| boolean | JSON布尔值，对应JSON中的`true`或`false`。 |
| bigint | 大整数，根据[ParseOptions](arkts-sta-jsonx.md#parseoptions)的`bigIntMode`配置解析。 |
| String | JSON字符串值。 |
| undefined | 缺失的值，JSON对象中不存在该键时使用。 |
| null | JSON中的`null`值。 |
| Double | 浮点数值，对应JSON中含小数或超出`Long`范围的数字。 |
| Long | 整数值，对应JSON中在`Long`范围内的数字。 |
| Record\<string, JsonRecordType> | 嵌套JSON对象，键为字符串，值递归为JsonRecordType。 |
| Array\<JsonRecordType> | JSON数组，元素递归为JsonRecordType。 |

## JsonReplacer

JsonReplacer提供自定义替换接口。实现该接口的对象传入`JSON.stringify`时，会先调用`jsonReplacer`，再将其返回的`Record<String, Any>`序列化。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### jsonReplacer

jsonReplacer(): Record\<String, Any>

返回用于JSON序列化的键值记录。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型                 | 说明                 |
| -------------------- | -------------------- |
| Record\<String, Any> | 用于序列化的键值记录。 |

**示例：**

```ts
class Point implements JsonReplacer {
    x: int = 1;
    y: int = 2;

    jsonReplacer(): Record<String, Any> {
        return { "x": this.x, "y": this.y };
    }
}

const json = JSON.stringify(new Point());
console.info(json); // '{"x":1,"y":2}'
```

## JSONRename

@interface JSONRename

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

JSONRename用于标记对象字段在JSON中的名称。`JSON.stringify`序列化该字段时使用`newName`作为key，`JSON.parse`和`JSON.parseUpdate`解析对象时也按`newName`匹配输入字段。

### 属性

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

| 名称    | 类型   | 只读 | 可选 | 说明             |
| ------- | ------ | ---- | ---- | ---------------- |
| newName | string | 否   | 否   | 字段在JSON中的名称。 |

**示例：**

```ts
class UserName {
    @JSONRename({ newName: "user_name" })
    name: string = "Alice";

    @JSONRename("user_age")
    age: int = 10;
}

const json = JSON.stringify(new UserName());
console.info(json); // '{"user_name":"Alice","user_age":10}'
```

## JSONStringifyIgnore

@interface JSONStringifyIgnore

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

JSONStringifyIgnore用于标记序列化时需要忽略的对象字段。被标记字段不会出现在`JSON.stringify`输出中。

**示例：**

```ts
class SessionInfo {
    id: string = "1001";

    @JSONStringifyIgnore
    token: string = "secret";
}

const json = JSON.stringify(new SessionInfo());
console.info(json); // '{"id":"1001"}'
```

## JSONParseIgnore

@interface JSONParseIgnore

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

JSONParseIgnore用于标记解析时需要忽略的对象字段。`JSON.parseUpdate`更新对象时，被标记字段会保留原值。

**示例：**

```ts
class ParseUser {
    name: string = "before";

    @JSONParseIgnore
    role: string = "guest";
}

const user = new ParseUser();
JSON.parseUpdate<ParseUser>("{\"name\":\"after\",\"role\":\"admin\"}", user);

console.info(user.name); // "after"
console.info(user.role); // "guest"
```

## JSONStringifyGetter

@interface JSONStringifyGetter

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

JSONStringifyGetter用于标记零参数的`get`访问器。调用`JSON.stringifyWithGetters`时，被标记访问器的名称会作为JSON key，返回值会作为对应的JSON value。

**示例：**

```ts
class DisplayName {
    first: string = "Ada";
    last: string = "Lovelace";

    @JSONStringifyGetter
    get fullName(): string {
        return this.first + " " + this.last;
    }
}

const json = JSON.stringifyWithGetters(new DisplayName());
console.info(json); // '{"first":"Ada","last":"Lovelace","fullName":"Ada Lovelace"}'
```

## JsonSerializable

JsonSerializable提供了一个接口，供外部类通过重写toJSON方法来实现自定义JSON序列化行为。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### toJSON

toJSON(): string

外部类通过重写toJSON方法来实现自定义JSON序列化行为。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| string | 自定义toJSON方法转换后的返回的字符串。 |

**示例：**

```ts
class testA {
    a: string = 'Hello';
}

console.info(JSON.stringify(new testA())); // '{"a":"Hello"}'

class testB implements JsonSerializable {
    a: string = 'Hello';

    toJSON(): string {
        return "testB Hello World";
    }
}

console.info(JSON.stringify(new testB())); // '"testB Hello World"'
```

## JsonParseError

JSON的标准错误类型，当发生JSON解析或操作错误时抛出。继承自`SyntaxError`。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

### constructor

constructor(msg: string, start_offset?: int, end_offset?: int)

JsonParseError的构造函数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名        | 类型   | 必填  | 说明                           |
| ------------ | ------ | ---- | ------------------------------- |
| msg          | string | 是   | 错误信息。                       |
| start_offset | int    | 否   | 错误的起始位置，默认为undefined。 |
| end_offset   | int    | 否   | 错误的结束位置，默认为undefined。 |

**示例：**

```ts
let err = new JsonParseError("Failed to opt JSON.");
console.info(err.message); // "Failed to opt JSON. at undefined..undefined"

try {
    JSON.parse<Object>('{test}', Class.from<Object>());
} catch(e) {
    console.info(e instanceof JsonParseError); // true
    console.info(e.message); // "Unterminated string at 6 at 2..6"
}
```

## JSON

提供JSON序列化和反序列化操作的基础工具类。

**系统能力：** SystemCapability.Utils.Lang

### stringify

static stringify(d: byte): String

将byte类型的值转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填  | 说明           |
| ----- | ------ | ----- | -------------- |
| d     | byte   | 是    | byte类型的值。|

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: byte = -1;
console.info(JSON.stringify(d)); // "-1"
```

### stringify

static stringify(d: char): String

将char类型数据转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填  | 说明           |
| ----- | ---- | ---- | -------------- |
| d     | char | 是   | char类型的值。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: char = c'A';
const json = JSON.stringify(d);
console.info(json); // "A"
```

### stringify

static stringify(d: short): String

将short类型数据转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型  | 必填  | 说明            |
| ----- | ----- | ---- | --------------- |
| d     | short | 是   | short类型的值。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: short = 1000;
console.info(JSON.stringify(d)); // "1000"
```

### stringify

static stringify(d: int): String

将int类型数据转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型  | 必填 | 说明          |
| ----- | ----- | ---- | ------------- |
| d     | int   | 是   | int类型的值。|

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: int = 100000;
console.info(JSON.stringify(d)); // "100000"
```

### stringify

static stringify(d: long): String

将long类型数据转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填  | 说明            |
| ----- | ---- | ---- | -------------- |
| d     | long | 是   | long类型的值。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: long = 9223372036854775807;
console.info(JSON.stringify(d)); // "9223372036854775807"
```

### stringify

static stringify(d: float): String

将float类型数据转换成字符串。非有限值（NaN、Infinity）序列化为null。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型  | 必填  | 说明            |
| ----- | ----- | ----- | --------------- |
| d     | float | 是    | float类型的值。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: Float = 1.5f;
console.info(JSON.stringify(d)); // "1.5"
// 非有限值序列化为null
console.info(JSON.stringify(Float.NaN)); // null
console.info(JSON.stringify(Float.POSITIVE_INFINITY)); // null
```

### stringify

static stringify(d: double): String

将double类型数据转换成字符串。非有限值（NaN、Infinity）序列化为null。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填  | 说明              |
| ----- | ------ | ----- | ---------------- |
| d     | double | 是    | double类型的值。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: Double = 1.5;
console.info(JSON.stringify(d)); // "1.5"
// 非有限值序列化为null
console.info(JSON.stringify(Double.NaN)); // null
console.info(JSON.stringify(Double.POSITIVE_INFINITY)); // null
```

### stringify

static stringify(d: bigint): String

将bigint转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型    | 必填  | 说明             |
| ------ | ------ | ---- | ---------------- |
| d      | bigint | 是   | bigint类型的对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | --------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: bigint = new bigint(9223372036854775807);
console.info(JSON.stringify(d)); // "9223372036854775807"
```

### stringify

static stringify(d: boolean): String

将boolean类型数据转换为字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型    | 必填  | 说明              |
| ----- | ------- | ---- | ------------------ |
| d     | boolean | 是   | boolean类型的值。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
console.info(JSON.stringify(true)); // "true"
console.info(JSON.stringify(false)); // "false"
```

### stringify

static stringify(d: String): String

将String类型数据格式化。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型   | 必填  | 说明             |
| ----- | ------ | ---- | ---------------- |
| d     | String | 是   | String类型的对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: String = "hello";
console.info(JSON.stringify(d)); // "hello"
```

### stringify

static stringify(d: FixedArray\<byte>): String

将FixedArray\<byte>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型               | 必填  | 说明          |
| ----- | ------------------ | ----- | ------------- |
| d     | FixedArray\<byte>  | 是    | byte数组。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<byte> = [-1, 0, 127];
console.info(JSON.stringify(d)); // "[-1,0,127]"
```

### stringify

static stringify(d: FixedArray\<char>): String

将FixedArray\<char>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型              | 必填  | 说明          |
| ----- | ----------------- | ---- | ------------- |
| d     | FixedArray\<char> | 是   | char数组。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<char> = [c'A', c'B', c'C'];

const json = JSON.stringify(d);
console.info(json); // '["A","B","C"]'
```

### stringify

static stringify(d: FixedArray\<short>): String

将FixedArray\<short>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型               | 必填  | 说明           |
| ----- | -----------------  | ---- | -------------- |
| d    | FixedArray\<short>  | 是   | short数组。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<short> = [-100, 0, 1000];
console.info(JSON.stringify(d)); // "[-100,0,1000]"
```

### stringify

static stringify(d: FixedArray\<int>): String

将FixedArray\<int>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型             | 必填  | 说明         |
| ----- | -----------------| ---- | ------------ |
| d     | FixedArray\<int> | 是   | int数组。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<int> = [100, 200, 300];
console.info(JSON.stringify(d)); // "[100,200,300]"
```

### stringify

static stringify(d: FixedArray\<long>): String

将FixedArray\<long>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型              | 必填  | 说明          |
| ----- | ----------------- | ---- | ------------- |
| d     | FixedArray\<long> | 是   | long数组。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<long> = [100, 200, 300];
console.info(JSON.stringify(d)); // "[100,200,300]"
```

### stringify

static stringify(d: FixedArray\<float>): String

将FixedArray\<float>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型               | 必填  | 说明           |
| ----- | ------------------ | ---- | -------------- |
| d     | FixedArray\<float> | 是   | float数组。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<float> = [1.1f, 2.2f, 3.3f];
console.info(JSON.stringify(d)); // "[1.1,2.2,3.3]"
```

### stringify

static stringify(d: FixedArray\<double>): String

将FixedArray\<double>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型                | 必填  | 说明            |
| ----- | ------------------- | ---- | --------------- |
| d     | FixedArray\<double> | 是   | double数组。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<double> = [1.1, 2.2, 3.3];
console.info(JSON.stringify(d)); // "[1.1,2.2,3.3]"
```

### stringify

static stringify(d: FixedArray\<boolean>): String

将FixedArray\<boolean>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型                 | 必填  | 说明             |
| ----- | -------------------- | ---- | ---------------- |
| d     | FixedArray\<boolean> | 是   | boolean数组。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<boolean> = [true, false, true];
console.info(JSON.stringify(d)); // "[true,false,true]"
```

### stringify

static stringify(d: Array\<Number>): String

将Array\<Number>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型            | 必填  | 说明            |
| ----- | --------------- | ---- | --------------- |
| d     | Array\<Number>  | 是   | Number数组。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: Array<Number> = [1.1, 2.2, 3.3];
console.info(JSON.stringify(d)); // "[1.1,2.2,3.3]"
```

### stringify

static stringify(d: ArrayLike\<Number>): String

将ArrayLike\<Number>转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型                | 必填  | 说明            |
| ----- | ------------------- | ---- | --------------- |
| d     | ArrayLike\<Number>  | 是   | Number类数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: ArrayLike<Number> = Int8Array.of(1, 2, 3);
console.info(JSON.stringify(d)); // '{"0":1,"1":2,"2":3}'
```

### stringify

static stringify(obj: JsonReplacer): String

将实现了`JsonReplacer`接口的对象转换为JSON字符串。先调用对象的`jsonReplacer`方法获取`Record<String, Any>`，再将其序列化。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| obj | [JsonReplacer](#jsonreplacer) | 是 | 实现了JsonReplacer接口的对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| String | JSON格式的字符串。 |

**示例：**

```ts
class Point implements JsonReplacer {
    x: int = 1;
    y: int = 2;

    jsonReplacer(): Record<String, Any> {
        return { "x": this.x, "y": this.y };
    }
}

const json = JSON.stringify(new Point());
console.info(json); // '{"x":1,"y":2}'
```

### stringify

static stringify(obj: Any): String

将ArkTS-Sta对象、数组和基本数据类型等数据转换为字符串。传入`undefined`时返回空字符串；传入`Function`时返回空字符串；`float`和`double`为非有限值时序列化为`null`；检测到循环引用时抛出`TypeError`。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型  | 必填  | 说明          |
| ----- | ----- | ----- | ------------- |
| obj   | Any   | 是    | Any类型的对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
class TestNode {
    value: String;

    constructor(value: String) {
        this.value = value;
    }
}

const nodeA = new TestNode('A');
const json = JSON.stringify(nodeA);
console.info(json); // '{"value":"A"}'
```

### stringify

static stringify(obj: Any, replacer: ((key: string, value: Any) => Any) | undefined | null, space?: string | int): string

将ArkTS-Sta对象、数组和基本数据类型等数据转换成字符串，并添加条件过滤。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                        | 必填 | 说明                     |
| -------- | --------------------------- | --- | ------------------------- |
| obj      | Any                         | 是  | 一个Any类型的对象。         |
| replacer | function \|undefined \|null | 否  | 过滤方法，默认为undefined。 |
| space    | string \| int               | 否  | 格式化参数，默认为undefined。|

**返回值：**

| 类型   | 说明            |
| ------ | --------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
class TestNode {
    value: String;

    constructor(value: String) {
        this.value = value;
    }
}

function toStringReplacer(key: string, value: Any): Any {
    if (key == "value") {
        return 'B';
    }

    return value;
}

const nodeA = new TestNode('A');
const json = JSON.stringify(nodeA, toStringReplacer, 0);
console.info(json); // '{"value":"B"}'
```

### stringify

static stringify(obj: Any, replacer: FixedArray\<double | string>, space?: int | string): string

将ArkTS-Sta对象、数组、基本数据类型等转换成字符串，并添加条件过滤。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                          | 必填  | 说明                     |
| -------- | ----------------------------- | ---- | ------------------------- |
| obj      | Any                           | 是   | 要转换的对象。              |
| replacer | FixedArray\<double \| string> | 是   | 过滤器。                   |
| space    | int \| string                 | 否   | 格式化缩进，默认为undefined。|

**返回值：**

| 类型   | 说明            |
| ------ | --------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
class TestNode {
    value: String;
    name: String = 'B';

    constructor(value: String) {
        this.value = value;
    }
}

const nodeA = new TestNode('A');
let arr: FixedArray<double | string> = ['name'];
const json = JSON.stringify(nodeA, arr, 0);
console.info(json); // '{"name":"B"}'
```

### stringify

static stringify(obj: Any, replacer: Array\<double | string> | Array\<string> | Array\<double>, space?: int | string): string

将ArkTS-Sta对象、数组和基本数据类型等转换成字符串，并添加条件过滤。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名    | 类型                     | 必填  | 说明                       |
| -------- | ------------------------ | ---- | -------------------------- |
| obj      | Any                                                | 是   | 要转换的对象。              |
| replacer | Array\<double \| string> \| Array\<string> \| Array\<double> | 是   | 过滤器。                    |
| space    | int \| string                                      | 否   | 格式化缩进，默认为undefined。 |

**返回值：**

| 类型   | 说明            |
| ------ | --------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
class TestNode {
    value: String;
    name: String = 'B';

    constructor(value: String) {
        this.value = value;
    }
}

const nodeA = new TestNode('A');
let arr: Array<double | string> = ['name'];
const json = JSON.stringify(nodeA, arr, 0);
console.info(json); // '{"name":"B"}'
```

### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElementSerializable): string

将jsonx.JsonElementSerializable对象转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                                 | 必填  | 说明                         |
| ----- | ---------------------------------------------------- | ----- | ---------------------------- |
| d     | [jsonx.JsonElementSerializable](arkts-sta-jsonx.md#jsonelementserializable) | 是    | JsonElementSerializable对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
class JsonElementClass implements jsonx.JsonElementSerializable {
    public toJSON(): jsonx.JsonElement {
        return jsonx.JsonElement.createString("test");
    }
}

let d: JsonElementClass = new JsonElementClass();
const json = JSON.stringifyJsonElement(d);
console.info(json); // '"test"'
```

### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElementSerializable, replacer?: (double | string)[], space?: int | string): string

将jsonx.JsonElementSerializable对象转换成字符串，支持传入过滤条件和格式化参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名    | 类型                                                 | 必填  | 说明                                   |
| -------- | ---------------------------------------------------- | ---- | --------------------------------------- |
| d        | [jsonx.JsonElementSerializable](arkts-sta-jsonx.md#jsonelementserializable) | 是   | JsonElementSerializable对象。            |
| replacer | (double \| string)[]                                 | 否   | double\|string类型的数组，默认为undefined。|
| space    | int \| string                                        | 否   | int\|string类型的对象，默认为undefined。   |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
class JsonElementClass implements jsonx.JsonElementSerializable {
    public toJSON(): jsonx.JsonElement {
        return jsonx.JsonElement.createString("test");
    }
}

let d: JsonElementClass = new JsonElementClass();
const json = JSON.stringifyJsonElement(d, undefined, 0);
console.info(json); // '"test"'
```

### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElement): string

将jsonx.JsonElement对象转换成字符串。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型                                       | 必填  | 说明            |
| ----- | ------------------------------------------ | ---- | ---------------- |
| d     | [jsonx.JsonElement](arkts-sta-jsonx.md#jsonelement)   | 是   | JsonElement对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
let d: jsonx.JsonElement = jsonx.JsonElement.createString("test");
const json = JSON.stringifyJsonElement(d);
console.info(json); // '"test"'
```

### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElement, replacer?: (double | string)[], space?: int | string): string

将jsonx.JsonElement对象转换成字符串，支持过滤条件和格式化参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名    | 类型                                            | 必填  | 说明                                    |
| -------- | ----------------------------------------------- | ---- | ---------------------------------------- |
| d        | [jsonx.JsonElement](arkts-sta-jsonx.md#jsonelement)        | 是   | JsonElement对象。                         |
| replacer | (double \| string)[]                            | 否   | double\|string类型的数组，默认为undefined。|
| space    | int \| string                                   | 否   | int\|string类型的对象，默认为undefined。   |

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| string | 转换后的字符串。 |

**示例：**

```ts
const map = new Map<string, jsonx.JsonElement>();
map.set("name", jsonx.JsonElement.createString("Tom"));
map.set("age", jsonx.JsonElement.createInteger(30));
const objectElem = jsonx.JsonElement.createObject(map);

const json = JSON.stringifyJsonElement(objectElem, undefined, 0);
console.info(json); // '{"name":"Tom","age":30}'
```

### stringifyWithGetters

static stringifyWithGetters(obj: Any): String

将ArkTS-Sta对象转换成JSON字符串，同时调用使用`@JSONStringifyGetter`注解标记的`get`方法，并将其返回值包含在输出中。`get`方法名作为JSON的key，返回值作为对应的value。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

> **注意：** 
>
> `@JSONStringifyGetter`注解仅对`get`方法生效。普通方法即使标注了此注解也不会被调用。未标注`@JSONStringifyGetter`的`get`方法同样不会包含在输出中。父类中标注的`get`方法也会被包含。

**参数：**

| 参数名 | 类型 | 必填  | 说明          |
| ----- | ---- | ----- | ------------- |
| obj   | Any  | 是    | Any类型的对象。|

**返回值：**

| 类型   | 说明                                       |
| ------ | ------------------------------------------ |
| String | JSON格式的字符串，包含注解get方法的返回值。|

**示例：**

```ts
class Person {
    private _firstName: string;
    private _lastName: string;

    constructor(firstName: string, lastName: string) {
        this._firstName = firstName;
        this._lastName = lastName;
    }

    @JSONStringifyGetter
    get firstName(): string {
        return this._firstName;
    }

    @JSONStringifyGetter
    get lastName(): string {
        return this._lastName;
    }

    @JSONStringifyGetter
    get fullName(): string {
        return this._firstName + " " + this._lastName;
    }
}

const p = new Person("John", "Doe");
const json = JSON.stringifyWithGetters(p);
console.info(json); // '{"fullName":"John Doe","lastName":"Doe","firstName":"John"}'
```

### stringifyWithGetters

static stringifyWithGetters(obj: Any, replacer: ((key: string, value: Any) => Any) | undefined | null, space?: int | string): string

将ArkTS-Sta对象转换成JSON字符串，同时调用`@JSONStringifyGetter`注解标记的`get`方法，支持自定义过滤器和格式化参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名    | 类型                        | 必填 | 说明                     |
| -------- | --------------------------- | --- | ------------------------- |
| obj      | Any                         | 是  | 一个Any类型的对象。         |
| replacer | function \|undefined \|null | 否  | 过滤方法，默认为undefined。 |
| space    | int \| string               | 否  | 格式化参数，默认为undefined。|

**返回值：**

| 类型   | 说明                                       |
| ------ | ------------------------------------------ |
| string | JSON格式的字符串，包含注解get方法的返回值。|

**示例：**

```ts
class Person {
    private _firstName: string;
    private _lastName: string;

    constructor(firstName: string, lastName: string) {
        this._firstName = firstName;
        this._lastName = lastName;
    }

    @JSONStringifyGetter
    get firstName(): string {
        return this._firstName;
    }

    @JSONStringifyGetter
    get lastName(): string {
        return this._lastName;
    }

    @JSONStringifyGetter
    get fullName(): string {
        return this._firstName + " " + this._lastName;
    }
}

function replacer(key: string, value: Any): Any {
    if (key == "fullName") {
        return undefined;
    }
    return value;
}

const p = new Person("John", "Doe");
const json = JSON.stringifyWithGetters(p, replacer, 2);
// replacer过滤了fullName，space=2表示缩进2个空格
// {
//   "lastName": "Doe",
//   "firstName": "John"
// }
console.info(json);
```

### stringifyWithGetters

static stringifyWithGetters(obj: Any, replacer: Array\<double | string> | Array\<string> | Array\<double>, space?: int | string): string

将ArkTS-Sta对象转换成JSON字符串，同时调用`@JSONStringifyGetter`注解标记的`get`方法，支持数组过滤器和格式化参数。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名    | 类型                                                           | 必填  | 说明                       |
| -------- | -------------------------------------------------------------- | ---- | -------------------------- |
| obj      | Any                                                            | 是   | 要转换的对象。              |
| replacer | Array\<double \| string> \| Array\<string> \| Array\<double>  | 是   | 过滤器数组。                |
| space    | int \| string                                                  | 否   | 格式化缩进，默认为undefined。|

**返回值：**

| 类型   | 说明                                       |
| ------ | ------------------------------------------ |
| string | JSON格式的字符串，包含注解get方法的返回值。|

**示例：**

```ts
class Person {
    private _firstName: string;
    private _lastName: string;

    constructor(firstName: string, lastName: string) {
        this._firstName = firstName;
        this._lastName = lastName;
    }

    @JSONStringifyGetter
    get firstName(): string {
        return this._firstName;
    }

    @JSONStringifyGetter
    get lastName(): string {
        return this._lastName;
    }

    @JSONStringifyGetter
    get fullName(): string {
        return this._firstName + " " + this._lastName;
    }
}

const p = new Person("John", "Doe");
let arr: Array<string> = ["firstName", "fullName"];
const json = JSON.stringifyWithGetters(p, arr, 0);
console.info(json); // '{"fullName":"John Doe","firstName":"John"}'
```

### parse

static parse\<T = Any>(json: string, type: Class): T | null | undefined

将JSON字符串转换成指定类型的对象。通过Class传入目标类型。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填  | 说明             |
| ------ | ------ | ---- | ----------------- |
| json   | string | 是   | JSON格式的字符串。 |
| type   | Class  | 是   | 目标类型。         |

**返回值：**

| 类型  | 说明                                                   |
| ----- | ----------------------------------------------------- |
| T \| null \| undefined  | 返回符合条件的具体对象，开发者可以访问其成员变量和成员函数。|

**示例：**

```ts
class A {
    intValue: Int = 0;
}

let text: String = `{\"intValue\":12}`;
let typ: Class = Class.from<A>();
let result = JSON.parse<A>(text, typ) as A;
console.info(result.intValue); // 12
```

### parse

static parse\<T>(json: string, reviver: ((key: string, value: Any) => Any) | undefined, type: Class, options?: jsonx.ParseOptions): T | null | undefined

将JSON字符串转换成符合条件的具体对象，支持自定义过滤器和解析参数。通过Class传入目标类型。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名   | 类型                                       | 必填  | 说明                       |
| ------- | ------------------------------------------ | ---- | --------------------------- |
| json    | string                                     | 是   | JSON格式的字符串。            |
| reviver | function                                   | 是   | 过滤器。                      |
| type    | Class                                      | 是   | 目标类型。                    |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型  | 说明                                                 |
| ---- | ----------------------------------------------------- |
| T \| null \| undefined  | 返回符合条件的具体对象，开发者可以访问其成员变量和成员函数。|

**示例：**

```ts
class A {
    intValue: Int = 0;
}

let text: string = `{\"intValue\":12}`;
let typ: Class = Class.from<A>();
let opt: jsonx.ParseOptions = {bigIntMode: jsonx.BigIntMode.DEFAULT} as jsonx.ParseOptions;
let result = JSON.parse<A>(text, undefined, typ, opt) as A;
console.info(result.intValue); // 12
```

### parseUpdate

static parseUpdate\<T>(json: string, instance: T): T

解析JSON字符串并将结果填充到已有实例的字段中。与parse\<T>(json, type)不同，此方法不要求目标类具有默认构造函数。JSON中不存在的key对应的字段保留实例上的当前值（合并语义）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**数组字段处理：**

- **FixedArray字段**：支持解析。运行时可以获取元素类型，JSON数组会被正确反序列化为对应的FixedArray。
- **Array字段**：不支持解析。由于类型擦除，运行时无法获取Array的元素类型，解析时会抛出Error。如果JSON中不包含该字段的key，Array字段会保留原值。

```ts
class Scores {
    label: string = "";
    fixed: FixedArray<int> = [];    // 支持解析
    resizable: double[] = [];       // 不支持解析，解析时抛出Error
}

const obj = new Scores();
obj.resizable = [99, 100];

// FixedArray字段正常解析
JSON.parseUpdate<Scores>('{"label":"ok","fixed":[1,2,3]}', obj);
console.info(obj.fixed.length); // 3
console.info(obj.resizable[0]); // 99（JSON中无此key，保留原值）

// Array字段解析会抛出Error
try {
    JSON.parseUpdate<Scores>('{"resizable":[10,20]}', obj);
} catch (e) {
    console.info(e.message); // "std.core.Array is expected, but get std.core.JSONArray"
}
```

**参数：**

| 参数名    | 类型   | 必填  | 说明                       |
| -------- | ------ | ---- | -------------------------- |
| json     | string | 是   | JSON格式的字符串。           |
| instance | T      | 是   | 要填充字段的已有实例对象。    |

**返回值：**

| 类型  | 说明                    |
| ---- | ----------------------- |
| T    | 填充完成后的同一实例对象。 |

**示例：**

```ts
class Config {
    host: string = "localhost";
    port: int = 8080;
    debug: boolean = false;
}

const cfg = new Config();
cfg.port = 9090;
cfg.debug = true;

JSON.parseUpdate<Config>('{"host":"example.com"}', cfg);

console.info(cfg.host);  // "example.com"
console.info(cfg.port);  // 9090（保留原值）
console.info(cfg.debug); // true（保留原值）
```

**嵌套对象示例：**

嵌套对象会递归填充，内部对象的引用保持不变。JSON中缺失的嵌套字段保留原值。

```ts
class Size {
    width: double = 0;
    height: double = 0;
}

class Widget {
    name: string = "";
    size: Size = new Size();
}

const w = new Widget();
JSON.parseUpdate<Widget>('{"name":"button","size":{"width":100,"height":50}}', w);

console.info(w.name);        // "button"
console.info(w.size.width);  // 100
console.info(w.size.height); // 50
```

**深层嵌套合并示例：**

```ts
class Address {
    city: string = "";
    zip: string = "";
}

class Department {
    name: string = "";
    address: Address = new Address();
}

class Employee {
    name: string = "";
    age: int = 0;
    dept: Department = new Department();
}

const emp = new Employee();
emp.name = "Bob";
emp.age = 40;
emp.dept.name = "Sales";
emp.dept.address.city = "Munich";
emp.dept.address.zip = "80331";

JSON.parseUpdate<Employee>('{"dept":{"name":"Engineering"}}', emp);

console.info(emp.name);              // "Bob"（保留原值）
console.info(emp.age);               // 40（保留原值）
console.info(emp.dept.name);         // "Engineering"
console.info(emp.dept.address.city); // "Munich"（保留原值）
console.info(emp.dept.address.zip);  // "80331"（保留原值）
```

### parseUpdate

static parseUpdate\<T>(json: string, reviver: ((key: string, value: Any) => Any) | undefined, instance: T, options?: jsonx.ParseOptions): T

解析JSON字符串并将结果填充到已有实例的字段中，支持可选的reviver函数和解析参数。与parse\<T>(json, type)不同，此方法不要求目标类具有默认构造函数。JSON中不存在的key对应的字段保留实例上的当前值（合并语义）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名    | 类型                                      | 必填  | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| json     | string                                    | 是   | JSON格式的字符串。           |
| reviver  | function \| undefined                     | 是   | 自定义值转换函数，或undefined。|
| instance | T                                         | 是   | 要填充字段的已有实例对象。     |
| options  | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions) | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型  | 说明                    |
| ---- | ----------------------- |
| T    | 填充完成后的同一实例对象。 |

**示例：**

```ts
class Point {
    x: double = 0;
    y: double = 0;
}

const pt = new Point();

const reviver = (key: string, val: Any): Any => {
    if (key == "x") {
        return (val as Double) * 10;
    }
    return val;
};

JSON.parseUpdate<Point>('{"x":3,"y":5}', reviver, pt);

console.info(pt.x); // 30
console.info(pt.y); // 5
```

**嵌套对象与reviver示例：**

内部对象不需要默认构造函数也可以更新，引用保持不变。

```ts
class Engine {
    model: string = "";

    constructor(model: string) {
        this.model = model;
    }
}

class Car {
    brand: string = "";
    engine: Engine = new Engine("default");
    year: int = 0;

    constructor(brand: string, engine: Engine, year: int) {
        this.brand = brand;
        this.engine = engine;
        this.year = year;
    }
}

const engine = new Engine("V6");
const car = new Car("Audi", engine, 2020);

const reviver = (key: string, val: Any): Any => { return val; };

JSON.parseUpdate<Car>(
    '{"brand":"BMW","engine":{"model":"V8"},"year":2024}', reviver, car
);

console.info(car.brand);        // "BMW"
console.info(car.year);         // 2024
console.info(car.engine.model); // "V8"
console.info(car.engine === engine); // true（引用保持不变）
```

### parseJsonElement

static parseJsonElement(text: string, options?: jsonx.ParseOptions): jsonx.JsonElement

将json字符串转换成JsonElement类型的实例。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型   | 必填  | 说明             |
| ------ | ------ | ----- | ---------------- |
| text   | string | 是    | json格式的字符串。 |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型                                     | 说明                             |
| ---------------------------------------- | --------------------------------- |
| [jsonx.JsonElement](arkts-sta-jsonx.md#jsonelement) | JsonElement对象，支持JSON相关操作。 |

**示例：**

```ts
let text: String = `{\"numberValue\":123456}`;
let opt: jsonx.ParseOptions = {bigIntMode: jsonx.BigIntMode.ALWAYS_PARSE_AS_BIGINT} as jsonx.ParseOptions;
let result: jsonx.JsonElement = JSON.parseJsonElement(text, opt);
console.info(result.getBigInt("numberValue")); // 123456
try {
    result.getLong("numberValue");
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Expected long, but element stores different value type. 
}

text = `{\"numberValue\":9223372036854775807}`;
opt =  { bigIntMode: jsonx.BigIntMode.PARSE_AS_BIGINT } as jsonx.ParseOptions;
result = JSON.parseJsonElement(text, opt);
console.info(result.getLong("numberValue")); // 9223372036854775807

text = `{\"numberValue\":9223372036854775808}`;
result = JSON.parseJsonElement(text, opt);
console.info(result.getBigInt("numberValue")); // 9223372036854775808
try {
    result.getLong("numberValue");
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Expected long, but element stores different value type. 
}

opt =  { bigIntMode: jsonx.BigIntMode.DEFAULT } as jsonx.ParseOptions;
try {
    result = JSON.parseJsonElement(text, opt);
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Value exceeds integer limits
}
```

### parseJsonElement

static parseJsonElement(text: string, reviver: (key: string, value: jsonx.JsonElement) => jsonx.JsonElement, options?: jsonx.ParseOptions): jsonx.JsonElement

将JSON字符串转换成JsonElement类型的实例，支持自定义过滤方法。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名  | 类型      | 必填  | 说明             |
| ------- | -------- | ---- | ---------------- |
| text    | string   | 是   | json格式的字符串。 |
| reviver | function | 是   | 过滤方法。        |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型                                      | 说明                             |
| ----------------------------------------- | --------------------------------- |
| [jsonx.JsonElement](arkts-sta-jsonx.md#jsonelement)  | JsonElement对象，支持JSON相关操作。 |

**示例：**

```ts
const reviver = (key: string, value: jsonx.JsonElement): jsonx.JsonElement => {
    return value;
};

let text: String = `{\"numberValue\":123456}`;
let opt: jsonx.ParseOptions = { bigIntMode: jsonx.BigIntMode.ALWAYS_PARSE_AS_BIGINT } as jsonx.ParseOptions;
let result: jsonx.JsonElement = JSON.parseJsonElement(text, reviver, opt);
console.info(result.getBigInt("numberValue")); // 123456
try {
    result.getLong("numberValue");
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Expected long, but element stores different value type. 
}

text = `{\"numberValue\":-9223372036854775807}`;
opt =  { bigIntMode: jsonx.BigIntMode.PARSE_AS_BIGINT } as jsonx.ParseOptions;
result = JSON.parseJsonElement(text, reviver, opt);
console.info(result.getLong("numberValue")); // -9223372036854775807

text = `{\"numberValue\":9223372036854775808}`;
result = JSON.parseJsonElement(text, reviver, opt);
console.info(result.getBigInt("numberValue")); // 9223372036854775808
try {
    result.getLong("numberValue");
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Expected long, but element stores different value type. 
}

opt =  { bigIntMode: jsonx.BigIntMode.DEFAULT } as jsonx.ParseOptions;
try {
    result = JSON.parseJsonElement(text, reviver, opt);
} catch (error) {
    const err: Error = error as Error;
    console.info(`${err.message}`); // Value exceeds integer limits
}
```

### parseJsonRecord

static parseJsonRecord(text: string, options?: jsonx.ParseOptions): Record\<string, JsonRecordType>

将JSON对象字符串解析为`Record<string, JsonRecordType>`。JSON根节点必须为对象（以`{`开头）。

**系统能力：** SystemCapability.Utils.Lang

**ArkTS-Sta起始版本：** 26.0.0

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | JSON格式的字符串。 |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions) | 否 | 解析操作参数，默认为undefined。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record\<string, [JsonRecordType](#jsonrecordtype)> | 解析得到的Record对象。 |

**示例：**

```ts
let text = '{"name":"ArkTS","version":24}';
let record = JSON.parseJsonRecord(text);
console.info(record["name"]); // "ArkTS"
console.info(record["version"]); // 24
```
