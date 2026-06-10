# ESValue
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供了ESValue封装类内`wrap`、`unwrap`、`check`、`accessor`、`instance`和`invoke`六种类型接口，其中：

- `wrap`提供了将ArkTS-Sta值转换为ArkTS-Dyn值并封装为ESValue对象的接口。
- `unwrap`提供了将ESValue对象解包为ArkTS-Sta值的接口，包括类型转换和解包。
- `check`提供了基本类型与引用类型的类型检查接口，以及ESValue对象之间的相等性比较接口。
- `accessor`提供了对ArkTS-Dyn对象属性和数组元素的访问接口、模块加载和全局对象访问的接口，以及可迭代对象的迭代器接口。
- `instance`提供了实例创建的接口。
- `invoke`提供了ArkTS-Dyn对象函数和方法的动态调用接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta与ArkTS-Dyn进行互操作的场景。
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
## ESValue_wrap

### Undefined

static get Undefined(): ESValue

获取存储ArkTS-Dyn动态类型undefined值的ESValue对象。

**返回值：**

|    类型     |            说明            |
| :---------: | :------------------------: |
|   ESValue   | 存储动态undefined值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let undefinedVal = ESValue.Undefined;
let isUndefinedVal = undefinedVal.isUndefined(); // true
```

### Null

static get Null(): ESValue

获取存储ArkTS-Dyn动态类型null值的ESValue对象。

**返回值：**

|    类型     |            说明            |
| :---------: | :------------------------: |
|   ESValue   | 存储动态null值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let nullVal = ESValue.Null;
let isNullVal = nullVal.isNull(); // true
```
### wrapBoolean

static wrapBoolean(b: boolean): ESValue

将布尔值包装为ESValue对象。

**参数：**

| 参数名 |  类型   | 必填 |       说明       |
| :----: | :-----: | :--: | :--------------: |
|    b   | boolean |  是  | 需要包装的boolean值。 |

**返回值：**

|    类型     |          说明          |
| :---------: | :--------------------: |
|   ESValue   | 存储动态布尔值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let trueVal = ESValue.wrapBoolean(true);
let boolVal = trueVal.toBoolean(); // true
```
### wrapString

static wrapString(s: string): ESValue

将字符串包装为ESValue对象。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|    s   | string |  是  | 需要包装的string对象。 |

**返回值：**

|    类型     |          说明          |
| :---------: | :--------------------: |
|   ESValue   | 存储动态字符串值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let strWrap = ESValue.wrapString('Hello');
let strValue = strWrap.toString(); // 'Hello'
```
### wrapNumber

static wrapNumber(n: number): ESValue

将数字包装为ESValue对象。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|    n   | number |  是  | 需要包装的number对象。 |

**返回值：**

|    类型     |          说明          |
| :---------: | :--------------------: |
|   ESValue   | 存储动态number值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let numWrap = ESValue.wrapNumber(3.1415);
let numValue = numWrap.toNumber(); // 3.1415
```
### wrapBigInt

static wrapBigInt(bi: bigint): ESValue

将BigInt包装为ESValue对象。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|   bi   | bigint |  是  | 需要包装的bigint对象。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态bigint值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let bigWrap = ESValue.wrapBigInt(9007199254740991n);
let bigValue = bigWrap.toBigInt(); // 9007199254740991n
```
### wrapByte

static wrapByte(b: byte): ESValue

将字节整数值包装为ESValue对象。`isNumber()`对byte类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |        说明        |
| :----: | :----: | :--: | :----------------: |
|    b   |  byte  |  是  | 需要包装的8位整数 (-128~127)。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态byte的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let byteWrap = ESValue.wrapByte(100);
let byteValue = byteWrap.toNumber(); // 100 (byte属于number类型)
```
### wrapShort

static wrapShort(s: short): ESValue

将短整数值包装为ESValue对象。`isNumber()`对short类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |         说明         |
| :----: | :----: | :--: | :------------------: |
|    s   | short  |  是  | 要包装的16位整数 (-32768~32767)。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态short值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let shortWrap = ESValue.wrapShort(20000);
let shortValue = shortWrap.toNumber(); // 20000 (short属于number类型)
```
### wrapInt

static wrapInt(i: int): ESValue

