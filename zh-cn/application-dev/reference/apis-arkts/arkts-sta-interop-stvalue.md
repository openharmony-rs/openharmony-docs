# STValue
<!--Kit: ArkTS-->
<!--Subsystem: RuntimeCore-->
<!--Owner: @lijin1039-->
<!--Designer: @lijin1039-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @zhang_yixin13-->

本模块提供了STValue封装类内`accessor`、`check`、`instance`、`invoke`、`unwrap`和`wrap`六种类型接口，其中：

- `accessor`提供对ArkTS-Sta对象属性、数组元素和命名空间变量的访问接口。
- `check`提供了基本类型与引用类型的类型检查的接口。
- `instance`提供了实例创建、查找类型和继承关系的接口。
- `invoke`提供了ArkTS-Sta对象方法、类静态方法和命名空间函数动态调用相关的接口。
- `wrap`提供了将ArkTS-Dyn值转换为ArkTS-Sta值并封装为STValue对象的接口。
- `unwrap`提供了将STValue对象解包为ArkTS-Dyn值的接口。

> **说明：**
>
> - 本模块仅适用于ArkTS-Dyn与ArkTS-Sta进行互操作的场景。
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## STValue_accessor

### findClass

static findClass(desc: string): STValue

用于根据ArkTS-Sta类名查找类定义，接受一个类的全限定路径字符串作为参数，返回封装了该类的STValue对象。

**参数:**

| 参数名 |  类型  | 必填 |     说明     |
| :----: | :----: | :--: | :----------: |
|  desc  | string |  是  | 类全限定路径。 |

**返回值:**

|  类型   |          说明           |
| :-----: | :---------------------: |
| STValue | 封装了该类的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
// stvalue_test.ets
let studentCls = STValue.findClass('stvalue_accessor.Student');
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Student {}
```

### findNamespace

static findNamespace(desc: string): STValue

用于根据名称查找命名空间，接受一个字符串参数（命名空间的全限定路径），返回表示该命名空间的STValue对象。

**参数:**

| 参数名 |  类型  | 必填 |        说明        |
| :----: | :----: | :--: | :----------------: |
|  desc  | string |  是  | 命名空间全限定路径。 |

**返回值:**

|  类型   |            说明             |
| :-----: | :-------------------------: |
| STValue | 代表该命名空间的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
// stvalue_test.ets
let ns = STValue.findNamespace('stvalue_accessor.MyNamespace');
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace MyNamespace {}
```

### findEnum

static findEnum(desc: string): STValue

用于根据名称查找枚举类型定义，接受一个字符串参数（枚举的全限定路径），返回表示该枚举的STValue对象。如果枚举不存在或参数错误，会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |      说明      |
| :----: | :----: | :--: | :------------: |
|  desc  | string |  是  | 枚举全限定路径。 |

**返回值:**
|  类型   |          说明           |
| :-----: | :---------------------: |
| STValue | 代表该枚举的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```ts
// stvalue_test.ets
let colorEnum = STValue.findEnum('stvalue_accessor.COLOR');
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export enum COLOR {
    Red,
    Green
}
```

### classGetSuperClass

classGetSuperClass(): STValue | null

用于获取类的父类定义，不接受任何参数，返回表示父类的STValue对象。如果当前类没有父类（如Object类），会返回null；如果`this`不是类，则会抛出异常。

**返回值:**

|  类型   |         说明          |
| :-----: | :-------------------: |
| STValue | 代表父类的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
// stvalue_test.ets
let subClass = STValue.findClass('stvalue_accessor.Dog');
let parentClass = subClass.classGetSuperClass();  // 代表父类'stvalue_accessor.Animal'的STValue对象
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Animal {
  static name: string = 'Animal';
}
export class Dog extends Animal {
  static name: string = 'Dog';
}
```

### fixedArrayGetLength

fixedArrayGetLength(): number

用于获取固定长度数组的元素数量，不接受任何参数，返回表示数组长度的数字值。如果调用对象不是固定长度数组类型，会抛出异常。

**返回值:**

|  类型  |   说明   |
| :----: | :------: |
| number | 数组长度。 |

**示例:**

ArkTS-Dyn示例：

```typescript
// stvalue_test.ets
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let strArray = tns.namespaceGetVariable('strArray', SType.REFERENCE);
let arrayLength = strArray.fixedArrayGetLength(); // 3
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let strArray: FixedArray<string> = ['ab', 'cd', 'ef'];
}
```

### enumGetIndexByName

enumGetIndexByName(name: string): number

用于根据枚举成员名称查询其在枚举中的索引位置，接受一个字符串参数（成员名称），返回表示该成员索引的数字值。如果成员不存在或参数错误，会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |   说明   |
| :----: | :----: | :--: | :------: |
|  name  | string |  是  | 枚举名称。 |

**返回值:**

|  类型  |   说明   |
| :----: | :------: |
| number | 枚举索引。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let colorEnum = STValue.findEnum('stvalue_accessor.COLOR');
let redIndex = colorEnum.enumGetIndexByName('Red'); // 0
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export enum COLOR{
    Red = 1,
    Green = 3
}
```

### enumGetValueByName

enumGetValueByName(name: string, valueType: SType): STValue

用于根据成员名称获取枚举成员的值，接受两个参数：成员名称和值类型，返回对应值的STValue对象。支持整型和字符串类型的枚举值，如果成员不存在、类型不匹配或参数错误，会抛出异常。

**参数:**

|  参数名   |  类型  | 必填 |    说明    |
| :-------: | :----: | :--: | :--------: |
|   name    | string |  是  |  枚举名称。  |
| valueType | SType  |  是  | 枚举值类型。 |

**返回值:**

|  类型   |        说明         |
| :-----: | :-----------------: |
| STValue | 枚举值的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let colorEnum = STValue.findEnum('stvalue_accessor.COLOR');
let redValue = colorEnum.enumGetValueByName('Red', SType.INT);
// 获取的枚举值是一个STValue对象，需要拆箱获取对应primitive值
let unwrapRedValue = redValue.unwrapToNumber(); // 1
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export enum COLOR{
    Red = 1,
    Green = 3,
}
```

### classGetStaticField

classGetStaticField(name: string, fieldType: SType): STValue

用于获取类的静态字段值，接受两个参数：字段名称和字段类型，返回对应值的STValue对象。如果字段不存在、类型不匹配或参数错误，会抛出异常。

**参数:**

|  参数名   |  类型  | 必填 |   说明   |
| :-------: | :----: | :--: | :------: |
| fieldName | string |  是  | 字段名称。 |
| fieldType | SType  |  是  | 字段类型。 |

**返回值:**

|  类型   |        说明         |
| :-----: | :-----------------: |
| STValue | 字段值的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let personClass = STValue.findClass('stvalue_accessor.Person');
let name = personClass.classGetStaticField('name', SType.REFERENCE).unwrapToString(); // 'Person'
let age = personClass.classGetStaticField('age', SType.INT).unwrapToNumber();  // 18
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Person {
    static name: string = 'Person';
    static age: number = 18;
}
```

