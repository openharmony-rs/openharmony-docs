# JSON

本模块提供JSON基础操作。开发者可以使用本模块的功能，将对象转换成JSON格式的字符串或者将JSON格式的字符串转换成对象。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 20开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## JSONValue

JSONValue是以下所有JSON对象的基类。

| 名称         | 说明             |
| ---------- | -------------- |
| JSONObject | 一个JSON对象。      |
| JSONArray  | 一个JSON数组。      |
| JSONNumber | 一个JSON数字。      |
| JSONString | 一个JSON字符串。    |
| JSONTrue   | 一个JSON值为true。  |
| JSONFalse  | 一个JSON值为false。 |
| JSONNull   | 一个JSON值为null。  |


## JSONObject

JSON类型的对象。


### 属性

| 名称        | 类型                               | 只读  | 可选  | 说明             |
| ---------- | ---------------------------------- | ---- | ---- | ---------------- |
| keys_      | Array\<[JSONString](#jsonstring)>  | 否   | 否    | key值数组。       |
| values     | Array\<[JSONValue](#jsonvalue)>    | 否   | 否    | value值数组。     |
| START_CHAR | Char                               | 是   | 否    | 起始字符。        |
| END_CHAR   | Char                               | 是   | 否    | 结束字符。        |
| SEPARATOR  | Char                               | 是   | 否    | 键值间分隔字符。  |
| DELIMETER  | Char                               | 是   | 否    | 键值对间分隔字符。|
| EMPTY      | Char                               | 是   | 否    | 空对象字符串。    |



### getFields

getFields(): Map\<String, JSONValue>

该方法获取JSON对象的元素。

**返回值：**

| 类型                                            | 说明              |
| ----------------------------------------------- | ----------------- |
| Map\<String, [JSONValue](#jsonvalue)>           | 一个map类型的对象。 |

**示例：**

```ts
let json: String = `{\"intValue\":12}`;
try {
    let jsonObj: JSONObject = JSONParser.parse(json) as JSONObject;
    let fields: Map<String, JSONValue> = jsonObj.getFields();
    console.info(fields.get("intValue")); // 12
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

### toString

toString(): String

该方法将当前对象转换成JSON字符串。

**返回值：**

| 类型    | 说明             |
| ------ | ---------------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
let json: String = `{\"intValue\":12}`;
try {
    let jsonObj: JSONObject = JSONParser.parse(json) as JSONObject;
    let str: String = jsonObj.toString();
    console.info(str); // {intValue:12}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JSONArray

JSON格式的数组。

### 属性

| 名称        | 类型                             | 只读  | 可选  | 说明             |
| ---------- | -------------------------------- | ---- | ----- | -----------------|
| values     | Array\<[JSONValue](#jsonvalue)>  | 否   | 否    | JSONValue数组。   |
| START_CHAR | Char                             | 是   | 否    | 起始字符。        |
| END_CHAR   | Char                             | 是   | 否    | 结束字符。        |
| SEPARATOR  | Char                             | 是   | 否    | 间隔字符。        |


### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
let json: String = `[\"A\", \"B\"]`;
try {
    let jsonArr: JSONArray = JSONParser.parse(json) as JSONArray;
    let str: String = jsonArr.toString();
    console.info(str); // [A,B]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JSONNumber

JSON中表示数字的数据类型。

### 属性

| 名称         | 类型   | 只读  | 可选  | 说明             |
| ----------- | ------ | ----- | ----- | --------------- |
| value       | Double | 否    | 否    | Double值。      |
| bigintValue | bigint | 否    | 否    | bigint值。      |


### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
let json: String = "1.0";
try {
    let jsonNum: JSONNumber = JSONParser.parse(json) as JSONNumber;
    let str: String = jsonNum.toString();
    console.info(str); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JSONString

JSON格式的字符串。

### 属性

| 名称        | 类型   | 只读  | 可选  | 说明             |
| ---------- | ------ | ---- | ----- | ---------------- |
| value      | String | 否   | 否    | String值。       |
| START_CHAR | Char   | 是   | 否    | 起始字符。        |
| END_CHAR   | Char   | 是   | 否    | 结束字符。        |

### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型    | 说明              |
| ------ | ----------------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
let json: String = "A";
try {
    let jsonStr: JSONString = new JSONString();
    jsonStr.value = json;
    let str: String = jsonStr.toString();
    console.info(str); // A
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JSONTrue

JSON布尔类型，表示值为true。

### 属性

| 名称        | 类型   | 只读  | 可选  | 说明                           |
| ---------- | ------ | ---- | ----- | ------------------------------- |
| value      | String | 是   | 否    | 字符串类型的布尔值，默认为 "true"。|
| START_CHAR | Char   | 是   | 否    | 起始字符。                       |

### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型    | 说明            |
| ------ | ---------------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
try {
    let jsonTrue: JSONTrue = new JSONTrue();
    let str: String = jsonTrue.toString();
    console.info(str); // true
}catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


## JSONFalse

JSON布尔类型，表示值为false。

### 属性

| 名称        | 类型   | 只读  | 可选  | 说明                            |
| ---------- | ------ | ----- | ---- | ------------------------------- |
| value      | String | 是   | 否    | 字符串类型的布尔值，默认为"false"。|
| START_CHAR | Char   | 是   | 否    | 起始字符。                       |

### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
try {
    let jsonFalse: JSONFalse = new JSONFalse();
    let str: String = jsonFalse.toString();
    console.info(str); // false
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JSONNull

JSON类型，表示值为null。

### 属性

| 名称        | 类型   | 只读  | 可选  | 说明             |
| ---------- | ------ | ---- | ----- | ---------------- |
| value      | String | 是   | 否    | 默认为"null"。    |
| START_CHAR | Char   | 是   | 否    | 起始字符。        |


### toString

toString(): String

转换成JSON格式的字符串。

**返回值：**

| 类型     | 说明          |
| ------ | ----------- |
| String | JSON格式的字符串。 |

**示例：**

```ts
try {
    let jsonNull: JSONNull = new JSONNull();
    let str: String = jsonNull.toString();
    console.info(str); // null
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

## JsonSerializable

JsonSerializable提供了一个接口，供外部类通过重写toJSON方法来实现自定义JSON序列化行为。

### toJSON

toJSON(): string

外部类通过重写toJSON方法来实现自定义JSON序列化行为。

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| string | 自定义toJSON方法转换后的返回的字符串。 |

**示例：**

```ts
class testA {
    a: string = 'Hello'
}

console.info(JSON.stringify(new testA())) // {"a":"Hello"}

class testB implements JsonSerializable {
    a: string = 'Hello'

    toJSON(): string {
        return "testB Hello World"
    }
}

console.info(JSON.stringify(new testB())) // "testB Hello World"
```

## JsonParseError

JSON的标准错误类型，当发生JSON解析或操作错误时抛出。

### constructor

constructor(msg: String, start_offset?: Int, end_offset?: Int)

JsonParseError的构造函数。

**参数：**

| 参数名        | 类型   | 必填  | 说明                           |
| ------------ | ------ | ---- | ------------------------------- |
| msg          | String | 是   | 错误信息。                       |
| start_offset | Int    | 否   | 错误的起始位置，默认为undefined。 |
| end_offset   | Int    | 否   | 错误的结束位置，默认为undefined。 |

**示例：**

```ts
try {
    let typ: Type = Type.of(new Object());
    const json = JSON.parse<Object>("[1, 2, 3]", typ) as Object;
} catch (error) {
    throw new JsonParseError("Failed to opt JSON.");
}
```


## JSON

提供JSON序列化和反序列化操作的基础工具类。

### stringify
所有以"stringify"开头的方法均是stringify的别名，推荐直接调用stringify方法，举例如下。

**示例1：**
```ts
try {
    let d: Byte = 1;
    const json = JSON.stringify(d); // stringifyByte(d: Byte)
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```

**示例2：**
```ts
try {
    let d: Short = 1;
    const json = JSON.stringify(d); // stringifyShort(d: Short)
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyByte

static stringifyByte(d: Byte): String

将Byte类型的值转换成字符串。

**参数：**

| 参数名 | 类型   | 必填  | 说明           |
| ----- | ------ | ----- | -------------- |
| d     | Byte   | 是    | Byte类型的对象。|

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Byte = 1;
    const json = JSON.stringifyByte(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyShort

static stringifyShort(d: Short): String

将Short类型数据转换成字符串。

**参数：**

| 参数名 | 类型  | 必填  | 说明            |
| ----- | ----- | ---- | --------------- |
| d     | Short | 是   | Short类型的对象。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |


**示例：**

```ts
try {
    let d: Short = 1;
    const json = JSON.stringifyShort(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyInt

static stringifyInt(d: Int): String

将Int类型数据转换成字符串。

**参数：**

| 参数名 | 类型  | 必填 | 说明          |
| ----- | ----- | ---- | ------------- |
| d     | Int   | 是   | Int类型的对象。|

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Int = 1;
    const json = JSON.stringifyInt(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyLong

static stringifyLong(d: Long): String

将Long类型数据转换成字符串。

**参数：**

| 参数名 | 类型 | 必填 | 说明            |
| ----- | ---- | ---- | -------------- |
| d     | Long | 是   | Long类型的对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Long = 1;
    const json = JSON.stringifyLong(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyFloat

static stringifyFloat(d: Float): String

将Float类型数据转换成字符串。

**参数：**

| 参数名 | 类型  | 必填  | 说明            |
| ----- | ----- | ----- | --------------- |
| d     | Float | 是    | Float类型的对象。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Float = 1.0;
    const json = JSON.stringifyFloat(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyDouble

static stringifyDouble(d: Double): String

将Double类型数据转换成字符串。

**参数：**

| 参数名 | 类型   | 必填  | 说明              |
| ----- | ------ | ----- | ---------------- |
| d     | Double | 是    | Double类型的对象。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Double = 1.0;
    const json = JSON.stringifyDouble(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyBigint

static stringifyBigint(d: bigint): String

将bigint转换为字符串。

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
try {
    let d: bigint = new bigint(1.0);
    const json = JSON.stringifyBigint(d);
    console.info(json); // 1
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyChar

static stringifyChar(d: Char): String

将Char类型数据转换成字符串。

**参数：**

| 参数名 | 类型 | 必填  | 说明           |
| ----- | ---- | ---- | -------------- |
| d     | Char | 是   | Char类型的对象。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Char = c'A';
    const json = JSON.stringifyChar(d);
    console.info(json); // "A"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyBoolean

static stringifyBoolean(d: Boolean): String

将Boolean类型数据转换为字符串。

**参数：**

| 参数名 | 类型    | 必填  | 说明              |
| ----- | ------- | ---- | ------------------ |
| d     | Boolean | 是   | Boolean类型的对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: Boolean = true;
    const json = JSON.stringifyBoolean(d);
    console.info(json); // true
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyString

static stringifyString(d: String): String

将String类型数据格式化。

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
try {
    let d: String = "{value: A}";
    const json = JSON.stringifyString(d);
    console.info(json); // "{value: A}"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyAnyObj

static stringifyAnyObj(obj: Any): String

将ArkTS-Sta对象、数组和基本数据类型等数据转换为字符串。

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

try {
    const json = JSON.stringifyAnyObj(nodeA);
    console.info(json); // {"value":"A"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyObjValue

static stringifyObjValue(obj: Any,
                replacer: ((key: String, value: Any) => Any) | undefined | null,
                space?: String | Int): String

将ArkTS-Sta对象、数组和基本数据类型等数据转换成字符串，并添加条件过滤。

**参数：**

| 参数名    | 类型                        | 必填 | 说明                     |
| -------- | --------------------------- | --- | ------------------------- |
| obj      | Any                         | 是  | 一个Any类型的对象。         |
| replacer | function \|undefined \|null | 否  | 过滤方法，默认为undefined。 |
| space    | String \| Int               | 否  | 格式化参数，默认为undefined。|

**返回值：**

| 类型     | 说明    |
| ------ | -------- |
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

function toStringReplacer(key: String, value: Any): Any {
    if (key == "value") {
        return 'B';
    }

    return value;
}

try {
    const json = JSON.stringifyObjValue(nodeA, toStringReplacer, 0);
    console.info(json); // {"value":"B"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyDoubleStringFixedArray

static stringifyDoubleStringFixedArray(obj: Any, replacer: FixedArray\<Double | String>, space?: Int | String): String

将ArkTS-Sta对象、数组、基本数据类型等转换成字符串，并添加条件过滤。

**参数：**

| 参数名    | 类型                          | 必填  | 说明                     |
| -------- | ----------------------------- | ---- | ------------------------- |
| obj      | Any                           | 是   | 要转换的对象。              |
| replacer | FixedArray\<Double \| String> | 是   | 过滤器。                   |
| space    | String \| Int                 | 否   | 格式化缩进，默认为undefined。|

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

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

let arr: FixedArray<Double | String> = ['name'];

try {
    const json = JSON.stringifyDoubleStringFixedArray(nodeA, arr, 0);
    console.info(json); // {"name":"B"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyDoubleStringArray

static stringifyDoubleStringArray(obj: Any, replacer: Array\<Double | String>, space?: Int | String): String

将ArkTS-Sta对象、数组和基本数据类型等转换成字符串，并添加条件过滤。

**参数：**

| 参数名    | 类型                     | 必填  | 说明                       |
| -------- | ------------------------ | ---- | -------------------------- |
| obj      | Any                      | 是   | 要转换的对象。              |
| replacer | Array\<Double \| String> | 是   | 过滤器。                    |
| space    | String \| Int            | 否   | 格式化缩进，默认为undefined。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

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

let arr: Array<Double | String> = ['name'];

try {
    const json = JSON.stringifyDoubleStringArray(nodeA, arr, 0);
    console.info(json); // {"name":"B"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyStringArray

static stringifyStringArray(obj: Any, replacer: Array\<String>, space?: Int | String): String

将ArkTS-Sta对象、数组、基本数据类型等转换成字符串，并添加条件过滤。

**参数：**

| 参数名    | 类型           | 必填  | 说明                      |
| -------- | -------------- | ---- | -------------------------- |
| obj      | Any            | 是   | 要转换的对象。              |
| replacer | Array\<String> | 是   | 过滤器。                    |
| space    | String \| Int  | 否   | 格式化缩进，默认为undefined。 |

**返回值：**

| 类型    | 说明            |
| ------ | --------------- |
| String | 转换后的字符串。 |

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

let arr: Array<String> = ['name'];

try {
    const json = JSON.stringifyStringArray(nodeA, arr, 0);
    console.info(json); // {"name":"B"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyByteFixedArray

static stringifyByteFixedArray(d: FixedArray\<Byte>): String

将FixedArray\<Byte>转换成字符串。

**参数：**

| 参数名 | 类型               | 必填  | 说明          |
| ----- | ------------------ | ----- | ------------- |
| d     | FixedArray\<Byte>  | 是    | Byte数组对象。 |

**返回值：**

| 类型     | 说明       |
| ------ | -------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Byte> = [1, 2, 3];

try {
    const json = JSON.stringifyByteFixedArray(d);
    console.info(json); // [1,2,3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyShortFixedArray

static stringifyShortFixedArray(d: FixedArray\<Short>): String

将FixedArray\<Short>转换成字符串。

**参数：**

| 参数名 | 类型               | 必填  | 说明           |
| ----- | -----------------  | ---- | -------------- |
| d    | FixedArray\<Short>  | 是   | Short数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Short> = [1, 2, 3];

try {
    const json = JSON.stringifyShortFixedArray(d);
    console.info(json); // [1,2,3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyIntFixedArray

static stringifyIntFixedArray(d: FixedArray\<Int>): String

将FixedArray\<Int>转换成字符串。

**参数：**

| 参数名 | 类型             | 必填  | 说明         |
| ----- | -----------------| ---- | ------------ |
| d     | FixedArray\<Int> | 是   | Int数组对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Int> = [1, 2, 3];

try {
    const json = JSON.stringifyIntFixedArray(d);
    console.info(json); // [1,2,3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyLongFixedArray

static stringifyLongFixedArray(d: FixedArray\<Long>): String

将FixedArray\<Long>转换成字符串。

**参数：**

| 参数名 | 类型              | 必填  | 说明          |
| ----- | ----------------- | ---- | ------------- |
| d     | FixedArray\<Long> | 是   | Long数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Long> = [1, 2, 3];

try {
    const json = JSON.stringifyLongFixedArray(d);
    console.info(json); // [1,2,3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyFloatFixedArray

static stringifyFloatFixedArray(d: FixedArray\<Float>): String

将FixedArray\<Float>转换成字符串。

**参数：**

| 参数名 | 类型               | 必填  | 说明           |
| ----- | ------------------ | ---- | -------------- |
| d     | FixedArray\<Float> | 是   | Float数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Float> = [1.1f, 2.2f, 3.3f];

try {
    const json = JSON.stringifyFloatFixedArray(d);
    console.info(json); // [1.1,2.2,3.3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyDoubleFixedArray

static stringifyDoubleFixedArray(d: FixedArray\<Double>): String

将FixedArray\<Double>转换成字符串。

**参数：**

| 参数名 | 类型                | 必填  | 说明            |
| ----- | ------------------- | ---- | --------------- |
| d     | FixedArray\<Double> | 是   | Double数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Double> = [1.1, 2.2, 3.3];

try {
    const json = JSON.stringifyDoubleFixedArray(d);
    console.info(json); // [1.1,2.2,3.3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyCharFixedArray

static stringifyCharFixedArray(d: FixedArray\<Char>): String

将FixedArray\<Char>转换成字符串。

**参数：**

| 参数名 | 类型              | 必填  | 说明          |
| ----- | ----------------- | ---- | ------------- |
| d     | FixedArray\<Char> | 是   | Char数组对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: FixedArray<Char> = [c'A', c'B', c'C'];

try {
    const json = JSON.stringifyCharFixedArray(d);
    console.info(json); // ["A","B","C"]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyBooleanFixedArray

static stringifyBooleanFixedArray(d: FixedArray\<Boolean>): String

将FixedArray\<Boolean>转换成字符串。

**参数：**

| 参数名 | 类型                 | 必填  | 说明             |
| ----- | -------------------- | ---- | ---------------- |
| d     | FixedArray\<Boolean> | 是   | Boolean数组对象。 |

**返回值：**

| 类型    | 说明           |
| ------ | -------------- |
| String | 转换后的字符串。 |


**示例：**

```ts
let d: FixedArray<Boolean> = [true, false, true];

try {
    const json = JSON.stringifyBooleanFixedArray(d);
    console.info(json); // [true,false,true]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyNumberArray

static stringifyNumberArray(d: Array\<Number>): String

将FixedArray\<Number>转换成字符串。

**参数：**

| 参数名 | 类型                | 必填  | 说明            |
| ----- | ------------------- | ---- | --------------- |
| d     | FixedArray\<Number> | 是   | Number数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: Array<Number> = [1.1, 2.2, 3.3];

try {
    const json = JSON.stringifyNumberArray(d);
    console.info(json); // [1.1,2.2,3.3]
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyNumberArrayLike

static stringifyNumberArrayLike(d: ArrayLike\<Number>): String

将ArrayLike\<Number>转换成字符串。

**参数：**

| 参数名 | 类型                | 必填  | 说明            |
| ----- | ------------------- | ---- | --------------- |
| d     | ArrayLike\<Number>  | 是   | Number数组对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
let d: ArrayLike<Number> = [1.1, 2.2, 3.3];

try {
    const json = JSON.stringifyNumberArrayLike(d);
    console.info(json); // {"0":1.1,"1":2.2,"2":3.3}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElementSerializable): String

将jsonx.JsonElementSerializable对象转换成字符串。

**参数：**

| 参数名 | 类型                                                 | 必填  | 说明                         |
| ----- | ---------------------------------------------------- | ----- | ---------------------------- |
| d     | [jsonx.JsonElementSerializable](arkts-sta-jsonx.md) | 是    | JsonElementSerializable对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
class JsonElementClass implements jsonx.JsonElementSerializable {
    public toJSON(): jsonx.JsonElement {
        return jsonx.JsonElement.createString("test");
    }
}

try {
    let d: JsonElementClass = new JsonElementClass();
    const json = JSON.stringifyJsonElement(d);
    console.info(json); // "test"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElementSerializable, replacer?: (Double | String)[], space?: Int | String): String

将jsonx.JsonElementSerializable对象转换成字符串，支持传入过滤条件和格式化参数。

**参数：**

| 参数名    | 类型                                                 | 必填  | 说明                                   |
| -------- | ---------------------------------------------------- | ---- | --------------------------------------- |
| d        | [jsonx.JsonElementSerializable](arkts-sta-jsonx.md) | 是   | JsonElementSerializable对象。            |
| replacer | Array\<Double \| String>                             | 否   | Double\|String类型的数组，默认为undefined。|
| space    | Int \| String                                        | 否   | Int\|String类型的对象，默认为undefined。   |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
class JsonElementClass implements jsonx.JsonElementSerializable {
    public toJSON(): jsonx.JsonElement {
        return jsonx.JsonElement.createString("test");
    }
}

try {
    let d: JsonElementClass = new JsonElementClass();
    const json = JSON.stringifyJsonElement(d, undefined, 0);
    console.info(json); // "test"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElement): String

将jsonx.JsonElement对象转换成字符串。

**参数：**

| 参数名 | 类型                                       | 必填  | 说明            |
| ----- | ------------------------------------------ | ---- | ---------------- |
| d     | [jsonx.JsonElement](arkts-sta-jsonx.md)   | 是   | JsonElement对象。 |

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: jsonx.JsonElement = jsonx.JsonElement.createString("test");
    const json = JSON.stringifyJsonElement(d);
    console.info(json); // "test"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyJsonElement

static stringifyJsonElement(elem: jsonx.JsonElement, replacer?: (Double | String)[], space?: Int | String): String

将jsonx.JsonElement对象转换成字符串，支持过滤条件和格式化参数。

**参数：**

| 参数名    | 类型                                            | 必填  | 说明                                    |
| -------- | ----------------------------------------------- | ---- | ---------------------------------------- |
| d        | [jsonx.JsonElement](arkts-sta-jsonx.md)        | 是   | JsonElement对象。                         |
| replacer | Array\<Double \| String>                        | 否   | Double\|String类型的数组，默认为undefined。|
| space    | Int \| String                                   | 否   | Int\|String类型的对象，默认为undefined。   |

**返回值：**

| 类型   | 说明             |
| ------ | --------------- |
| String | 转换后的字符串。 |

**示例：**

```ts
try {
    let d: jsonx.JsonElement = jsonx.JsonElement.createString("test");
    const json = JSON.stringifyJsonElement(d, undefined, 0);
    console.info(json); // "test"
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyWithGetters

static stringifyWithGetters(obj: Any): String

将ArkTS-Sta对象转换成JSON字符串，同时调用使用`@JSONStringifyGetter`注解标记的`get`方法，并将其返回值包含在输出中。`get`方法名作为JSON的key，返回值作为对应的value。

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

try {
    const json = JSON.stringifyWithGetters(p);
    console.info(json); // {"firstName":"John","lastName":"Doe","fullName":"John Doe"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyWithGetters

static stringifyWithGetters(obj: Any, replacer: ((key: string, value: Any) => Any) | undefined | null, space?: int | string): string

将ArkTS-Sta对象转换成JSON字符串，同时调用`@JSONStringifyGetter`注解标记的`get`方法，支持自定义过滤器和格式化参数。

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

const p = new Person("John", "Doe");

function replacer(key: string, value: Any): Any {
    if (key == "fullName") {
        return undefined;
    }
    return value;
}

try {
    const json = JSON.stringifyWithGetters(p, replacer, 2);
    console.info(json); 
    // {
    //   "firstName": "John"
    //   "lastName": "Doe",
    // }
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### stringifyWithGetters

static stringifyWithGetters(obj: Any, replacer: Array\<double | string> | Array\<string> | Array\<double>, space?: int | string): string

将ArkTS-Sta对象转换成JSON字符串，同时调用`@JSONStringifyGetter`注解标记的`get`方法，支持数组过滤器和格式化参数。

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

try {
    const json = JSON.stringifyWithGetters(p, arr, 0);
    console.info(json); // {"firstName":"John","fullName":"John Doe"}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### parse

static parse\<T>(text: String, type: Type):Any

将JSON字符串转换成指定类型的对象。

**参数：**

| 参数名  | 类型   | 必填  | 说明             |
| ------ | ------ | ---- | ----------------- |
| text   | String | 是   | JSON格式的字符串。 |
| type   | Type   | 是   | 目标类型。         |

**返回值：**

| 类型  | 说明                                                   |
| ----- | ----------------------------------------------------- |
| Any   | 返回符合条件的具体对象，开发者可以访问其成员变量和成员函数。|

**示例：**

```ts
class A {
    intValue: Int = 0;
}

let text: String = `{\"intValue\":12}`;
let typ: Type = Type.of(new A());
try {
    let result = JSON.parse<A>(text, typ) as A;
    console.info(result.intValue); // 12
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### parse

static parse\<T>(text: String, reviver: ((key: String, value: Any) => Any) | undefined, type: Type, options?: jsonx.ParseOptions): Any

将JSON字符串转换成符合条件的具体对象，支持自定义过滤器和解析参数。

**参数：**

| 参数名   | 类型                                       | 必填  | 说明                       |
| ------- | ------------------------------------------ | ---- | --------------------------- |
| text    | String                                     | 是   | JSON格式的字符串。            |
| reviver | function                                   | 是   | 过滤器。                      |
| type    | Type                                       | 是   | 目标类型。                    |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型  | 说明                                                 |
| ---- | ----------------------------------------------------- |
| Any  | 返回符合条件的具体对象，开发者可以访问其成员变量和成员函数。|

**示例：**

```ts
class A {
    intValue: Int = 0;
}

let text: String = `{\"intValue\":12}`;
let typ: Type = Type.of(new A());
let opt: jsonx.ParseOptions = {bigIntMode: jsonx.BigIntMode.DEFAULT} as jsonx.ParseOptions;
try {
    let result = JSON.parse<A>(text, undefined, typ, opt) as A;
    console.info(result.intValue); // 12
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```


### parseUpdate

static parseUpdate\<T>(json: string, instance: T): T

解析JSON字符串并将结果填充到已有实例的字段中。与parse\<T>(json, type)不同，此方法不要求目标类具有默认构造函数。JSON中不存在的key对应的字段保留实例上的当前值（合并语义）。

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

console.info(cfg.host);  // example.com
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

console.info(w.name);        // button
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

console.info(emp.name);              // Bob（保留原值）
console.info(emp.age);               // 40（保留原值）
console.info(emp.dept.name);         // Engineering
console.info(emp.dept.address.city); // Munich（保留原值）
console.info(emp.dept.address.zip);  // 80331（保留原值）
```


### parseUpdate

static parseUpdate\<T>(json: string, reviver: ((key: string, value: Any) => Any) | undefined, instance: T, options?: jsonx.ParseOptions): T

解析JSON字符串并将结果填充到已有实例的字段中，支持可选的reviver函数和解析参数。与parse\<T>(json, type)不同，此方法不要求目标类具有默认构造函数。JSON中不存在的key对应的字段保留实例上的当前值（合并语义）。

**参数：**

| 参数名    | 类型                                      | 必填  | 说明                       |
| -------- | ----------------------------------------- | ---- | -------------------------- |
| json     | string                                    | 是   | JSON格式的字符串。           |
| reviver  | function \| undefined                     | 是   | 自定义值转换函数，或undefined。|
| instance | T                                         | 是   | 要填充字段的已有实例对象。     |
| options  | [jsonx.ParseOptions](arkts-sta-jsonx.md) | 否   | 解析操作参数，默认为undefined。|

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

console.info(car.brand);        // BMW
console.info(car.year);         // 2024
console.info(car.engine.model); // V8
console.info(car.engine === engine); // true（引用保持不变）
```


### parseJsonElement

static parseJsonElement(text: string, options?: jsonx.ParseOptions): jsonx.JsonElement

将json字符串转换成JsonElement类型的实例。

**参数：**

| 参数名  | 类型   | 必填  | 说明             |
| ------ | ------ | ----- | ---------------- |
| text   | string | 是    | json格式的字符串。 |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型                                     | 说明                             |
| ---------------------------------------- | --------------------------------- |
| [jsonx.JsonElement](arkts-sta-jsonx.md) | JsonElement对象，支持JSON相关操作。 |

**示例：**

```ts
let text: String = `{\"numberValue\":123456}` 
let opt: jsonx.ParseOptions = {bigIntMode: jsonx.BigIntMode.ALWAYS_PARSE_AS_BIGINT} as jsonx.ParseOptions 
let result: jsonx.JsonElement = JSON.parseJsonElement(text, opt)	 
console.info(result.getBigInt("numberValue")) // 123456
try {	 
    result.getLong("numberValue")
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`);	 // Expected long, but element stores different value type. 
}

text = `{\"numberValue\":9223372036854775807}`
opt =  { bigIntMode: jsonx.BigIntMode.PARSE_AS_BIGINT } as jsonx.ParseOptions 
result = JSON.parseJsonElement(text, opt)
console.info(result.getLong("numberValue")) // 9223372036854775807

text = `{\"numberValue\":9223372036854775808}`
result = JSON.parseJsonElement(text, opt)
console.info(result.getBigInt("numberValue")) // 9223372036854775808
try {	 
    result.getLong("numberValue")
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`);	 // Expected long, but element stores different value type. 
}

opt =  { bigIntMode: jsonx.BigIntMode.DEFAULT } as jsonx.ParseOptions 
try {	 
    result = JSON.parseJsonElement(text, opt)
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`); // Value exceeds integer limits.
}
```


### parseJsonElement

static parseJsonElement(text: string, reviver: (key: string, value: jsonx.JsonElement) => jsonx.JsonElement, options?: jsonx.ParseOptions): jsonx.JsonElement

将JSON字符串转换成JsonElement类型的实例，支持自定义过滤方法。

**参数：**

| 参数名  | 类型      | 必填  | 说明             |
| ------- | -------- | ---- | ---------------- |
| text    | string   | 是   | json格式的字符串。 |
| reviver | function | 是   | 过滤方法。        |
| options | [jsonx.ParseOptions](arkts-sta-jsonx.md#parseoptions)  | 否   | 解析操作参数，默认为undefined。|

**返回值：**

| 类型                                      | 说明                             |
| ----------------------------------------- | --------------------------------- |
| [jsonx.JsonElement](arkts-sta-jsonx.md)  | JsonElement对象，支持JSON相关操作。 |

**示例：**

```ts
const reviver = (key: string, value: jsonx.JsonElement): jsonx.JsonElement => {
    return value;
};

let text: String = `{\"numberValue\":123456}` 
let opt: jsonx.ParseOptions = { bigIntMode: jsonx.BigIntMode.ALWAYS_PARSE_AS_BIGINT } as jsonx.ParseOptions 
let result: jsonx.JsonElement = JSON.parseJsonElement(text, reviver, opt)	 
console.info(result.getBigInt("numberValue")) // 123456
try {	 
    result.getLong("numberValue")
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`); // Expected long, but element stores different value type. 
}

text = `{\"numberValue\":-9223372036854775807}`
opt =  { bigIntMode: jsonx.BigIntMode.PARSE_AS_BIGINT } as jsonx.ParseOptions 
result = JSON.parseJsonElement(text, reviver, opt)
console.info(result.getLong("numberValue")) // -9223372036854775807

text = `{\"numberValue\":9223372036854775808}`
result = JSON.parseJsonElement(text, reviver, opt)
console.info(result.getBigInt("numberValue")) // 9223372036854775808
try {	 
    result.getLong("numberValue")
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`); // Expected long, but element stores different value type. 
}

opt =  { bigIntMode: jsonx.BigIntMode.DEFAULT } as jsonx.ParseOptions 
try {	 
    result = JSON.parseJsonElement(text, reviver, opt)
} catch (error) {	 
    const err: Error = error as Error;	 
    console.log(`${err.message}`);	// Value exceeds integer limits.
}
```


## JSONParser

JSON反序列化器，作用是将一个JSON字符串转换为JSONValue对象。

### constructor
constructor(json: String)

JSONParser的构造函数。

**参数：**

| 参数名  | 类型   | 必填  | 说明            |
| ------ | ------ | ---- | ---------------- |
| json   | String | 是   | JSON格式的字符串。 |

**示例：**

```ts
let parser: JSONParser = new JSONParser("{\"intValue\": 1}");
```

### parse

static parse(json: String): JSONValue

将JSON格式的字符串转换成JSONValue对象。

**参数：**

| 参数名  | 类型   | 必填  | 说明             |
| ------ | ------ | ---- | ---------------- |
| json   | String | 是   | JSON格式的字符串。 |

**返回值：**

| 类型      | 说明                                                       |
| --------- | ---------------------------------------------------------  |
| [JSONValue](#jsonvalue) | JSONValue类型的对象，可以转换成具体的JSON对象。 |

**示例：**

```ts
let json: String = `{\"intValue\":12}`;
try {
    let jsonObj: JSONObject = JSONParser.parse(json) as JSONObject;
    console.info(jsonObj); // {intValue:12}
} catch (error) {
    const err: Error = error as Error;
    console.error(`Failed to opt JSON. Code is ${err.code}, message is ${err.message}`);
}
```