将整数值包装为ESValue对象。`isNumber()`对int类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |       说明       |
| :----: | :----: | :--: | :--------------: |
|    i   |  int  |  是  | 要包装的32位整数值（-2<sup>31</sup> 到2<sup>31</sup> -1）。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态int的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let intWrap = ESValue.wrapInt(2147483647);
let intValue = intWrap.toNumber(); // 2147483647 (int属于number类型)
```
### wrapLong

static wrapLong(l: long): ESValue

将长整数值包装为ESValue对象。`isNumber()`对long类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |         说明         |
| :----: | :----: | :--: | :------------------: |
|    l   |  long  |  是  | 需要包装的64位整数。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态long值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let longWrap = ESValue.wrapLong(9223372036854775807);
let longValue = longWrap.toNumber(); // 9223372036854775807 (long属于number类型)
```
### wrapLongLossy

static wrapLongLossy(l: long): ESValue

将长整数值以有损转换方式包装为ESValue对象。当传入的long值超出JavaScript的安全整数范围时，精度可能丢失。

**参数：**

| 参数名 |  类型  | 必填 |        说明        |
| :----: | :----: | :--: | :--------------: |
|    l   |  long  |  是  | 需要包装的64位整数。 |

**返回值：**

|    类型     |           说明            |
| :---------: | :-----------------------: |
|   ESValue   | 存储动态long值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let lossyWrap = ESValue.wrapLongLossy(Number.MAX_SAFE_INTEGER + 100);
let lossyValue = lossyWrap.isNumber(); // true
```
### wrapFloat

static wrapFloat(f: float): ESValue

将单精度浮点数值包装为ESValue对象。`isNumber()`对float类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |           说明           |
| :----: | :----: | :--: | :--------------------: |
|    f   | float  |  是  | 需要包装的32位浮点数数值。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态float值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let floatWrap = ESValue.wrapFloat(3.1415927);
let floatValue = floatWrap.toNumber(); // 3.1415927 (float属于number类型)
```
### wrapDouble

static wrapDouble(d: double): ESValue

将双精度浮点数值包装为ESValue对象。`isNumber()`对double类型返回`true`。

**参数：**

| 参数名 |  类型  | 必填 |          说明          |
| :----: | :----: | :--: | :------------------: |
|    d   | double |  是  | 需要包装的64位浮点数数值。 |

**返回值：**

|    类型     |           说明           |
| :---------: | :----------------------: |
|   ESValue   | 存储动态double值的ESValue对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let doubleWrap = ESValue.wrapDouble(3.14159265358);
let doubleValue = doubleWrap.toNumber(); // 3.14159265358 (double属于number类型)
```
### wrap

static wrap(o: Any): ESValue

将任意值包装为ESValue对象，会自动检测值的来源并标记其是否为ArkTS-Sta静态对象。

**参数：**

| 参数名 |  类型  | 必填 |           说明           |
| :----: | :----: | :--: | :--------------------: |
|    o   |  Any   |  是  | 需要包装的任意值（Object \| null \| undefined）。 |

**返回值：**

|    类型     |              说明              |
| :---------: | :---------------------------: |
|   ESValue   | 包装任意值的ESValue对象，自动标记来源。 |

**示例：**

ArkTS-Sta示例：

```typescript
let staticObj = new MyStaticClass();
let wrapped = ESValue.wrap(staticObj);
let isFromSta = wrapped.isStaticObject(); // true
```
## ESValue_unwrap

### unwrap

unwrap(): Any

将ESValue解包为原始值类型。

**返回值：**

|  类型  |        说明        |
| :----: | :----------------: |
|   Any  | ESValue保存的原始对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let numVal = ESValue.wrapNumber(42);
let raw = numVal.unwrap(); // 42 (number)
```
### toBoolean

toBoolean(): boolean

将ESValue对象中保存的值转换为Boolean类型返回，若类型不匹配则抛出异常。

**返回值：**

|   类型    |       说明       |
| :-------: | :--------------: |
| boolean | ESValue对象中保存的boolean值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapBoolean(true);
let boolVal = val.toBoolean(); // true
```
### toString

toString(): string

将ESValue对象中保存的值转换为string类型返回，若类型不匹配则抛出异常。

**返回值：**

|  类型   |       说明       |
| :-----: | :--------------: |
| string | ESValue对象中保存的string值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapString('hello');
let strValue = val.toString(); // 'hello'
```
### toNumber

toNumber(): number

将ESValue对象中保存的值转换为number类型返回，支持byte、short、int、long、float、number等数值子类型。若类型不匹配则抛出异常。

**返回值：**

|  类型   |       说明       |
| :-----: | :--------------: |
| number | ESValue对象中保存的number值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapNumber(42);
let numVal = val.toNumber(); // 42
```
### toBigInt

toBigInt(): bigint

将ESValue对象中保存的值转换为bigint类型返回，若类型不匹配则抛出异常。

**返回值：**

|  类型   |       说明        |
| :-----: | :---------------: |
| bigint | ESValue对象中保存的bigint值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapBigInt(100n);
let bigValue = val.toBigInt(); // 100n
```
### toUndefined