### classSetStaticField

classSetStaticField(name: string, val: STValue, fieldType: SType): void

用于设置类的静态字段值，接受三个参数：字段名称、要设置的值和字段类型）。主要作用是修改类的静态成员变量，支持基本类型和引用类型。如果类型不匹配、字段不存在或参数错误，会抛出异常。

**参数:**

|  参数名   |  类型   | 必填 |    说明    |
| :-------: | :-----: | :--: | :--------: |
| fieldName | string  |  是  |  字段名称。  |
|    val    | STValue |  是  | 要设置的值。 |
| fieldType |  SType  |  是  |  字段类型。  |

**返回值:** 无

**示例:**

ArkTS-Dyn示例：

```typescript
let personClass = STValue.findClass('stvalue_accessor.Person');
personClass.classSetStaticField('name', STValue.wrapString('Bob'), SType.REFERENCE);
personClass.classSetStaticField('age', STValue.wrapNumber(21), SType.DOUBLE);
let name = personClass.classGetStaticField('name', SType.REFERENCE).unwrapToString(); // 'Bob'
let age = personClass.classGetStaticField('age', SType.DOUBLE).unwrapToNumber(); // 21
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Person {
    static name: string = 'Person';
    static age: number = 18;
}
```

### objectGetProperty

objectGetProperty(name: string, propType: SType): STValue

用于获取对象实例的属性值，接受两个参数：属性名称和属性类型，返回对应值的STValue对象。主要作用是访问对象的成员变量，支持基本类型和引用类型。如果属性不存在、类型不匹配或参数错误，会抛出异常。

**参数:**

|  参数名  |  类型  | 必填 |   说明   |
| :------: | :----: | :--: | :------: |
| propName | string |  是  | 属性名称。 |
| propType | SType  |  是  | 属性类型。 |

**返回值:**

|  类型   |        说明         |
| :-----: | :-----------------: |
| STValue | 属性值的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let alice = tns.namespaceGetVariable('studentAlice', SType.REFERENCE);
let name = alice.objectGetProperty('name', SType.REFERENCE).unwrapToString(); // 'Alice'
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Student {
    name: string;
    constructor(n: string) {
        this.name = n;
    }
}

export namespace testNameSpace {
    export let studentAlice: Student = new Student('Alice');
}
```

### objectSetProperty

objectSetProperty(name: string, val: STValue, propType: SType): void

用于设置对象实例的属性值，接受三个参数：属性名称、要设置的值和属性类型。主要作用是修改对象的成员变量，支持基本类型和引用类型。如果类型不匹配、属性不存在或参数错误，会抛出异常。

**参数:**

|  参数名  |  类型   | 必填 |    说明    |
| :------: | :-----: | :--: | :--------: |
| propName | string  |  是  |  属性名称。  |
|   val    | STValue |  是  | 要设置的值。 |
| propType |  SType  |  是  |  属性类型。  |

**返回值:** 无

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let alice = tns.namespaceGetVariable('studentAlice', SType.REFERENCE);
let name = alice.objectSetProperty('name', STValue.wrapString('Bob'), SType.REFERENCE);
let name = alice.objectGetProperty('name', SType.REFERENCE).unwrapToString(); // 'Bob'
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export class Student {
    name: string;
    constructor(n: string) {
        this.name = n;
    }
}

export namespace testNameSpace {
    export let studentAlice: Student = new Student('Alice');
}
```

### fixedArrayGet

fixedArrayGet(idx: number, elementType: SType): STValue

用于获取固定长度数组中指定索引的元素值，接受两个参数：索引位置和元素类型，返回对应值的STValue对象。主要作用是访问数组元素，支持基本类型和引用类型。如果索引越界、类型不匹配或参数错误，会抛出异常。

**参数:**

|   参数名    |  类型  | 必填 |     说明     |
| :---------: | :----: | :--: | :----------: |
|     idx     | number |  是  |   数组索引。   |
| elementType | SType  |  是  | 数组元素类型。 |

**返回值:**

|  类型   |       说明        |
| :-----: | :---------------: |
| STValue | 元素的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace');
let strArray = tns.namespaceGetVariable('strArray', SType.REFERENCE);
let str = strArray.fixedArrayGet(1, SType.REFERENCE).unwrapToString(); // 'cd'
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let strArray: FixedArray<string> = ['ab', 'cd', 'ef'];
}
```

### fixedArraySet

fixedArraySet(idx: number, val: STValue, elementType: SType): void

用于设置固定长度数组中指定索引的元素值，接受三个参数：索引位置、要设置的值和元素类型。主要作用是修改数组元素，支持基本类型和引用类型。如果类型不匹配、索引越界或参数错误，会抛出异常。

**参数:**

|   参数名    |  类型   | 必填 |     说明     |
| :---------: | :-----: | :--: | :----------: |
|     idx     | number  |  是  |   数组索引。   |
|     val     | STValue |  是  |  要设置的值。  |
| elementType |  SType  |  是  | 数组元素类型。 |

**返回值:** 无

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace');
let strArray = tns.namespaceGetVariable('strArray', SType.REFERENCE);
strArray.fixedArraySet(1, STValue.wrapString('xy'), SType.REFERENCE);
let str = strArray.fixedArrayGet(1, SType.REFERENCE).unwrapToString(); // 'xy'
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let strArray: FixedArray<string> = ['ab', 'cd', 'ef'];
}
```

### namespaceGetVariable

namespaceGetVariable(name: string, variableType: SType): STValue | null

用于获取命名空间中的变量值，接受两个参数：变量名称和变量类型，返回对应值的STValue对象。主要作用是访问命名空间中的全局变量，支持基本类型和引用类型。如果变量不存在、类型不匹配或参数错误，会抛出异常。

**参数:**

|    参数名    |  类型  | 必填 |      说明      |
| :----------: | :----: | :--: | :------------: |
|     name     | string |  是  |    变量名称。    |
| variableType | SType  |  是  | 变量类型枚举值。 |

**返回值:**

|  类型   |        说明         |
| :-----: | :-----------------: |
| STValue | 变量值的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_accessor.MyNamespace');
let data = ns.namespaceGetVariable('data', SType.INT);
let num = data.unwrapToNumber();  // 42
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace MyNamespace {
    export let data: int = 42;
}
```

### namespaceSetVariable

namespaceSetVariable(name: string, value: STValue, variableType: SType): boolean

用于设置命名空间中的变量值，接受三个参数：变量名称、要设置的值和变量类型，返回操作是否成功的布尔值。主要作用是修改命名空间中的全局变量，支持基本类型和引用类型。如果变量不存在、类型不匹配或参数错误，会抛出异常。

**参数:**

|    参数名    |  类型   | 必填 |      说明      |
| :----------: | :-----: | :--: | :------------: |
|     name     | string  |  是  |    变量名称。    |
|    value     | STValue |  是  |   要设置的值。   |
| variableType |  SType  |  是  | 变量类型枚举值。 |

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |命名空间变量设置是否成功。<br>true: 设置成功。<br>false: 设置失败。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_accessor.MyNamespace');
ns.namespaceSetVariable('data', STValue.wrapInt(0), SType.INT);
let data = ns.namespaceGetVariable('data', SType.INT);
let num = data.unwrapToNumber();  // 0
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace MyNamespace {
    export let data: int = 42;
}
```