toUndefined(): undefined

将ESValue对象中保存的值转换为undefined返回，若类型不匹配则抛出异常。

**返回值：**

|     类型      |   说明   |
| :-----------: | :------: |
| undefined | ESValue对象中保存的undefined值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.Undefined;
let undefValue = val.toUndefined(); // undefined
```
### toNull

toNull(): null

将ESValue对象中保存的值转换为null返回，若类型不匹配则抛出异常。

**返回值：**

|  类型  | 说明 |
| :----: | :--: |
|  null  | ESValue对象中保存的null值。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.Null;
let nullValue = val.toNull(); // null
```
### toStaticObject

toStaticObject(): object

将ESValue对象中保存的值转换为静态对象返回，若对象不是来自ArkTS-Sta则抛出异常。

**返回值：**

|  类型   |         说明          |
| :-----: | :-------------------: |
| object | ESValue对象中保存的静态对象。|

**示例：**

ArkTS-Sta示例：

```typescript
let objVal = ESValue.instantiateEmptyObject();
objVal.setProperty('property', ESValue.wrapString('value'));
```
### toPromise

toPromise(): Promise\<ESValue>

将ESValue对象中保存的Promise对象转换为`Promise<ESValue>`返回，resolve和reject的结果会被包装为ESValue对象。若类型不匹配则抛出异常。

**返回值：**

|      类型       |              说明              |
| :-------------: | :---------------------------: |
| Promise<ESValue\> | 返回ESValue对象中保存的Promise对象。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export async function sleepRetNumber(ms: number): Promise<number> {
    await sleep(ms);
    return 0xcafe;
}
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let sleepRetNumber = module.getProperty('sleepRetNumber');
let promiseESValue = sleepRetNumber.invoke(ESValue.wrapNumber(5000));
if (promiseESValue.isPromise()) {
    let promise = promiseESValue.toPromise();
    promise.then((result) => {
        let num = result.toNumber(); // 0xcafe
    });
}
```
## ESValue_check

### isBoolean

isBoolean(): boolean

判断ESValue对象中保存的对象是否是Boolean类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是Boolean类型。<br>true: 是Boolean类型。<br>false: 不是Boolean类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapBoolean(true);
let isBool = val.isBoolean(); // true
```
### isString

isString(): boolean

判断ESValue对象中保存的对象是否是string类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是string类型。<br>true: 是string类型。<br>false: 不是string类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapString('text');
let isStringValue = val.isString(); // true
```
### isNumber

isNumber(): boolean

判断ESValue对象中保存的对象是否是number类型，包括byte、short、int、long、float和number等数值子类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是number类型，包括byte、short、int、long、float和number等数值子类型。<br>true: 是number类型。<br>false: 不是number类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapNumber(3.14);
let isNumValue = val.isNumber(); // true

let intVal = ESValue.wrapInt(42);
let isNumValue1 = intVal.isNumber(); // true
```
### isBigInt

isBigInt(): boolean

判断ESValue对象中保存的对象是否是bigint类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是bigint类型。<br>true: 是bigint类型。<br>false: 不是bigint类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.wrapBigInt(100n);
let isBigIntValue = val.isBigInt(); // true
```
### isUndefined

isUndefined(): boolean

判断ESValue对象中保存的对象是否是undefined值。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是undefined值。<br>true: 是undefined值。<br>false: 不是undefined值。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.Undefined;
let isUndefinedValue = val.isUndefined(); // true
```
### isNull

isNull(): boolean

判断ESValue对象中保存的对象是否是null值。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是null值。<br>true: 是null值。<br>false: 不是null值。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val = ESValue.Null;
let isNullValue = val.isNull(); // true
```
### isStaticObject

isStaticObject(): boolean

判断ESValue对象中保存的对象是否是在ArkTS-Sta中创建的类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是ArkTS-Sta静态对象。<br>true: 是静态对象。<br>false: 不是静态对象。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let obj = ESValue.instantiateEmptyObject();
let isStaticObj = obj.isStaticObject(); // true
```
### isECMAObject

isECMAObject(): boolean

判断ESValue对象中保存的对象是否是ECMA类型。即不是静态对象、不是基本类型（boolean、string、number、bigint）、不是undefined/null、也不是function的对象。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是ECMA类型。<br>true: 是ECMA标准对象类型。<br>false: 不是ECMA标准对象类型。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
class A {};
export let a = new A();
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let obj = module.getProperty('a');
let isECMAObj = obj.isECMAObject(); // true
```
### isObject

isObject(): boolean

判断ESValue对象中保存的对象是否是Object类型，即ECMA对象或静态对象。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是Object类型（ECMA对象或静态对象）。<br>true: 是对象类型（ECMA对象或静态对象）。<br>false: 不是对象类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let staticObj = ESValue.instantiateEmptyObject();
let ecmaObj = createECMAObject();
let isStaObj = staticObj.isObject(); // true
let isECMAObj = ecmaObj.isObject(); // true
```
### isFunction

isFunction(): boolean

判断ESValue对象中保存的对象是否是Function类型。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是Function类型。<br>true: 是函数类型。<br>false: 不是函数类型。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let isFunc = func.isFunction(); // true
```
### isPromise

isPromise(): boolean

判断ESValue对象中保存的对象是否是Promise对象。

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否是Promise对象。<br>true: 是Promise对象。<br>false: 不是Promise对象。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export async function sleepRetNumber(ms: number): Promise<number> {
    await sleep(ms);
    return 0xcafe;
}
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let sleepRetNumber = module.getProperty('sleepRetNumber');
let res = sleepRetNumber.invoke(ESValue.wrapNumber(5000)).isPromise();
```
### typeOf

typeOf(): String

获取ESValue对象中保存的动态对象的类型字符串，返回值为小写形式的类型名称。

**返回值：**

|   类型    |          说明           |
| :-------: | :---------------------: |
|   String  | ESValue中保存对象类型字符串（小写形式）。 |

**示例：**

ArkTS-Sta示例：

```typescript
ESValue.wrapNumber(42).typeOf();      // 'number'
ESValue.Null.typeOf();                // 'null'
ESValue.Undefined.typeOf();           // 'undefined'
ESValue.wrapString('hello').typeOf(); // 'string'
```
### instanceOf

instanceOf(type: ESValue | Type): boolean

检查ESValue对象中保存的动态对象是否是指定类型的实例。支持两种类型参数：传入`ESValue`时检查是否为该动态类型的实例；传入`Type`时按ArkTS-Sta的类型规则进行检查。

**参数：**

| 参数名 |      类型       | 必填 |         说明         |
| :----: | :------------: | :--: | :------------------: |
|  type  | ESValue \| Type |  是  | 动态类型或静态类型。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的动态对象是否是指定类型的实例。<br>true: 是目标类型实例。<br>false: 不是目标类型实例。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export class User {
  ID = 123;
}
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsUser = module.getProperty('User');
let user = jsUser.instantiate();
let res = user.instanceOf(jsUser); // true
```
### areEqual

static areEqual(ev1: ESValue, ev2: ESValue): boolean

判断两个ESValue对象中保存的对象是否抽象相等，遵循JavaScript的抽象相等规则（`==`）。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|   ev1  |   ESValue  |  是  | 比较的第一个值。 |
|   ev2  |   ESValue  |  是  | 比较的第二个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | 两个ESValue对象中保存的对象是否抽象相等。<br>true: 值相等（抽象相等规则）。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val1 = ESValue.wrapNumber(42);
let val2 = ESValue.wrapString('42');
let res = ESValue.areEqual(val1, val2); // true (抽象相等)
```
### areStrictlyEqual

static areStrictlyEqual(ev1: ESValue, ev2: ESValue): boolean

判断两个ESValue对象中保存的对象是否严格相等，遵循JavaScript的严格相等规则（`===`）。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|   ev1  |   ESValue  |  是  | 比较的第一个值。 |
|   ev2  |   ESValue  |  是  | 比较的第二个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | 两个ESValue对象中保存的对象是否严格相等。<br>true: 值相等（严格相等规则）。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val1 = ESValue.wrapNumber(42);
let val2 = ESValue.wrapString('42');
let res = ESValue.areStrictlyEqual(val1, val2); // false
```
### areEqualSafe

static areEqualSafe(ev1: ESValue, ev2: ESValue): boolean

安全判断两个ESValue对象中保存的对象是否相等。当任一值为null或undefined时，二者视为相等；否则使用严格相等规则进行比较。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|   ev1  |   ESValue  |  是  | 比较的第一个值。 |
|   ev2  |   ESValue  |  是  | 比较的第二个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | 两个ESValue对象中保存的对象是否安全相等。<br>true: null和undefined互视为相等，其余使用严格相等。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let nullVal = ESValue.Null;
let undefVal = ESValue.Undefined;
let res = ESValue.areEqualSafe(nullVal, undefVal); // true
```
### isEqualTo

isEqualTo(other: ESValue): boolean