### arrayGet

arrayGet(idx: number): STValue

用于获取动态数组指定索引位置的元素，并将其封装为STValue对象返回，调用该方法的对象需要是有效的STValue引用类型数组对象。

**参数:**

| 参数名 |  类型  | 必填 |      说明      |
| :----: | :----: | :--: | :------------: |
|  idx   | number |  是  | 数组元素的索引。 |

**返回值:**

|  类型   |              说明              |
| :-----: | :----------------------------: |
| STValue | 封装了指定位置元素的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let intArray = tns.namespaceGetVariable('intArray', SType.REFERENCE);
let arrayValue0 = intArray.arrayGet(0);
let num = arrayValue0.objectInvokeMethod('toInt', ':i', []).unwrapToNumber(); // 1
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let intArray: Array<int> = [1, 2, 3, 4, 5];
}
```

### arraySet

arraySet(idx: number, val: STValue): void

用于设置动态数组指定索引位置的元素值，调用该方法的对象需要是有效的STValue引用类型数组对象，同时设置的数组值`val`需要是封装了引用类型对象的STValue对象。

**参数:**

| 参数名 |  类型   | 必填 |          说明           |
| :----: | :-----: | :--: | :---------------------: |
|  idx   | number  |  是  |     要设置的数组索引。    |
|  val   | STValue |  是  | 要存入的STValue封装对象。 |

**返回值:** 无

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let intArray = tns.namespaceGetVariable('intArray', SType.REFERENCE);
let intClass = STValue.findClass('std.core.Int');
let intObj = intClass.classInstantiate('i:', [STValue.wrapInt(10)]);
intArray.arraySet(0, intObj);
let arrayValue0 = intArray.arrayGet(0);
let num = arrayValue0.objectInvokeMethod('toInt', ':i', []).unwrapToNumber(); // 10
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let intArray: Array<int> = [1, 2, 3, 4, 5];
}
```

### arrayPush

arrayPush(val: STValue): void

在动态数组的末尾添加一个新元素，调用该方法的对象需要是有效的STValue引用类型数组对象，同时新添加的数组值`val`需要是封装了引用类型对象的STValue对象。

**参数:**

| 参数名 |  类型   | 必填 |          说明           |
| :----: | :-----: | :--: | :---------------------: |
|  val   | STValue |  是  | 要添加的STValue封装对象。 |

**返回值:** 无

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let intArray = tns.namespaceGetVariable('intArray', SType.REFERENCE);
let intClass = STValue.findClass('std.core.Int');
let intObj = intClass.classInstantiate('i:', [STValue.wrapInt(10)]);
intArray.arrayPush(intObj);
let arrayValue0 = intArray.arrayGet(5);
let num = arrayValue0.objectInvokeMethod('toInt', ':i', []).unwrapToNumber(); // 10
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let intArray: Array<int> = [1, 2, 3, 4, 5];
}
```

### arrayPop

arrayPop(): STValue

移除并返回动态数组的最后一个元素，调用该方法的对象需要是有效的STValue引用类型数组对象。

**返回值:**

|  类型   |              说明              |
| :-----: | :----------------------------: |
| STValue | 被移除的末尾元素的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let intArray = tns.namespaceGetVariable('intArray', SType.REFERENCE);
let intPop = intArray.arrayPop();
let num = intPop.objectInvokeMethod('toInt', ':i', []).unwrapToNumber(); // 5
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let intArray: Array<int> = [1, 2, 3, 4, 5];
}
```

### arrayGetLength

arrayGetLength(): number

用于获取动态数组的长度，调用该方法的对象需要是有效的STValue引用类型数组对象。

**返回值:**

|  类型  |          说明          |
| :----: | :--------------------: |
| number | 动态数组当前的元素个数。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let tns = STValue.findNamespace('stvalue_accessor.testNameSpace')
let intArray = tns.namespaceGetVariable('intArray', SType.REFERENCE);
let num = intArray.arrayGetLength(); // 5
```

ArkTS-Sta示例：

```typescript
// stvalue_accessor.ets
export namespace testNameSpace {
    export let intArray: Array<int> = [1, 2, 3, 4, 5];
}
```

### objectGetType

objectGetType(): STValue

用于获取引用类型对象的类型信息，不接受任何参数，返回表示对象类型的STValue对象。如果`this`包装的不是ArkTS-Sta对象引用，会抛出异常。

**返回值:**

|  类型   |         说明          |
| :-----: | :-------------------: |
| STValue | 类型信息的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let strWrap = STValue.wrapString('hello world');
let strType = strWrap.objectGetType();
let isString = strWrap.objectInstanceOf(strType); // true
```

## STValue_check

### isString