判断一个ESValue中保存的对象是否与另外一个ESValue中保存的对象抽象相等，是`areEqual`的实例方法版本。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|  other |   ESValue  |  是  | 比较的另一个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否与另一个ESValue中保存的对象抽象相等。<br>true: 值相等（抽象相等规则）。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val1 = ESValue.wrapNumber(42);
let val2 = ESValue.wrapString('42');
let res = val1.isEqualTo(val2); // true
```
### isStrictlyEqualTo

isStrictlyEqualTo(other: ESValue): boolean

判断一个ESValue中保存的对象是否与另外一个ESValue中保存的对象严格相等，是`areStrictlyEqual`的实例方法版本。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|  other |   ESValue  |  是  | 比较的另一个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否与另一个ESValue中保存的对象严格相等。<br>true: 值相等（严格相等规则）。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let val1 = ESValue.wrapNumber(42);
let val2 = ESValue.wrapNumber(42);
let res = val1.isStrictlyEqualTo(val2); // true
```
### isEqualToSafe

isEqualToSafe(other: ESValue): boolean

安全判断一个ESValue中保存的对象是否与另外一个ESValue中保存的对象相等，是`areEqualSafe`的实例方法版本。null和undefined互视为相等。

**参数：**

| 参数名 |    类型    | 必填 |     说明     |
| :----: | :--------: | :--: | :----------: |
|  other |   ESValue  |  是  | 比较的另一个值。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | ESValue对象中保存的对象是否与另一个ESValue中保存的对象安全相等。<br>true: null和undefined互视为相等，其余使用严格相等。<br>false: 值不相等。<br>默认: false。 |

**示例：**

ArkTS-Sta示例：

```typescript
let nullVal = ESValue.Null;
let undefVal = ESValue.Undefined;
let res = nullVal.isEqualToSafe(undefVal); // true
```
## ESValue_accessor

### getProperty

getProperty(name: string): ESValue

以`name`值为属性名，获取this中保存的动态对象的属性值。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :---------: |
|  name  | string |  是  |  属性名称。  |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的获取到属性值。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let A = {
    'property1': 1,
    'property2': 2
};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsObjectA = module.getProperty('A');
let prop1 = jsObjectA.getProperty('property1');
```
### getProperty

getProperty(index: number): ESValue

以`index`值为属性名，获取this中保存的动态对象里的数组值或属性值。当index为正整数时获取数组元素，否则按属性名获取。

**参数：**

| 参数名 |  类型  | 必填 |    说明    |
| :----: | :----: | :--: | :--------: |
| index  | number |  是  |  对应数组元素的索引。  |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的获取到元素值。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let jsArray = ['foo', 1, true];
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsArray = module.getProperty('jsArray');
let val = jsArray.getProperty(2);
```
### getProperty

getProperty(property: ESValue): ESValue

以`property`保存的动态对象为属性名，获取this保存的动态对象的属性值。

**参数：**

|  参数名  |   类型   | 必填 |     说明     |
| :------: | :------: | :--: | :----------: |
| property | ESValue |  是  | 属性标识对象。 |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的获取到属性值。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let jsArray = ['foo', 1, true];
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsArray = module.getProperty('jsArray');
let val = jsArray.getProperty(ESValue.wrapNumber(2));
```
### getPropertySafe

getPropertySafe(name: string): ESValue

以`name`值为属性名安全获取属性值。若属性存在则返回对应的ESValue，若属性不存在则返回`ESValue.Undefined`，不会抛出异常。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :---------: |
|  name  | string |  是  |  属性名称。  |

**返回值：**

|   类型    |            说明             |
| :-------: | :------------------------: |
|  ESValue | ESValue包装的属性值，不存在时返回ESValue.Undefined。 |

**示例：**

ArkTS-Sta示例：

```typescript
let obj = ESValue.instantiateEmptyObject();
obj.setProperty('key', ESValue.wrapString('value'));
let val = obj.getPropertySafe('key'); // ESValue包装的'value'
let missing = obj.getPropertySafe('nonexistent'); // ESValue.Undefined
```
### getPropertySafe

getPropertySafe(index: number): ESValue

以`index`为索引安全获取元素值。若元素存在则返回对应的ESValue，若不存在则返回`ESValue.Undefined`，不会抛出异常。

**参数：**

| 参数名 |  类型  | 必填 |    说明    |
| :----: | :----: | :--: | :--------: |
| index  | number |  是  |  数组索引。  |

**返回值：**

|   类型    |            说明             |
| :-------: | :------------------------: |
|  ESValue | ESValue包装的元素值，不存在时返回ESValue.Undefined。 |

**示例：**

ArkTS-Sta示例：

```typescript
let arr = ESValue.instantiateEmptyArray();
arr.setProperty(0, ESValue.wrapNumber(1));
let val = arr.getPropertySafe(0); // ESValue包装的1
let missing = arr.getPropertySafe(99); // ESValue.Undefined
```
### getPropertySafe

getPropertySafe(property: ESValue): ESValue

以`property`保存的动态对象为属性名安全获取属性值。若属性存在则返回对应的ESValue，若不存在则返回`ESValue.Undefined`，不会抛出异常。

**参数：**

|  参数名  |   类型   | 必填 |     说明     |
| :------: | :------: | :--: | :----------: |
| property | ESValue |  是  | 属性标识对象。 |

**返回值：**

|   类型    |            说明             |
| :-------: | :------------------------: |
|  ESValue | ESValue包装的属性值，不存在时返回ESValue.Undefined。 |

**示例：**

ArkTS-Sta示例：

```typescript
let global = ESValue.getGlobal();
let symbolIterator = global.getProperty("Symbol").getPropertySafe("iterator");
```
### setProperty

setProperty(name: string, value: [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)): void

以`name`值为属性名，设置this保存的动态对象的属性值。`value`参数支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

| 参数名 |       类型        | 必填 |     说明     |
| :----: | :-------: | :--: | :----------: |
|  name  |  string   |  是  |   属性名称。   |
| value  | [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue) |  是  |   属性值。    |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export let A = {
    'property1': 1,
};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsObjectA = module.getProperty('A');
let value = ESValue.wrapNumber(5);
jsObjectA.setProperty('property1', value);
```
### setProperty

setProperty(index: number, value: [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)): void

以`index`值为属性名，设置this保存的动态对象的属性值。当index为正整数时设置数组元素，否则按属性名设置。`value`参数支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

| 参数名 |       类型        | 必填 |     说明     |
| :----: | :-------: | :--: | :----------: |
| index  |  number   |  是  |   数组索引。   |
| value  | [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue) |  是  |   元素值。     |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export let jsArray1 = ['foo', 1, true];
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsArray1 = module.getProperty('jsArray1');
let value = ESValue.wrapBoolean(false);
jsArray1.setProperty(2, value);
```
### setProperty

setProperty(property: ESValue, value: [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)): void

以`property`保存的动态对象为属性名，设置this保存的动态对象的属性值。`value`参数支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

|  参数名  |       类型        | 必填 |     说明     |
| :------: | :-------: | :--: | :----------: |
| property |  ESValue  |  是  | 属性标识对象。 |
|  value   | [StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue) |  是  |   属性值。     |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export let A = {
    'property1': 1,
};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsObjectA = module.getProperty('A');
let value = ESValue.wrapNumber(5);
let property = ESValue.wrapString('property1');
jsObjectA.setProperty(property, value);
```
### hasProperty

hasProperty(name: string): boolean

以`name`为属性名，检查this保存的动态对象中是否包含指定属性，检查范围包含原型链上的属性。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|  name  | string |  是  |   属性名称。  |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | this保存的动态对象中是否包含指定属性。<br>true: 属性存在（包含原型链上的属性）。<br>false: 属性不存在。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
class dynamicObjectA {
    idx: number = 0
}
export let dyObj = new dynamicObjectA();
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let obj = module.getProperty('dyObj');
let hasIdx = obj.hasProperty('idx');
```
### hasProperty

hasProperty(property: ESValue): boolean

以`property`保存的动态对象为属性名，检查this保存的动态对象中是否包含指定属性，检查范围包含原型链上的属性。

**参数：**

|  参数名  |   类型   | 必填 |     说明     |
| :------: | :------: | :--: | :----------: |
| property | ESValue |  是  | 属性标识对象。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | this保存的动态对象中是否包含指定属性。<br>true: 属性存在（包含原型链上的属性）。<br>false: 属性不存在。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
class dynamicObjectA {
    idx: number = 0
}
export let dyObj = new dynamicObjectA();
export let key = 'idx';
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let obj = module.getProperty('dyObj');
let key = module.getProperty('key');
let hasIdx = obj.hasProperty(key);
```
### hasOwnProperty

hasOwnProperty(name: string): boolean