isString(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta字符串，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta字符串。<br>true: 是ArkTS-Sta字符串。<br>false: 不是ArkTS-Sta字符串。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let str = STValue.wrapString("Hello");
let isStr = str.isString(); // true

let num = STValue.wrapInt(42);
let isStr1 = num.isString(); // false

let ns = STValue.findNamespace('stvalue_check.Check');
data = ns.namespaceGetVariable('shouldBeString', SType.REFERENCE);
let isStr2 = str.isString(); // true
```

ArkTS-Sta示例：

```typescript
// stvalue_check.ets
export namespace Check {
   export let shouldBeString: string = "I am a string";
}
```

### isBigInt

isBigInt(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta BigInt对象，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta BigInt对象。<br>true: 是ArkTS-Sta BigInt对象。<br>false: 不是ArkTS-Sta BigInt对象。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let bigNum = STValue.wrapBigInt(1234567890n);
let isBigInt = bigNum.isBigInt(); // true
let num = STValue.wrapInt(42);
let isBigInt1 = num.isBigInt(); // false
```

### isNull

isNull(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的`null`，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta null类型。<br>true: 是ArkTS-Sta null类型。<br>false: 不是ArkTS-Sta null类型。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let nullValue = STValue.getNull();
let isNull = nullValue.isNull(); // true
let intValue = STValue.wrapNumber(42);
let isNull1 = intValue.isNull(); // false
```

### isUndefined

isUndefined(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的`undefined`，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta undefined类型。<br>true: 是ArkTS-Sta undefined类型。<br>false: 不是ArkTS-Sta undefined类型。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let undefValue = STValue.getUndefined();
let isUndef = undefValue.isUndefined(); // true
let intValue = STValue.wrapNumber(42);
let isUndef1 = intValue.isUndefined(); // false
```

### isEqualTo

isEqualTo(other: STValue): boolean

用于比较`this`和`other`包装的ArkTS-Sta对象引用是否相等，返回布尔值结果。`this`和`other`包装需要包装ArkTS-Sta对象引用。如果参数错误或类型不匹配，会抛出异常。

**参数:**

| 参数名 |  类型   | 必填 |           说明            |
| :----: | :-----: | :--: | :-----------------------: |
| other  | STValue |  是  | 要比较的另一个STValue对象。 |

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |两个STValue对象包装的引用是否相等。<br>true: 引用相等。<br>false: 引用不相等。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_check.Check');
let leftRef = ns.namespaceGetVariable('leftRef', SType.REFERENCE);
let rightRef = ns.namespaceGetVariable('rightRef', SType.REFERENCE);
let rightRefNotEqual = ns.namespaceGetVariable('rightRefNotEqual', SType.REFERENCE);
let isEqual = leftRef.isEqualTo(rightRef); // true
let isEqual1 = leftRef.isEqualTo(rightRefNotEqual); // false
```

ArkTS-Sta示例：

```typescript
// stvalue_check.ets
export namespace Check {
    export let leftRef: string = 'isEqualTo';
    export let rightRef: string = 'isEqualTo';
    export let rightRefNotEqual: string = 'isEqualToNotEqual';
}
```

### isStrictlyEqualTo

isStrictlyEqualTo(other: STValue): boolean

用于比较`this`和`other`包装的ArkTS-Sta对象引用是否严格相等，返回布尔值结果。`this`和`other`包装需要包装ArkTS-Sta对象引用。

**参数:**

| 参数名 |  类型   | 必填 |           说明            |
| :----: | :-----: | :--: | :-----------------------: |
| other  | STValue |  是  | 要比较的另一个STValue对象。 |

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |两个STValue对象包装的引用是否严格相等。<br>true: 引用严格相等。<br>false: 引用不严格相等。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_check.Check');
let magicNull = STValue.getNull();
let magicUndefined = STValue.getUndefined();
let result1 = magicNull.isStrictlyEqualTo(magicUndefined); // false

let magicString1 = ns.namespaceGetVariable('magicString1', SType.REFERENCE);
let magicString2 = ns.namespaceGetVariable('magicString2', SType.REFERENCE);
let result2 = magicString1.isStrictlyEqualTo(magicString2); // false
let result3 = magicString1.isStrictlyEqualTo(magicString1); // true
```

ArkTS-Sta示例：

```typescript
// stvalue_check.ets
export namespace Check {
    export let magicString1: string = 'Hello World';
    export let magicString2: string = 'Hello World!';
}
```

### isBoolean

isBoolean(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的boolean值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta boolean。<br>true: 是ArkTS-Sta boolean。<br>false: 不是ArkTS-Sta boolean。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let boolValue = STValue.wrapBoolean(true);
let isBool = boolValue.isBoolean(); // true
let numValue = STValue.wrapInt(1);
let isBool1 = numValue.isBoolean(); // false
```

### isByte

isByte(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的byte值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta byte。<br>true: 是ArkTS-Sta byte。<br>false: 不是ArkTS-Sta byte。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let byteValue = STValue.wrapByte(127);
let isByte = byteValue.isByte(); // true
let intValue = STValue.wrapInt(42);
let isByte1 = intValue.isByte(); // false
```

### isChar

isChar(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的char值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta char。<br>true: 是ArkTS-Sta char。<br>false: 不是ArkTS-Sta char。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let charValue = STValue.wrapChar('A');
let isChar = charValue.isChar(); // true
let strValue = STValue.wrapString("Hello");
let isChar1 = strValue.isChar(); // false
```

### isShort

isShort(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的short值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta short。<br>true: 是ArkTS-Sta short。<br>false: 不是ArkTS-Sta short。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let shortValue = STValue.wrapShort(32767);
let isShort = shortValue.isShort(); // true
let intValue = STValue.wrapInt(32767);
let isShort1 = intValue.isShort(); // false
```

### isInt

isInt(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的int值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta int。<br>true: 是ArkTS-Sta int。<br>false: 不是ArkTS-Sta int。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let intValue = STValue.wrapInt(44);
let isInt = intValue.isInt(); // true
let longValue = STValue.wrapLong(1024);
let isInt1 = longValue.isInt(); // false
```

### isLong

isLong(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的long值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta long。<br>true: 是ArkTS-Sta long。<br>false: 不是ArkTS-Sta long。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let longValue = STValue.wrapLong(1024);
let isLong = longValue.isLong(); // true
let intValue = STValue.wrapInt(44);
let isLong1 = intValue.isLong(); // false
```

### isFloat

isFloat(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的float值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta float。<br>true: 是ArkTS-Sta float。<br>false: 不是ArkTS-Sta float。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let floatValue = STValue.wrapFloat(3.14);
let isFloat = floatValue.isFloat(); // true
let intValue = STValue.wrapInt(42);
let isFloat1 = intValue.isFloat(); // false
```

### isNumber

isNumber(): boolean

用于检查STValue对象是否包装的是ArkTS-Sta的number/double值，不接受任何参数，返回布尔值结果。

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |STValue对象包装的类型是否为ArkTS-Sta number/double。<br>true: 是ArkTS-Sta number/double。<br>false: 不是ArkTS-Sta number/double。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let doubleValue = STValue.wrapNumber(3.14);
let isNumber = doubleValue.isNumber(); // true
let intValue = STValue.wrapInt(42);
let isNumber1 = intValue.isNumber(); // false
```

### typeIsAssignableFrom

static typeIsAssignableFrom(fromType: STValue, toType: STValue): boolean

用于检查类型之间的赋值兼容性，接受两个参数：源类型（fromType）和目标类型（toType），返回布尔值结果。fromType和toType一般来源于`findClass`、`objectGetType`以及`classGetSuperClass`的返回值。基于底层类型系统的规则，判断源类型的值是否可以安全赋值给目标类型的变量。

**参数:**

|  参数名  |  类型   | 必填 |            说明            |
| :------: | :-----: | :--: | :------------------------: |
| fromType | STValue |  是  |   源类型（被赋值的类型）。   |
|  toType  | STValue |  是  | 目标类型（赋值的目标类型）。 |

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |fromType是否可以赋值给toType。<br>true: 可以赋值。<br>false: 不可以赋值。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let studentCls = STValue.findClass('stvalue_example.Student');
let subStudentCls = STValue.findClass('stvalue_example.SubStudent');
let isAssignable = STValue.typeIsAssignableFrom(subStudentCls, studentCls); // true
let isAssignable1 = typeIsAssignableFrom(studentCls, subStudentCls); // false
```

ArkTS-Sta示例：

```typescript
// stvalue_example.ets
export class Student {}
export class SubStudent extends Student {}
```

### objectInstanceOf

objectInstanceOf(typeArg: STValue): boolean

用于检查对象是否为指定类型的实例，接受一个参数（类型对象），返回布尔值结果。如果对象是指定类型的实例返回true，否则返回false。

**参数:**

| 参数名  |  类型   | 必填 |           说明           |
| :-----: | :-----: | :--: | :----------------------: |
| typeArg | STValue |  是  | 要检查的类型（类或接口）。 |

**返回值:**

|  类型   |                  说明                   |
| :-----: | ------------------------------------- |
| boolean |对象是否为指定类型的实例。<br>true: 是指定类型的实例。<br>false: 不是指定类型的实例。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let studentCls = STValue.findClass('stvalue_check.Student');
let stuObj = studentCls.classInstantiate(':', []);
let isInstance = stuObj.objectInstanceOf(studentCls); // true
```

ArkTS-Sta示例：

```typescript
// stvalue_check.ets
export class Student {
    constructor() {}
}
```

### isSTArray

static isSTArray(value: object): boolean

用于判断一个对象是否代表ArkTS-Sta内的std.core.Array类型对象，返回布尔值结果。

**参数:**

| 参数名 |  类型  | 必填 |   说明   |
| :----: | :----: | :--: | :------: |
| value  | object |  是  | 判断的对象。 |

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| boolean | 判断一个对象是否代表ArkTS-Sta内的std.core.Array类型对象。<br>true: 是ArkTS-Sta内的std.core.Array类型。<br>false:  不是ArkTS-Sta内的std.core.Array类型。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stArr: st.Array<string> = STValue.newSTArray<string>();
STValue.isSTArray(stArr);  // true
let otherVal = new Object();
STValue.isSTArray(otherVal);  // false
```

### isSTMap

static isSTMap(value: object): boolean

用于判断一个对象是否代表ArkTS-Sta内的std.core.Map类型对象，返回布尔值结果。

**参数:**

| 参数名 |  类型  | 必填 |   说明   |
| :----: | :----: | :--: | :------: |
| value  | object |  是  | 判断的对象。 |

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| boolean | 判断一个对象是否代表ArkTS-Sta内的std.core.Map类型对象。<br>true: 是ArkTS-Sta内的std.core.Map类型。<br>false:  不是ArkTS-Sta内的std.core.Map类型。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stMap: st.Map<string, object> = STValue.newSTMap<string, object>();
STValue.isSTMap(stMap);  // true
let otherVal = new Object();
STValue.isSTMap(otherVal);  // false
```

### isSTSet

static isSTSet(value: object): boolean

用于判断一个对象是否代表ArkTS-Sta内的std.core.Set类型对象，返回布尔值结果。

**参数:**

| 参数名 |  类型  | 必填 |   说明   |
| :----: | :----: | :--: | :------: |
| value  | object |  是  | 判断的对象。 |

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| boolean | 判断一个对象是否代表ArkTS-Sta内的std.core.Set类型对象。<br>true: 是ArkTS-Sta内的std.core.Set类型。<br>false:  不是ArkTS-Sta内的std.core.Set类型。<br>默认: false。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stSet: st.Set<string> = STValue.newSTSet<string>();
STValue.isSTSet(stSet);  // true
let otherVal = new Object();
STValue.isSTSet(otherVal);  // false
```

## STValue_instance

### classInstantiate

classInstantiate(ctorSignature: string, args: STValue[]): STValue

用于通过类的构造函数实例化对象，接受两个参数：构造函数签名和参数数组，返回新创建的对象。动态创建类实例，支持带参数的构造函数调用，如果类不存在、构造函数不匹配或参数错误，会抛出异常。

**参数:**

|    参数名     |   类型    | 必填 |              说明               |
| :-----------: | :-------: | :--: | :-----------------------------: |
| ctorSignature |  string   |  是  | 构造函数（`参数类型:返回类型`）。 |
|     args      | STValue[] |  是  |        构造函数参数数组。         |

**返回值:**

|  类型   |       说明       |
| :-----: | :--------------: |
| STValue | 新创建的对象实例。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let studentCls = STValue.findClass('stvalue_instance.Student');
let clsObj1 = studentCls.classInstantiate(':', []);
let obj1Age = clsObj1.objectGetProperty('age', SType.INT).unwrapToNumber(); // 0
let clsObj2 = studentCls.classInstantiate('i:', [STValue.wrapInt(23)]);
let obj2Age = clsObj2.objectGetProperty('age', SType.INT).unwrapToNumber(); // 23
```

ArkTS-Sta示例：

```typescript
// stvalue_instance.ets
export class Student {
    public age: int = 0;
    constructor() {}
    constructor(age: int) { this.age = age; }
}
```

### newFixedArrayPrimitive

static newFixedArrayPrimitive(length: number, elementType: SType): STValue

用于创建预分配内存固定长度的基本类型数组，只接受两个参数：数组长度和元素类型（SType枚举），返回创建的数组对象。每种基本类型都有固定的默认值（例如SType.BOOLEAN默认false，SType.INT默认0），故不需要传入数组元素初始值，只需要指定数组长度以及元素类型即可。支持所有基本数据类型，如果元素类型不支持或参数错误，会抛出异常。

**参数:**

|   参数名    |  类型  | 必填 |           说明           |
| :---------: | :----: | :--: | :----------------------: |
|   length    | number |  是  |         数组长度。         |
| elementType | SType  |  是  | 数组元素类型（数值形式）。 |

**返回值:**

|  类型   |               说明                |
| :-----: | :-------------------------------: |
| STValue | 新创建的固定长度数组的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_instance.Instance');
// 创建的SType.BOOLEAN类型数组boolArray初始长度为5，初始值为false
let boolArray = STValue.newFixedArrayPrimitive(5, SType.BOOLEAN);
let isArray = ns.namespaceInvokeFunction('checkFixPrimitiveBooleanArray', 'A{z}:z', [boolArray]).unwrapToBoolean(); // true
```

```typescript
// stvalue_instance.ts ArkTS-Sta
export namespace Instance {
    export function checkFixPrimitiveBooleanArray(arr: FixedArray<boolean>): boolean {
        if (arr.length != 5) {
            return false;
        }
        for (let i = 0; i < 5; i++) {
            console.info(arr[i])
            if (arr[i] != false) {
                return false;
            }
        }
        return true;
    }
}
```

### newFixedArrayReference

static newFixedArrayReference(length: number, elementType: STValue, initialElement: STValue): STValue

用于创建预分配内存固定长度的引用类型数组，接受三个参数：数组长度、元素类型和**初始元素** ，返回创建的数组对象。由于引用类型没有统一的默认值，因此创建引用类型数组时，除了长度和元素类型，还需指定**初始元素** ，来将所有数组元素会初始化为该元素的引用。支持类、接口等引用类型元素，数组所有元素初始化为相同的初始值，如果参数错误或类型不匹配，会抛出异常。

**参数:**

|     参数名     |  类型   | 必填 |       说明       |
| :------------: | :-----: | :--: | :--------------: |
|     length     | number  |  是  |     数组长度。     |
|  elementType   | STValue |  是  |   数组元素类型。   |
| initialElement | STValue |  是  | 数组元素的初始值。 |

**返回值:**

|  类型   |                 说明                  |
| :-----: | :-----------------------------------: |
| STValue | 新创建的固定长度引用数组的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let ns = STValue.findNamespace('stvalue_instance.Instance');
let intClass = STValue.findClass('std.core.Int');
let intObj = intClass.classInstantiate('i:', [STValue.wrapInt(5)]);
// 创建的Int引用类型数组refArray初始长度为3，初始值是一个装箱了值为5的Int引用类型
let refArray = STValue.newFixedArrayReference(3, intClass, intObj);
let res = ns.namespaceInvokeFunction('checkFixReferenceObjectArray', 'A{C{std.core.Object}}:z', [refArray])res.unwrapToBoolean(); // true
```

```typescript
// stvalue_instance.ts ArkTS-Sta
export namespace Instance {
    function checkFixReferenceObjectArray(arr: FixedArray<Object>): boolean {
        if (arr.length != 3) {
            return false;
        }
        for (let i = 0; i < 3; i++) {
            if (!(arr[i] instanceof Int)) {
                return false;
            }
        }
        return true;
    }
}
```

### newArray

static newArray(len: number, initialElement: STValue): STValue

用于创建一个指定长度的新动态数组，并使用提供的初始元素填充数组的所有位置，其中初始元素STValue需要封装引用类型。

**参数:**

| 参数名 |  类型   | 必填 |                    说明                    |
| :----: | :-----: | :--: | :---------------------------------------: |
|  len   | number  |  是  |                数组的初始长度。              |
| initialElement | STValue |  是 | 用于填充数组每一个位置的初始元素（需为引用类型）。 |

**返回值:**

|  类型   |              说明               |
| :-----: | :----------------------------: |
| STValue | 封装了新创建数组的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let intClass = STValue.findClass('std.core.Int');
let intObj = intClass.classInstantiate('i:', [STValue.wrapInt(0)]);
let intArray = STValue.newArray(5, intObj); // [0, 0, 0, 0, 0]
```

### newSTArray

static newSTArray<T = any>(): st.Array\<T>

用于创建一个st.Array对象，代表ArkTS-Sta内的std.core.Array类型对象，初始容量与std.core.Array无参构造的对象一致。

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| st.Array | 代表ArkTS-Sta内的std.core.Array类型对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stArr: st.Array<string> = STValue.newSTArray<string>();
```

### newSTSet

static newSTSet<T = any>(): st.Set\<T>

用于创建一个st.Set对象，代表ArkTS-Sta内的std.core.Set类型对象，初始容量为8。

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| st.Set | 代表ArkTS-Sta内的std.core.Set类型对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stSet: st.Set<string> = STValue.newSTSet<string>();
```

### newSTMap

static newSTMap<K = any, V = any>(): st.Map<K, V>

用于创建一个st.Map对象，代表ArkTS-Sta内的std.core.Map类型对象，初始容量为8。

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| st.Map | 代表ArkTS-Sta内的std.core.Map类型对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
import st from "static.@ohos.lang.interop";
let stMap: st.Map<string, object> = STValue.newSTMap<string, object>();
```

## STValue_invoke
### namespaceInvokeFunction

namespaceInvokeFunction(functionName: string, signature: string, args: STValue[]): STValue

用于在命名空间中调用指定函数，接受三个参数：函数名称、函数签名和参数数组，返回函数调用的结果。主要作用是执行命名空间中的全局函数或静态函数，支持带参数的函数调用，如果函数不存在、签名不匹配或参数错误，会抛出异常。此外，不支持调用ArkTS-Sta中使用overload关键字定义的重载函数（`overload foo {foo1, foo2}`）。

**参数:**

|    参数名    |   类型    | 必填 |                 说明                  |
| :----------: | :-------: | :--: | :-----------------------------------: |
| functionName |  string   |  是  |               函数名称。                |
|  signature   |  string   |  是  | 函数签名（`参数类型:返回类型`）。 |
|     args     | STValue[] |  是  |             函数参数数组。              |

**返回值:**

|  类型   |           说明            |
| :-----: | :-----------------------: |
| STValue | 函数调用结果的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let nsp = STValue.findNamespace('stvalue_invoke.Invoke');
let b1 = STValue.wrapBoolean(false);
let b2 = STValue.wrapBoolean(false);
let b = nsp.namespaceInvokeFunction('BooleanInvoke', 'zz:z', [b1, b2]).unwrapToBoolean(); // false
```

ArkTS-Sta示例：

```typescript
// stvalue_invoke.ets
export namespace Invoke{
  // boolean type
  export function BooleanInvoke(b1 : Boolean, b2 : Boolean) : Boolean{
      return b1 & b2;
  }
}
```

### functionalObjectInvoke

functionalObjectInvoke(args: STValue[]): STValue

用于调用函数式对象（如lambda表达式或函数对象），接受一个参数数组（必须为引用类型如果需要使用primitive需要事先装箱），返回函数调用的结果。主要作用是执行函数式对象，支持带参数的调用，如果参数非引用类型或函数对象无效，会抛出异常。此外，不支持调用ArkTS-Sta中使用overload关键字定义的重载函数（`overload foo {foo1, foo2}`）。

**参数:**

| 参数名 |   类型    | 必填 |              说明              |
| :----: | :-------: | :--: | :----------------------------: |
|  args  | STValue[] |  是  | 函数参数数组（必须为引用类型）。 |

**返回值:**

|  类型   |                 说明                  |
| :-----: | :-----------------------------------: |
| STValue | 函数调用结果的STValue对象（引用类型）。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let nsp = STValue.findNamespace('stvalue_invoke.Invoke');
let getNumberFn = nsp.namespaceGetVariable('getNumberFn', SType.REFERENCE); // 获取的函数式对象getNumberFn为引用类型
let numRes = getNumberFn.functionalObjectInvoke([]); // 函数调用结果numRes是装箱后的引用类型
let jsNum = numRes.objectInvokeMethod('toInt', ':i', []); // 将结果转换为STValue装箱的int类型
let unwrapJsNum = jsNum.unwrapToNumber(); // 通过拆箱获取STValue内的函数结果: 123

let numberCls = STValue.findClass('std.core.Double');
let numberObj3 = numberCls.classInstantiate('d:', [STValue.wrapNumber(3)]); // 创建Double类型的实例
let numberObj5 = numberCls.classInstantiate('d:', [STValue.wrapNumber(5)]);
let getSumFn = nsp.namespaceGetVariable('getSumFn', SType.REFERENCE);
let sumRes = getSumFn.functionalObjectInvoke([numberObj3, numberObj5]); // 需要传入引用类型对象，这里是Double类型
let sumNum = sumRes.objectInvokeMethod('toDouble', ':d', []); // 将结果转换为STValue装箱的double类型
let unwrapSumNum = sumNum.unwrapToNumber(); // 8
```

ArkTS-Sta示例：

```typescript
// stvalue_invoke.ets
export namespace Invoke {
    export let getNumberFn = () => { return 123; }
    export let getSumFn = (n1: number, n2: number) => { return n1 + n2; }
}
```

### objectInvokeMethod

objectInvokeMethod(name: string, signature: string, args: STValue[]): STValue

用于动态调用对象的方法，接受三个参数：方法名称、方法签名以及参数数组，返回方法调用的结果。主要作用是执行对象的实例方法，支持带参数的方法调用，如果方法不存在、签名不匹配或参数错误，会抛出异常。此外，不支持调用ArkTS-Sta中使用overload关键字定义的重载函数（例如： `overload foo {foo1, foo2}`）。

**参数:**

|  参数名   |      类型      | 必填 |                 说明                  |
| :-------: | :------------: | :--: | :-----------------------------------: |
|   name    |     string     |  是  |               方法名称。                |
| signature |     string     |  是  | 方法签名（`参数类型:返回类型`）。 |
|   args    | STValue[]     |  是  |             方法参数数组。              |

**返回值:**

|  类型   |                     说明                      |
| :-----: | :-------------------------------------------: |
| STValue | 方法调用结果的STValue对象（void方法返回null）。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let studentCls = STValue.findClass('stvalue_invoke.Student');
let clsObj = studentCls.classInstantiate('iC{std.core.String}:', [STValue.wrapInt(18), STValue.wrapString('stu1')]);
let stuAge = clsObj.objectInvokeMethod('getStudentAge', ':i', []);
let unwrapStuAge = stuAge.unwrapToNumber(); // 18
let stuName = clsObj.objectInvokeMethod('getStudentName', ':C{std.core.String}', []);
let unwrapstuName.unwrapToString(); // 'stu1'
```

ArkTS-Sta示例：

```typescript
// stvalue_invoke.ets
export class Student {
    age:int;
    name: string;
    constructor(age: int, name: string) {
        this.age = age;
        this.name = name;
    }
    getStudentAge(): int {
        return this.age;
    }
    getStudentName(): string {
        return this.name;
    }
}
```

### classInvokeStaticMethod

classInvokeStaticMethod(name: string, signature: string, args: STValue[]): STValue

用于调用类的静态方法，接受三个参数：方法名称、方法签名和参数数组，返回方法调用的结果。主要作用是执行类的静态方法，支持带参数的方法调用，如果方法不存在、签名不匹配或参数错误，会抛出异常。此外，不支持调用ArkTS-Sta中使用overload关键字定义的重载方法（例如：`overload methd {methd1, methd2}`）。

**参数:**

|  参数名   |   类型    | 必填 |                 说明                  |
| :-------: | :-------: | :--: | :-----------------------------------: |
|   name    |  string   |  是  |               方法名称。                |
| signature |  string   |  是  | 方法签名（`参数类型:返回类型`）。 |
|   args    | STValue[] |  是  |             方法参数数组。              |

**返回值:**

|  类型   |                     说明                      |
| :-----: | :-------------------------------------------: |
| STValue | 方法调用结果的STValue对象（void方法返回null）。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let studentCls = STValue.findClass('stvalue_invoke.Student');
let stuId = studentCls.classInvokeStaticMethod('getStudentId', ':i', []);
let unwrapStuId = stuId.unwrapToNumber(); // 999

studentCls.classInvokeStaticMethod('setStudentId', 'i:', [STValue.wrapInt(888)]);
let newStuId = studentCls.classInvokeStaticMethod('getStudentId', ':i', []);
let unwrapNewStuId = stuId.unwrapToNumber(); // 888
```

ArkTS-Sta示例：

```typescript
// stvalue_invoke.ets
export class Student {
    private static id: int = 999;
    static getStudentId(): int {
        return Student.id;
    }
    static setStudentId(newId: int): void {
        Student.id = newId;
    }
}
```

## STValue_unwrap

### unwrapToNumber

unwrapToNumber(): number

用于将STValue对象解包为数字，不接受任何参数，返回数字值结果。支持基本数值类型(`boolean`, `byte`, `short`, `int`, `long`, `float`, `double`)的解包，如果值类型不支持或对象为引用类型，会抛出异常。

**返回值:**

|  类型  |      说明      |
| :----: | :------------: |
| number | 解包后的数字值。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let intValue = STValue.wrapInt(42);
let num = intValue.unwrapToNumber(); // 42
```

### unwrapToString

unwrapToString(): string

用于将STValue对象解包为字符串，不接受任何参数，返回字符串结果。仅支持字符串对象（`std.core.String`）的解包，其它类型会抛出异常。

**返回值:**

|  类型  |       说明       |
| :----: | :--------------: |
| string | 解包后的字符串值。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let strValue = STValue.wrapString("Hello World");
let str = strValue.unwrapToString(); // "Hello World"
```

### unwrapToBoolean

unwrapToBoolean(): boolean

用于将STValue对象解包为布尔值，不接受任何参数，返回布尔值结果。支持基本类型的解包，不支持引用类型。如果值类型不支持，会抛出异常。

**返回值:**

|  类型   |      说明      |
| :-----: | :------------: |
| boolean | 解包后的布尔值。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let boolValue = STValue.wrapBoolean(true);
let bool = boolValue.unwrapToBoolean(); // true
let intValue = STValue.wrapInt(1);
let bool1 = intValue.unwrapToBoolean(); // true
let zeroValue = STValue.wrapInt(0);
let bool2 = zeroValue.unwrapToBoolean(); // false
```

### unwrapToBigInt

unwrapToBigInt(): bigint

用于将STValue中的大整数对象解包为BigInt类型，不接受任何参数，返回大整数值结果。支持特定的大整数类（`std.core.BigInt`），其它类型会抛出异常。

**返回值:**

|  类型  |       说明       |
| :----: | :--------------: |
| bigint | 解包后的大整数值。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let bigIntValue = STValue.wrapBigInt(12345678901234567890n);
let bigInt = bigIntValue.unwrapToBigInt(); // 12345678901234567890n
```

## STValue_wrap

### wrapByte

static wrapByte(value: number): STValue

用于将数字包装为字节byte（8位有符号整数）的STValue对象，接受一个数字参数，返回包装后的STValue对象。如果值超出字节范围（-128到127），会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |      说明      |
| :----: | :----: | :--: | :------------: |
| value  | number |  是  | 要包装的数字值。 |

**返回值:**

|  类型   |            说明             |
| :-----: | :-------------------------: |
| STValue | 包装后的字节类型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let byteValue = STValue.wrapByte(127);
let isByte = byteValue.isByte(); // true
```

### wrapChar

static wrapChar(str: string): STValue

用于将字符串包装为字符类型（16位Unicode字符）的STValue对象，接受一个字符串参数，返回包装后的STValue对象。是将单个字符的字符串转换为字符类型，如果字符串长度不为1，会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |        说明        |
| :----: | :----: | :--: | :----------------: |
| str    | string |  是  | 要包装的单字节字符。 |

**返回值:**

|  类型   |            说明             |
| :-----: | :-------------------------: |
| STValue | 包装后的字符类型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let charValue = STValue.wrapChar('A');
let isChar = charValue.isChar(); // true
```

### wrapShort

static wrapShort(value: number): STValue

用于将数字包装为短整型short（16 位有符号整数）的STValue对象，接受一个数字参数，返回包装后的STValue对象。如果值超出短整型范围（-2<sup>15</sup> 到2<sup>15</sup> -1），会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |              说明               |
| :----: | :----: | :--: | :-----------------------------: |
| value  | number |  是  | 要包装的数字值（-2<sup>15</sup> 到2<sup>15</sup> -1）。 |

**返回值:**

|  类型   |           说明            |
| :-----: | :-----------------------: |
| STValue | 包装后的短整型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let shortValue = STValue.wrapShort(32767);
let isShort = shortValue.isShort(); // true
```

### wrapInt

static wrapInt(value: number): STValue

用于将数字包装为整型（32位有符号整数）的STValue对象，接受一个数字参数，返回包装后的STValue对象。如果值超出整型范围（-2<sup>31</sup> 到2<sup>31</sup> -1），会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |              说明               |
| :----: | :----: | :--: | :-----------------------------: |
| value  | number |  是  | 要包装的数字值（-2<sup>31</sup> 到2<sup>31</sup> -1）。 |

**返回值:**

|  类型   |          说明           |
| :-----: | :---------------------: |
| STValue | 包装后的整型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let intValue = STValue.wrapInt(123);
let isInt = intValue.isInt(); // true
```

### wrapLong

static wrapLong(value: number|BigInt): STValue

用于将数字或大整数包装为长整型（64位有符号整数）的STValue对象，接受一个数字或BigInt参数，返回包装后的STValue对象。如果输入的number类型的值超出了整数的精度范围（-2<sup>53</sup> -1到2<sup>53</sup> -1），或者输入的BigInt值超出长整型范围（-2<sup>63</sup> 到2<sup>63 </sup>-1），会抛出异常。

**参数:**

| 参数名 |  类型  | 必填 |              说明               |
| :----: | :----: | :--: | :-----------------------------: |
| value  | number\|BigInt |  是  | 要包装的数字值（-2<sup>63</sup> 到2<sup>63</sup> -1）。 |

**返回值:**

|  类型   |           说明            |
| :-----: | :-----------------------: |
| STValue | 包装后的长整型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let longValue = STValue.wrapLong(123);
let isLong = longValue.isLong(); // true

let longValue = STValue.wrapLong(123n);
let isLong = longValue.isLong(); // true
```

### wrapFloat

static wrapFloat(value: number): STValue

用于将数字包装为单精度浮点型（32位浮点数）的STValue对象。针对从双精度浮点数value到单精度浮点数float的转换，实际效果和c++的`static_cast<float>(value)`相同。接受一个数字参数，返回包装后的STValue对象。若数字参数超出单精度浮点数可表示的范围，会被转换为正无穷（+Infinity）或负无穷（-Infinity）。

**参数:**

| 参数名 |  类型  | 必填 |      说明      |
| :----: | :----: | :--: | :------------: |
| value  | number |  是  | 要包装的数字值。 |

**返回值:**

|  类型   |              说明               |
| :-----: | :-----------------------------: |
| STValue | 包装后的单精度浮点型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let floatValue = STValue.wrapFloat(3.14);
let isFloat = floatValue.isFloat(); // true
```

### wrapNumber

static wrapNumber(value: number): STValue

用于将数字包装为双精度浮点型（64位浮点数）的STValue对象，接受一个数字参数，返回包装后的STValue对象。若数字参数超出双精度浮点数可表示的范围，会被转换为正无穷（+Infinity）或负无穷（-Infinity）

**参数:**

| 参数名 |  类型  | 必填 |      说明      |
| :----: | :----: | :--: | :------------: |
| value  | number |  是  | 要包装的数字值。 |

**返回值:**

|  类型   |              说明               |
| :-----: | :-----------------------------: |
| STValue | 包装后的双精度浮点型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let doubleValue = STValue.wrapNumber(3.14);
let isDouble = doubleValue.isNumber(); // true
```

### wrapBoolean

static wrapBoolean(value: boolean): STValue

用于将布尔值包装为布尔类型的STValue对象，接受一个布尔参数，返回包装后的STValue对象，支持true和false两种值。

**参数:**

| 参数名 |  类型   | 必填 |      说明      |
| :----: | :-----: | :--: | :------------: |
| value  | boolean |  是  | 要包装的数字值。 |

**返回值:**

|  类型   |            说明             |
| :-----: | :-------------------------: |
| STValue | 包装后的布尔类型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let boolValue = STValue.wrapBoolean(true);
let isBool = boolValue.isBoolean(); // true
```

### wrapString

static wrapString(value: string): STValue

用于将字符串包装为字符串类型的STValue对象，接受一个字符串参数，返回包装后的STValue对象。

**参数:**

| 参数名 |  类型  | 必填 |       说明       |
| :----: | :----: | :--: | :--------------: |
| value  | string |  是  | 要包装的字符串值。 |

**返回值:**

|  类型   |             说明              |
| :-----: | :---------------------------: |
| STValue | 包装后的字符串类型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let strValue = STValue.wrapString("Hello World");
let isStr = strValue.isString(); // true
```

### wrapBigInt

static wrapBigInt(value: bigint): STValue

用于将ArkTS-Dyn BigInt对象包装为ArkTS-Sta BigInt类型的STValue对象，接受一个BigInt参数，返回包装后的STValue对象。

**参数:**

| 参数名 |  类型  | 必填 |       说明       |
| :----: | :----: | :--: | :--------------: |
| value  | bigint |  是  | 要包装的大整数值。 |

**返回值:**

|  类型   |             说明              |
| :-----: | :---------------------------: |
| STValue | 包装后的BigInt类型STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let stBigInt = STValue.wrapBigInt(12345678901234567890n);
let isBigInt = stBigInt.isBigInt(); // true
```

### getNull

static getNull(): STValue

用于获取表示ArkTS-Sta内表示`null`的STValue对象，不接受任何参数，返回一个特殊的STValue对象。该对象在所有调用中返回相同的STValue实例。

**返回值:**

|  类型   |         说明          |
| :-----: | :-------------------: |
| STValue | 表示`null`的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let stNull = STValue.getNull();
let isNull = stNull.isNull(); // true
let stNull1 = STValue.getNull();
stNull === stNull1; // true
```

### getUndefined

static getUndefined(): STValue

用于获取表示ArkTS-Sta内表示`undefined`的STValue对象，不接受任何参数，返回一个特殊的STValue对象。该对象在所有调用中返回相同的STValue实例。

**返回值:**

|  类型   |            说明            |
| :-----: | :------------------------: |
| STValue | 表示`undefined`的STValue对象。 |

**示例:**

ArkTS-Dyn示例：

```typescript
let undefValue = STValue.getUndefined();
let isUndef = undefValue.isUndefined(); // true
let undefValue1 = STValue.getUndefined();
undefValue === undefValue1;  // true
```