以`name`为属性名，检查this保存的动态对象中自身（不包含原型链）是否包含指定属性。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|  name  | string |  是  |   属性名称。   |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | this保存的动态对象中自身是否包含指定属性（不包含原型链）。<br>true: 对象自身包含该属性。<br>false: 对象自身不包含该属性。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
class dynamicObjectA {
    idx: number = 0
}
export let dyObj = new dynamicObjectA();
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let obj = module.getProperty('dyObj');
let hasIdx = obj.hasOwnProperty('idx');
```
### hasOwnProperty

hasOwnProperty(property: ESValue): boolean

以`property`保存的动态对象为属性名，检查this保存的对象中自身（不包含原型链）是否包含指定属性。

**参数：**

|  参数名  |   类型   | 必填 |     说明     |
| :------: | :------: | :--: | :----------: |
| property | ESValue |  是  | 属性标识对象。 |

**返回值：**

|   类型    |                  说明                   |
| :-------: | ------------------------------------- |
| boolean | this保存的动态对象中自身是否包含指定属性（不包含原型链）。<br>true: 对象自身包含该属性。<br>false: 对象自身不包含该属性。<br>默认: false。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
class dynamicObjectA {
    idx: number = 0
}
export let dyObj = new dynamicObjectA();
export let key = 'idx';
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let obj = module.getProperty('dyObj');
let key = module.getProperty('key');
let hasIdx = obj.hasOwnProperty(key);
```
### keys

keys(): IterableIterator\<ESValue>

获取this保存的动态对象中自身可枚举属性名的迭代器，迭代得到的值为ESValue包装的动态对象。

**返回值：**

|            类型             |        说明         |
| :-------------------------: | :-----------------: |
| IterableIterator<ESValue\> | ESValue包装的属性名迭代器。|

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let testIteratorObject = {'a': 1, 'b': 2, 'c' : 3};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsIterableObject = module.getProperty('testIteratorObject');
let result: String = new String();
for (const key of jsIterableObject.keys()) {
    result += key.toString();
}
```
### values

values(): IterableIterator\<ESValue>

获取this保存的动态对象中自身可枚举属性值的迭代器，迭代得到的值为ESValue包装的动态对象。

**返回值：**

|            类型             |        说明         |
| :-------------------------: | :-----------------: |
| IterableIterator<ESValue\> | ESValue包装的属性值迭代器。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let testIteratorObject = {'a': 1, 'b': 2, 'c' : 3};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsIterableObject = module.getProperty('testIteratorObject');
let result: number = 0;
for (const value of jsIterableObject.values()) {
    result += value.toNumber();
}
```
### entries

entries(): IterableIterator\<[ESValue, ESValue]\>

获取this保存的动态对象中自身可枚举键值对的迭代器，迭代得到的键值对都为ESValue包装的动态对象。

**返回值：**

|                  类型                   |        说明         |
| :-------------------------------------: | :-----------------: |
| IterableIterator\<[ESValue, ESValue]\> | [ESValue包装的属性名, ESValue包装的属性值]元组迭代器。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let testIteratorObject = {'a': 1, 'b': 2, 'c' : 3};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsIterableObject = module.getProperty('testIteratorObject');
let resultKey: String = new String();
let resultValue: number = 0;
for (const entry of jsIterableObject.entries()) {
    resultKey += entry[0].toString();
    resultValue += entry[1].toNumber();
}
```
### load

static load(module: string): ESValue

根据指定路径名加载ArkTS-Dyn的模块，返回用ESValue包装的对象。

**参数：**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
| module | string |  是  | 模块路径或标识。 |

**返回值：**

|   类型    |          说明          |
| :-------: | :--------------------: |
|   ESValue | ESValue包装ArkTS-Dyn的模块。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
let num = 1;
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
```
### getGlobal

static getGlobal(): ESValue

获取ArkTS-Dyn的globalThis对象，返回用ESValue包装的对象。

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|   ESValue | 运行时全局对象引用。 |

**示例：**

ArkTS-Sta示例：

```typescript
let global = ESValue.getGlobal();
```
### $_iterator

$_iterator(): IterableIterator\<ESValue>

获取this保存的动态对象中的迭代器对象，迭代的值为ESValue包装的动态对象。

**返回值：**

|            类型             |                    说明                    |
| :-------------------------: | :----------------------------------------: |
| IterableIterator<ESValue\> | 实现ESValue对象内部成员的可迭代迭代器接口。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.js
export let jsIterable = ['a', 'b', 'c', 'd'];
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsIterable = module.getProperty('jsIterable');
let result: String = new String();
for (const elem of jsIterable) {
    result += elem.toString();
}
```
### iterator

iterator(): IterableIterator\<ESValue>

`iterator`是`$_iterator`的别名方法，行为与`$_iterator`完全一致。

**返回值：**

|            类型             |                    说明                    |
| :-------------------------: | :----------------------------------------: |
| IterableIterator<ESValue\> | 实现ESValue对象内部成员的可迭代迭代器接口。 |

**示例：**

ArkTS-Sta示例：

```typescript
let iter = jsIterable.iterator();
let next = iter.next();
```
## ESValue_instance

### instantiate

instantiate(...args: FixedArray\<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)>): ESValue

实例化一个类，并将其包装成ESValue对象返回。参数为构造函数所需的参数，`args`支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

|     参数名     |           类型           | 必填 |       说明       |
| :------------: | :---------------------: | :--: | :--------------: |
| args | FixedArray<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)\> |  否  | 动态类构造函数的可选参数列表。 |

**返回值：**

|   类型    |            说明             |
| :-------: | :-------------------------: |
|   ESValue | 存储实例对象的ESValue对象。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export class User {
    name: string;
    id: number;
    constructor(name: string, id: number) {
        this.name = name;
        this.id = id;
    }
}
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let dynUser = module.getProperty('User');
let instance = dynUser.instantiate(ESValue.wrapString('hello'), ESValue.wrapNumber(32));
```
### instantiateEmptyObject

static instantiateEmptyObject(): ESValue

初始化一个ArkTS-Dyn空对象，并将其包装成ESValue对象返回。

**返回值：**

|   类型    |          说明          |
| :-------: | :--------------------: |
|   ESValue | ESValue包装的ArkTS-Dyn空的object对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let obj = ESValue.instantiateEmptyObject();
obj.setProperty('key', ESValue.wrapString('value'));
```
### instantiateEmptyArray

static instantiateEmptyArray(): ESValue

初始化一个ArkTS-Dyn空的Array对象，并将其包装成ESValue对象返回。

**返回值：**

|   类型    |          说明          |
| :-------: | :--------------------: |
|   ESValue | ESValue包装的ArkTS-Dyn空的Array对象。 |

**示例：**

ArkTS-Sta示例：

```typescript
let arr = ESValue.instantiateEmptyArray();
arr.setProperty(0, ESValue.wrapNumber(1));
arr.setProperty(1, ESValue.wrapNumber(2));
```
## ESValue_invoke

### invoke

invoke(...args: FixedArray\<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)>): ESValue

执行this中保存的动态对象的函数或方法，`args`为参数列表，支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

|   参数名   |           类型           | 必填 |     说明     |
| :--------: | :---------------------: | :--: | :----------: |
| args | FixedArray<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)\> |  否  | 动态对象函数或方法的可选参数列表。 |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的方法执行结果。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export let jsFunc = function () { return 6; };
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsFunc = module.getProperty('jsFunc');
let result = jsFunc.invoke();
```
### invokeWithRecv

invokeWithRecv(recv: ESValue, ...args: FixedArray\<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)>): ESValue

以`recv`为this上下文，`args`为参数，执行ESValue中保存的方法。`args`支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

| 参数名 |           类型           | 必填 |     说明     |
| :----: | :---------------------: | :--: | :----------: |
|  recv  |         ESValue          |  是  |    this值。   |
| ...args | FixedArray<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)\> |  否  | 函数参数列表。 |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的方法执行结果。 |

**示例：**

ArkTS-Sta示例：

```typescript
let global = ESValue.getGlobal();
let symbol = global.getProperty("Symbol");
let symbolIterator = symbol.getProperty("iterator");
let symbolIteratorMethod = iterableObj.getProperty(symbolIterator);
let iterator = symbolIteratorMethod.invokeWithRecv(iterableObj);
```
### invokeMethod

invokeMethod(method: string, ...args: FixedArray\<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)>): ESValue

以`method`方法名获取this中保存的动态对象的方法并执行该方法。`args`支持传入ESValue对象或ArkTS-Sta静态对象。

**参数：**

| 参数名 |           类型           | 必填 |     说明     |
| :----: | :---------------------: | :--: | :----------: |
| method |          string          |  是  |   方法名称。   |
| ...args | FixedArray<[StaticOrESValue](../../quick-start/arkts-sta-interop-interface.md#staticoresvalue)\> |  否  | 方法参数列表。 |

**返回值：**

|   类型    |        说明         |
| :-------: | :-----------------: |
|  ESValue | ESValue包装的方法执行结果。 |

**示例：**

ArkTS-Dyn示例：

```typescript
// file1.ts
export let objWithFunc = {
    'func': function () {
        return 'hello';
    }
};
```

ArkTS-Sta示例：

```typescript
// file2.ets
let module = ESValue.load('file1');
let jsObjWithFunc = module.getProperty('objWithFunc');
let result = jsObjWithFunc.invokeMethod('func');
```