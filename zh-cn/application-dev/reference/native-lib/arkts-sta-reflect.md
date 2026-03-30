# reflect

本模块提供反射相关的功能，包括类反射、字段反射、方法反射和动态代理。开发者可以使用本模块获取类和对象的反射信息，包括检查接口类型、函数对象类型、获取字段和方法的元数据，并在运行时创建实例、调用方法和访问字段，以及创建动态代理对象。

> **说明：**
>
> - 本模块仅适用于ArkTS-Sta。
>
> - 本模块首批接口从API version 24开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## isLiteralInitializedInterface

isLiteralInitializedInterface(target: Object): boolean

检查给定对象是否是基于接口初始化的字面量对象。

**参数：**

| 参数   | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| target | Object | 是   | 要检查的对象。    |

**返回值：**

| 类型    | 说明                                               |
| ------- | -------------------------------------------------- |
| boolean | 如果target是用字面量初始化的接口对象返回true，否则返回false。 |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
}
class MyClass implements MyInterface {
    public name: string = "Bob";
    public age: int = 25;
}

// 使用对象字面量初始化接口
let obj1: MyInterface = { name: "Alice", age: 30 };
console.info(reflect.isLiteralInitializedInterface(obj1)); // true

// 使用对象字面量初始化类
let obj2: MyClass = { name: "Alice", age: 30 };
console.info(reflect.isLiteralInitializedInterface(obj2)); // false

// 使用类实例化
let obj3: MyInterface = new MyClass();
console.info(reflect.isLiteralInitializedInterface(obj3)); // false
```

## isFuncObjAsync

isFuncObjAsync(target: Function): boolean

判断函数对象是否是异步函数。

**参数：**

| 参数   | 类型     | 必填 | 说明                   |
| ------ | -------- | ---- | ---------------------- |
| target | Function | 是   | 要检查的函数对象。      |

**返回值：**

| 类型    | 说明                                                         |
| ------- | ------------------------------------------------------------ |
| boolean | 如果目标类标注了`std.core.AsyncFunctionObject`注解返回true，否则返回false。 |

**示例：**

```ts
async function asyncFunc() {
    console.info("async function");
}

function syncFunc() {
    console.info("sync function");
}

console.info(reflect.isFuncObjAsync(asyncFunc)); // true
console.info(reflect.isFuncObjAsync(syncFunc)); // false
```

## getInstanceGettersRecursive

getInstanceGettersRecursive(targetClass: Class): Array\<InstanceMethod>

返回类及其父类的所有公共实例getter方法。

**参数：**

| 参数        | 类型   | 必填 | 说明           |
| ----------- | ------ | ---- | -------------- |
| targetClass | [Class](#class) | 是   | 要获取getter的类。 |

**返回值：**

| 类型   | 说明                               |
| ------ | ---------------------------------- |
| Array\<[InstanceMethod](#instancemethod)\> | 包含类所有getter的新数组实例。 |

**示例：**

```ts
class BaseClass {
    private _baseField: string = '';
    public get baseField(): string {
        return this._baseField;
    }
}

class MyClass extends BaseClass {
    private _name: string = '';
    private _age: int = 0;

    public get name(): string {
        return this._name;
    }

    public get age(): int {
        return this._age;
    }
}

let cls = Class.from<MyClass>();
let getters = reflect.getInstanceGettersRecursive(cls);
console.info(getters.length); // 3
for (let getter of getters) {
    console.info(getter.getName()); // "%%get-age", "%%get-name", "%%get-baseField"
}
```

## getInstanceFieldsRecursive

getInstanceFieldsRecursive(targetClass: Class): Array\<InstanceField>

返回类及其父类的所有公共实例字段。

**参数：**

| 参数        | 类型   | 必填 | 说明           |
| ----------- | ------ | ---- | -------------- |
| targetClass | [Class](#class) | 是   | 要获取字段的类。 |

**返回值：**

| 类型   | 说明                             |
| ------ | -------------------------------- |
| Array\<[InstanceField](#instancefield)\> | 包含类所有字段的新数组实例。 |

**示例：**

```ts
class BaseClass {
    public baseField: string = 'base';
}

class MyClass extends BaseClass {
    public name: string = 'Alice';
    public age: int = 30;
    public city: string = 'Beijing';
}

let cls = Class.from<MyClass>();
let fields = reflect.getInstanceFieldsRecursive(cls);
console.info(fields.length); // 4
for (let field of fields) {
    console.info(field.getName()); // "baseField", "name", "age", "city"
}
```

## Class

用于描述运行时类型的类。

### 静态属性

| 名称                   | 类型    | 只读  | 可选  | 说明                     |
| --------------------- | ----- | --- | --- | ---------------------- |
| PRIMITIVE_BOOLEAN     | Class | 是   | 否   | boolean基本类型的Class对象。 |
| PRIMITIVE_BYTE        | Class | 是   | 否   | byte基本类型的Class对象。    |
| PRIMITIVE_CHAR        | Class | 是   | 否   | char基本类型的Class对象。    |
| PRIMITIVE_SHORT       | Class | 是   | 否   | short基本类型的Class对象。   |
| PRIMITIVE_INT         | Class | 是   | 否   | int基本类型的Class对象。     |
| PRIMITIVE_LONG        | Class | 是   | 否   | long基本类型的Class对象。    |
| PRIMITIVE_FLOAT       | Class | 是   | 否   | float基本类型的Class对象。   |
| PRIMITIVE_DOUBLE      | Class | 是   | 否   | double基本类型的Class对象。  |
| PRIMITIVE_NUMBER      | Class | 是   | 否   | number基本类型的Class对象。  |
| PRIMITIVE_VOID        | Class | 是   | 否   | void类型的Class对象。        |

### getName

getName(): string

获取类名。

**返回值：**

| 类型     | 说明     |
| -------- | -------- |
| string   | 类名。   |

**示例：**

```ts
class MyClass {}
let clazz = Class.of(new MyClass());
let name = clazz.getName();
console.info(name); // "MyClass"
```

### getSuper

getSuper(): Class | undefined

获取此类的父类。

**返回值：**

| 类型            | 说明           |
| --------------- | -------------- |
| Class \| undefined | 父类，如果没有父类则返回undefined。 |

**示例：**

```ts
class MyClass {}
let clazz = Class.of(new MyClass());
let superClazz = clazz.getSuper();
console.info(superClazz!.getName()); // "std.core.Object"
```

### isSubtypeOf

isSubtypeOf(other: Class): boolean

检查此类是否是另一个类的子类型。

**参数：**

| 参数   | 类型   | 必填 | 说明           |
| ------ | ------ | ---- | -------------- |
| other  | Class  | 是   | 要比较的类。    |

**返回值：**

| 类型    | 说明                                             |
| ------- | ------------------------------------------------ |
| boolean | 如果此类是other的子类型返回true，否则返回false。   |

**示例：**

```ts
class ParentClass {}
class ChildClass extends ParentClass {}
let childClazz = Class.from<ChildClass>();
let parentClazz = Class.from<ParentClass>();
let isSubtype = childClazz.isSubtypeOf(parentClazz);
console.info(isSubtype); // true
```

### getLinker

getLinker(): RuntimeLinker

获取与此类关联的运行时链接器。

**返回值：**

| 类型           | 说明             |
| -------------- | ---------------- |
| RuntimeLinker  | 此类的运行时链接器。 |

**示例：**

```ts
class MyClass {}
let clazz = Class.from<MyClass>();
let linker = clazz.getLinker();
console.info(linker != undefined); // true
let cls = linker!.loadClass('std.core.Map');
console.info(cls!.getName()); // "std.core.Map"
```

### getFixedArrayComponentType

getFixedArrayComponentType(): Class | undefined

如果此类是定长数组，获取其组件类型。

**返回值：**

| 类型            | 说明                                           |
| --------------- | ---------------------------------------------- |
| Class \| undefined | 定长数组的组件类型，如果不是定长数组则返回undefined。 |

**示例：**

```ts
let arr: FixedArray<int> = [1, 2, 3];
let cls = Class.of(arr).getFixedArrayComponentType();
console.info(cls!.getName()); // "i32"
```

### getInterfaces

getInterfaces(): FixedArray\<Class>

获取此类实现的所有接口。

**返回值：**

| 类型                | 说明                     |
| ------------------- | ------------------------ |
| FixedArray\<Class\> | 此类实现的接口数组。 |

**示例：**

```ts
class MyClass implements JsonSerializable, ArrayLike<string> {
    private arr: Array<String>;
    public constructor() {
        this.arr = Array.create<string>(100, '');
    }
    public constructor(arr: Array<String>) {
        this.arr = arr;
    }
    public $_get(index: int): string {
        return this.arr[index];
    }
    public $_set(index: int, val: string): void {
        this.arr[index] = val;
    }
    public get length(): int {
        return this.arr.length;
    }
    public toJSON(): String {
        return this.arr.join();
    }
}
let cls = Class.from<MyClass>();
let arr = cls.getInterfaces();
console.info(arr[0].getName()); // "std.core.JsonSerializable"
console.info(arr[1].getName()); // "std.core.ArrayLike"
```

### initialize

initialize(): void

如果此类未初始化，则首次使用时将调用类初始化器。

**示例：**

```ts
class MyClass {}
let cls = Class.from<MyClass>();
cls.initialize();
```

### ofAny

static ofAny(obj: Any): Class | undefined

获取任意类型对象的类。

**参数：**

| 参数 | 类型 | 必填 | 说明           |
| ---- | ---- | ---- | -------------- |
| obj  | Any  | 是   | 要获取类的对象。 |

**返回值：**

| 类型            | 说明                                       |
| --------------- | ------------------------------------------ |
| Class \| undefined | 对象的类，如果对象不是类实例则返回undefined。 |

**示例：**

```ts
let obj: Any = new Map<int, string>();
let cls = Class.ofAny(obj);
console.info(cls!.getName()); // "std.core.Map"
```

### of

static of(obj: Object | null): Class

获取对象的类。

**参数：**

| 参数 | 类型           | 必填 | 说明           |
| ---- | -------------- | ---- | -------------- |
| obj  | Object \| null | 是   | 要获取类的对象。 |

**返回值：**

| 类型   | 说明         |
| ------ | ------------ |
| Class  | 对象的类。   |

**示例：**

```ts
let obj = new Map<int, string>();
let cls = Class.of(obj);
console.info(cls.getName()); // "std.core.Map"
```

### from

static from\<T>(): Class

在不创建对象的情况下获取指定类型的类。

**返回值：**

| 类型   | 说明         |
| ------ | ------------ |
| Class  | 指定类型的类。 |

**示例：**

```ts
let cls = Class.from<Map<int, string>>();
console.info(cls.getName()); // "std.core.Map"
```

### current

static current(): Class

获取当前类。

**返回值：**

| 类型   | 说明     |
| ------ | -------- |
| Class  | 当前类。 |

**示例：**

```ts
class MyClass {
    public getClass(): Class {
        return Class.current();
    }
}
let obj = new MyClass();
let cls = obj.getClass();
console.info(cls.getName()); // "MyClass"
```

### ofCaller

static ofCaller(): Class | undefined

获取调用者的类。

**返回值：**

| 类型            | 说明                                      |
| --------------- | ----------------------------------------- |
| Class \| undefined | 调用者的类，如果没有调用者托管帧则返回undefined。 |

**示例：**

```ts
class A {
    public test(): boolean {
        return new B().testCaller();
    }
}
class B {
    public testCaller(): boolean {
        if (Class.ofCaller() == Class.from<A>()) { // 判断是否被A类调用
            return true;
        } else {
            return false;
        }
    }
}
class C {
    public test(): boolean {
        return new B().testCaller();
    }
}
console.info(new A().test()); // true
console.info(new C().test()); // false
```

### createInstance

createInstance(): Object

创建此类的新实例并调用其默认构造函数（无参数）。

**返回值：**

| 类型    | 说明                 |
| ------- | -------------------- |
| Object  | 此类的新实例。        |

**异常：**

| 错误             | 说明                                        |
| ---------------- | ------------------------------------------- |
| Error            | 类不可实例化或没有公共默认构造函数时抛出。     |
| Error            | 类之前未初始化且初始化失败时抛出。            |
| Error            | 构造函数抛出异常时抛出。                      |
| OutOfMemoryError | 内存不足无法分配对象时抛出。                 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let obj = cls.createInstance() as MyClass;
console.info(obj.name); // "test"
```

### getDescriptor

getDescriptor(): string

获取类的描述符。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 类的描述符。 |

**示例：**

```ts
let cls = Class.from<Set<string>>();
console.info(cls.getDescriptor()); // "Lstd/core/Set;"
```

### isEnum

isEnum(): boolean

检查当前类是否是枚举。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果此类是枚举返回true，否则返回false。 |

**示例：**

```ts
enum TestEnum {
    CLASS,
    METHOD
}
let cls = Class.from<TestEnum>();
console.info(cls.isEnum()); // true

let cls2 = Class.from<Set<int>>();
console.info(cls2.isEnum()); // false
```


### isInterface

isInterface(): boolean

检查当前类是否是接口。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果此类是接口返回true，否则返回false。 |

**示例：**

```ts
let cls = Class.from<ArrayLike<int>>();
console.info(cls.isInterface()); // true

let cls2 = Class.from<Array<int>>();
console.info(cls2.isInterface()); // false
```

### isFixedArray

isFixedArray(): boolean

检查此类是否是长度固定的数组（元素数量在创建时确定且不可变的数组）。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果此类是定长数组返回true，否则返回false。 |

**示例：**

```ts
let arr = new FixedArray<int>(1);
let cls = Class.of(arr);
console.info(cls.isFixedArray()); // true

let arr2 = new Array<int>();
let cls2 = Class.of(arr2);
console.info(cls2.isFixedArray()); // false
```

### isUnion

isUnion(): boolean

检查此类是否是联合类型。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果此类是联合类型返回true，否则返回false。 |

**示例：**

```ts
let cls = Class.from<int | string>();
console.info(cls.isUnion()); // true
console.info(cls.getName()); // "{Ustd.core.Int,std.core.String}"
```

### isFinal

isFinal(): boolean

检查此类是否是final类。

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 如果此类是final类返回true，否则返回false。 |

**示例：**

```ts
final class MyClass {}
let cls = Class.from<MyClass>();
console.info(cls.isFinal()); // true
```

### isAbstract

isAbstract(): boolean

检查此类是否是抽象类。

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 如果此类是抽象类返回true，否则返回false。 |

**示例：**

```ts
abstract class MyClass {}
let cls = Class.from<MyClass>();
console.info(cls.isAbstract()); // true
```

### isPrimitive

isPrimitive(): boolean

检查此类是否是基本类型。基本类型请参考[基本类型列表](#静态属性)

**返回值：**

| 类型    | 说明                                 |
| ------- | ------------------------------------ |
| boolean | 如果此类是基本类型返回true，否则返回false。 |

**示例：**

```ts
// boolean、byte、char、short、int、long、float、double这些类型都是false
let cls = Class.from<boolean>();
console.info(cls.isPrimitive()); // false

console.info(Class.PRIMITIVE_BOOLEAN.isPrimitive()); // true
```

### getInstanceMethods

getInstanceMethods(): FixedArray\<reflect.InstanceMethod>

获取当前类中所有声明的public实例方法（包括从接口继承的public实例方法）。

**返回值：**

| 类型                                | 说明             |
| ----------------------------------- | ---------------- |
| FixedArray\<[reflect.InstanceMethod](#instancemethod)\> | 实例方法数组。   |

**示例：**

```ts
class ParentClass {
    public sayHello(): string {
        return "sayHello";
    }
}
interface MyInterface {
    sayHi(): string;
}
class MyClass extends ParentClass implements MyInterface{
    public test(): string {
        return "test";
    }
    public test(msg: string): string {
        return msg;
    }
    private privateMethod(msg: string): string { // 私有方法不能反射
        return msg;
    }
    public sayHi(): string {
        return "sayHi";
    }
}
let cls = Class.from<MyClass>();
let methods = cls.getInstanceMethods();
console.info(methods.length); // 3

methods = cls.getSuper()!.getInstanceMethods();
console.info(methods.length); // 1
```


### getInstanceMethod

getInstanceMethod(name: string, signature?: FixedArray\<Class>): reflect.InstanceMethod | undefined

在类声明的方法中查找指定的public实例方法（包括从接口继承的public实例方法）。

**参数：**

| 参数      | 类型                        | 必填 | 说明                   |
| --------- | --------------------------- | ---- | ---------------------- |
| name      | string                      | 是   | 要查找的方法名。         |
| signature | FixedArray\<Class\>         | 否   | 定义方法签名的参数类型数组。 |

**返回值：**

| 类型                                      | 说明                               |
| ----------------------------------------- | ---------------------------------- |
| [reflect.InstanceMethod](#instancemethod) \| undefined       | 找到的实例方法，未找到则返回undefined。 |

**异常：**

| 错误   | 说明                       |
| ------ | -------------------------- |
| Error  | 当省略signature且存在多个重载时抛出。 |

**示例：**

```ts
class ParentClass {
    public sayHello(): string {
        return "sayHello";
    }
}
interface MyInterface {
    sayHi(): string;
}
class MyClass extends ParentClass implements MyInterface{
    public test(): string {
        return "test";
    }
    public test(msg: string): string {
        return msg;
    }
    private privateMethod(msg: string): string { // 私有方法不能反射
        return msg;
    }
    public sayHi(): string {
        return "sayHi";
    }
}

let obj = new MyClass();
let cls = Class.from<MyClass>();
let m1 = cls.getInstanceMethod('test', [Class.from<string>()]);
console.info(m1!.invoke(obj, ['msg'])); // "msg"

let m2 = cls.getInstanceMethod('test', []);
console.info(m2!.invoke(obj)); // "test"

let m3 = cls.getInstanceMethod('privateMethod', [Class.from<string>()]);
console.info(m3 == undefined); // true

let m4 = cls.getInstanceMethod('sayHi');
console.info(m4!.invoke(obj)); // "sayHi"

let m5 = cls.getInstanceMethod('sayHello');
console.info(m5 == undefined); // true

let m6 = cls.getSuper()!.getInstanceMethod('sayHello');
console.info(m6!.invoke(obj)); // "sayHello"
```

### getStaticMethods

getStaticMethods(): FixedArray\<reflect.StaticMethod>

获取所有此类中声明的public静态方法。

**返回值：**

| 类型                              | 说明           |
| --------------------------------- | -------------- |
| FixedArray\<[reflect.StaticMethod](#staticmethod)\> | 静态方法数组。 |

**示例：**

```ts
class ParentClass {
    public static sayHello(): string {
        return "sayHello";
    }
}
class MyClass extends ParentClass{
    public static test(): string {
        return "no param";
    }
    public static test(msg: string): string {
        return msg;
    }
    private static privateMethod(msg: string): string { // 私有方法不能反射
        return msg;
    }
}
let cls = Class.from<MyClass>();
let methods = cls.getStaticMethods();
console.info(methods.length); // 2

methods = cls.getSuper()!.getStaticMethods();
console.info(methods.length); // 1
```

### getStaticMethod

getStaticMethod(name: string, signature?: FixedArray\<Class>): reflect.StaticMethod | undefined

在此类声明的方法中查找指定的public静态方法。

**参数：**

| 参数      | 类型                        | 必填 | 说明                   |
| --------- | --------------------------- | ---- | ---------------------- |
| name      | string                      | 是   | 要查找的方法名。         |
| signature | FixedArray\<Class\>         | 否   | 定义方法签名的参数类型数组。 |

**返回值：**

| 类型                                    | 说明                             |
| --------------------------------------- | -------------------------------- |
| [reflect.StaticMethod](#staticmethod) \| undefined       | 找到的静态方法，未找到则返回undefined。 |

**异常：**

| 错误  | 说明                       |
| ----- | -------------------------- |
| Error | 当省略signature且存在多个重载时抛出。 |

**示例：**

```ts
class ParentClass {
    public static sayHello(): string {
        return "sayHello";
    }
}
class MyClass extends ParentClass{
    public static test(): string {
        return "no param";
    }
    public static test(msg: string): string {
        return msg;
    }
    private static privateMethod(msg: string): string { // 私有方法不能反射
        return msg;
    }
}
let cls = Class.from<MyClass>();
let m1 = cls.getStaticMethod('test', [Class.from<string>()]);
console.info(m1!.invoke(['test'])); // "test"

let m2 = cls.getStaticMethod('test', []);
console.info(m2!.invoke()); // "no param"

let m3 = cls.getStaticMethod('privateMethod', [Class.from<string>()]);
console.info(m3 == undefined); // true

let m4 = cls.getStaticMethod('sayHello');
console.info(m4 == undefined); // true

let m5 = cls.getSuper()!.getStaticMethod('sayHello');
console.info(m5!.invoke()); // "sayHello"
```

### getInstanceFields

getInstanceFields(): FixedArray\<reflect.InstanceField>

获取当前类中所有声明的public实例字段。

**返回值：**

| 类型                                | 说明           |
| ----------------------------------- | -------------- |
| FixedArray\<[reflect.InstanceField](#instancefield)\> | 实例字段数组。 |

**示例：**

```ts
class ParentClass {
    public age: int = 0;
    private address: string = ''; // 私有字段不能反射
}
class MyClass extends ParentClass {
    public name = 'class name';
    private remark = ''; // 私有字段不能反射
}
let cls = Class.from<MyClass>();
let fields = cls.getInstanceFields();
console.info(fields.length); // 1

fields = cls.getSuper()!.getInstanceFields();
console.info(fields.length); // 1
```

### getInstanceField

getInstanceField(name: string): reflect.InstanceField | undefined

在当前类声明的字段中按名称查找public实例字段。

**参数：**

| 参数  | 类型   | 必填 | 说明           |
| ----- | ------ | ---- | -------------- |
| name  | string | 是   | 要查找的字段名。 |

**返回值：**

| 类型                                      | 说明                             |
| ----------------------------------------- | -------------------------------- |
| [reflect.InstanceField](#instancefield) \| undefined       | 找到的实例字段，未找到则返回undefined。 |

**示例：**

```ts
class ParentClass {
    public age: int = 0;
    private address: string = ''; // 私有字段不能反射
}
class MyClass extends ParentClass {
    public name = 'class name';
    private remark = ''; // 私有字段不能反射
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField('name');
console.info(field!.getName()); // "name"

field = cls.getInstanceField('remark');
console.info(field == undefined); // true

field = cls.getInstanceField('age');
console.info(field == undefined); // true

field = cls.getSuper()!.getInstanceField('age');
console.info(field!.getName()); // "age"
```

### getStaticFields

getStaticFields(): FixedArray\<reflect.StaticField>

获取当前类中所有声明的public静态字段。

**返回值：**

| 类型                              | 说明           |
| --------------------------------- | -------------- |
| FixedArray\<[reflect.StaticField](#staticfield)\> | 静态字段数组。 |

**示例：**

```ts
class ParentClass {
    public static age: int = 0;
    private static address: string = ''; // 私有字段不能反射
}
class MyClass extends ParentClass {
    public static name = 'class name';
    private static remark = ''; // 私有字段不能反射
}
let cls = Class.from<MyClass>();
let fields = cls.getStaticFields();
console.info(fields.length); // 1

fields = cls.getSuper()!.getStaticFields();
console.info(fields.length); // 1
```

### getStaticField

getStaticField(name: string): reflect.StaticField | undefined

在此类声明的字段中按名称查找public静态字段。

**参数：**

| 参数  | 类型   | 必填 | 说明           |
| ----- | ------ | ---- | -------------- |
| name  | string | 是   | 要查找的字段名。 |

**返回值：**

| 类型                                    | 说明                             |
| --------------------------------------- | -------------------------------- |
| [reflect.StaticField](#staticfield) \| undefined       | 找到的静态字段，未找到则返回undefined。 |

**示例：**

```ts
class ParentClass {
    public static age: int = 0;
    private static address: string = ''; // 私有字段不能反射
}
class MyClass extends ParentClass {
    public static name = 'class name';
    private static remark = ''; // 私有字段不能反射
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField('name');
console.info(field!.getName()); // "name"

field = cls.getStaticField('remark');
console.info(field == undefined); // true

field = cls.getStaticField('age');
console.info(field == undefined); // true

field = cls.getSuper()!.getStaticField('age');
console.info(field!.getName()); // "age"
```

### getConstructors

getConstructors(): FixedArray\<reflect.Constructor>

获取此类中所有声明的public构造函数。

**返回值：**

| 类型                            | 说明             |
| ------------------------------- | ---------------- |
| FixedArray\<[reflect.Constructor](#constructor)\> | 构造函数数组。   |

```ts
class MyClass {
    public name = 'class name';

    private constructor() {} // 私有构造函数不能反射

    public constructor(name: string) {
        this.name = name;
    }
}

let cls = Class.from<MyClass>();
let methods = cls.getConstructors();
console.info(methods.length); // 1
```

### getUnionConstituentTypes

getUnionConstituentTypes(): FixedArray\<Class> | undefined

获取联合类型的所有组成类型。

**返回值：**

| 类型                        | 说明                                      |
| --------------------------- | ----------------------------------------- |
| FixedArray\<Class\> \| undefined | 组成联合类型的各个成员类型的数组，如果不是联合类型则返回undefined。 |

```ts
let cls = Class.from<int | string | Array<double>>();
let arr = cls.getUnionConstituentTypes()!;
for (let i = 0; i < arr.length; i++) {
    console.info(arr[i].getName()); // "std.core.Array", "std.core.Int", "std.core.String"
}
```

## InstanceField

表示类或接口的实例字段。

### isReadonly

isReadonly(): boolean

检查字段是否是只读字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是只读字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public readonly name = 'test';
    public count = 0;
}
let cls = Class.from<MyClass>();
let field1 = cls.getInstanceField("name");
let field2 = cls.getInstanceField("count");
console.info(field1!.isReadonly()); // true
console.info(field2!.isReadonly()); // false
```

### isPublic

isPublic(): boolean

检查字段是否是public字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是public字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
console.info(field!.isPublic()); // true
```

### isPrivate

isPrivate(): boolean

检查字段是否是private字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是private字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
console.info(field!.isPrivate()); // false
```

### isProtected

isProtected(): boolean

检查字段是否是protected字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是protected字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
console.info(field!.isProtected()); // false
```

### getType

getType(): Class

获取字段的类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| [Class](#class)  | 表示字段类型的类对象。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
    public count = 0;
}
let cls = Class.from<MyClass>();
let field1 = cls.getInstanceField("name");
let field2 = cls.getInstanceField("count");
console.info(field1!.getType().getName()); // "std.core.String"
console.info(field2!.getType().getName()); // "i32"
```

### getOwner

getOwner(): Class

获取声明此字段的类或接口。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| [Class](#class)  | 声明此字段的类对象。 |

**示例：**

```ts
class ParentClass {
    public name = 'parent';
}
class MyClass extends ParentClass {
    public name = 'test';
    public count = 0;
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("count");
console.info(field!.getOwner().getName()); // "MyClass"
```

### getName

getName(): string

获取字段的名称。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 字段的名称。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
console.info(field!.getName()); // "name"
```

### equals

equals(other: InstanceField): boolean

比较当前实例字段是否与给定的实例字段相等。

**参数：**

| 参数  | 类型            | 必填 | 说明                               |
| ----- | --------------- | ---- | ---------------------------------- |
| other | InstanceField   | 是   | 用于比较的另一个InstanceField对象。 |

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果两个实例字段相等返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let cls = Class.from<MyClass>();
let field1 = cls.getInstanceField("name");
let field2 = cls.getInstanceField("name");
console.info(field1!.equals(field2!)); // true
console.info(field1! === field2!); // false
```

### getValue

getValue(thisObj: Object): Any

从实例字段中读取值。

**参数：**

| 参数    | 类型   | 必填 | 说明                         |
| ------- | ------ | ---- | ---------------------------- |
| thisObj | Object | 是   | 作为`this`上下文的目标对象。 |

**返回值：**

| 类型 | 说明                       |
| ---- | -------------------------- |
| Any  | 从实例字段中读取的值。      |

**异常：**

| 错误      | 说明                             |
| --------- | -------------------------------- |
| TypeError | 当`thisObj`与字段不兼容时抛出。   |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let obj = new MyClass();
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
let value = field!.getValue(obj);
console.info(value); // "test"
```

### setValue

setValue(thisObj: Object, value: Any): void

向实例字段中写入值。

**参数：**

| 参数    | 类型   | 必填 | 说明                         |
| ------- | ------ | ---- | ---------------------------- |
| thisObj | Object | 是   | 目标对象。 |
| value   | Any    | 是   | 要写入的值。                 |

**异常：**

| 错误      | 说明                                         |
| --------- | -------------------------------------------- |
| TypeError | 当`thisObj`与字段不兼容时抛出。               |
| TypeError | 当值类型不匹配时抛出。                       |
| TypeError | 当字段是只读字段时抛出。                     |

**示例：**

```ts
class MyClass {
    public name = 'test';
}
let obj = new MyClass();
let cls = Class.from<MyClass>();
let field = cls.getInstanceField("name");
field!.setValue(obj, "new value");
console.info(obj.name); // "new value"
```

## StaticField

表示类的静态字段。

### isReadonly

isReadonly(): boolean

检查字段是否是只读字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是只读字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static readonly name = 'test';
    public static count = 0;
}
let cls = Class.from<MyClass>();
let field1 = cls.getStaticField("name");
let field2 = cls.getStaticField("count");
console.info(field1!.isReadonly()); // true
console.info(field2!.isReadonly()); // false
```

### isPublic

isPublic(): boolean

检查字段是否是public字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是public字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("name");
console.info(field!.isPublic()); // true
```

### isPrivate

isPrivate(): boolean

检查字段是否是private字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是private字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("name");
console.info(field!.isPrivate()); // false
```

### isProtected

isProtected(): boolean

检查字段是否是protected字段。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是protected字段返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("name");
console.info(field!.isProtected()); // false
```

### getType

getType(): Class

获取字段的类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| [Class](#class)  | 表示字段类型的类对象。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
    public static count = 0;
}
let cls = Class.from<MyClass>();
let field1 = cls.getStaticField("name");
let field2 = cls.getStaticField("count");
console.info(field1!.getType().getName()); // "std.core.String"
console.info(field2!.getType().getName()); // "i32"
```

### getOwner

getOwner(): Class

获取声明此字段的类或接口。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| [Class](#class)  | 声明此字段的类对象。 |

**示例：**

```ts
class ParentClass {
    public static name = 'parent';
}
class MyClass extends ParentClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("name");
console.info(field!.getOwner().getName()); // "MyClass"
```

### getName

getName(): string

获取字段的名称。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 字段的名称。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("name");
console.info(field!.getName()); // "name"
```

### equals

equals(other: StaticField): boolean

比较当前StaticField对象是否与另一个对象相等。

**参数：**

| 参数  | 类型          | 必填 | 说明                             |
| ----- | ------------- | ---- | -------------------------------- |
| other | StaticField   | 是   | 用于比较的另一个StaticField对象。 |

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果两个对象相等返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static name = 'test';
}
let cls = Class.from<MyClass>();
let field1 = cls.getStaticField("name");
let field2 = cls.getStaticField("name");
console.info(field1!.equals(field2!)); // true
console.info(field1! === field2!); // false
```

### getValue

getValue(): Any

从静态字段中读取值。

**返回值：**

| 类型 | 说明                   |
| ---- | ---------------------- |
| Any  | 静态字段的值。         |

**异常：**

| 错误              | 说明                               |
| ----------------- | ---------------------------------- |
| OutOfMemoryError  | 如果没有内存分配返回值时抛出。     |

**示例：**

```ts
class MyClass {
    public static count = 0;
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("count");
let value = field!.getValue();
console.info(value); // 0
```

### setValue

setValue(value: Any): void

向静态字段中写入值。

**参数：**

| 参数  | 类型 | 必填 | 说明         |
| ----- | ---- | ---- | ------------ |
| value | Any  | 是   | 要写入的值。 |

**异常：**

| 错误      | 说明                             |
| --------- | -------------------------------- |
| TypeError | 当值类型不兼容时抛出。           |
| TypeError | 当字段是只读字段时抛出。         |

**示例：**

```ts
class MyClass {
    public static count = 0;
}
let cls = Class.from<MyClass>();
let field = cls.getStaticField("count");
field!.setValue(10);
console.info(MyClass.count); // 10
```

## InstanceMethod

表示类或接口的实例方法。

### getName

getName(): string

获取方法的名称。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 方法的名称。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.getName()); // "test"
```

### getOwner

getOwner(): Class

获取声明此方法的类或接口。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| [Class](#class)  | 声明此方法的类对象。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.getOwner().getName()); // "MyClass"
```

### getReturnType

getReturnType(): Class

获取方法的返回类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| [Class](#class)  | 表示方法返回类型的类对象。 |

**示例：**

```ts
class MyClass {
    public test(): string {
        return "test";
    }
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.getReturnType().getName()); // "std.core.String"
```

### getParameterTypes

getParameterTypes(): FixedArray\<Class>

获取所有参数的类型。

**返回值：**

| 类型                | 说明               |
| ------------------- | ------------------ |
| FixedArray\<[Class](#class)\> | 包含所有参数类型的数组。 |

**示例：**

```ts
class MyClass {
    public test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
let paramTypes = method!.getParameterTypes();
console.info(paramTypes.length); // 2
console.info(paramTypes[0].getName()); // "i32"
console.info(paramTypes[1].getName()); // "std.core.String"
```

### getParameterType

getParameterType(idx: int): Class | undefined

通过索引获取指定位置参数的类型。

**参数：**

| 参数 | 类型 | 必填 | 说明               |
| ---- | ---- | ---- | ------------------ |
| idx  | int  | 是   | 参数的索引位置。    |

**返回值：**

| 类型            | 说明                                            |
| --------------- | ----------------------------------------------- |
| [Class](#class) \| undefined | 指定索引位置的参数类型的类对象，索引无效时返回undefined。 |

**示例：**

```ts
class MyClass {
    public test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
let paramType = method!.getParameterType(0);
console.info(paramType!.getName()); // "i32"
```

### getParametersNum

getParametersNum(): int

获取方法参数的数量。

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| int  | 方法参数的数量。    |

**示例：**

```ts
class MyClass {
    public test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.getParametersNum()); // 2
```

### isNative

isNative(): boolean

检查方法是否是native方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是native方法返回true，否则返回false。 |

**示例：**

```ts
let cls = Class.from<Array<int>>();
let method = cls.getInstanceMethod("$_set");
console.info(method!.isNative()); // true
```

### isPublic

isPublic(): boolean

检查方法是否是public方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是public方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isPublic()); // true
```

### isPrivate

isPrivate(): boolean

检查方法是否是private方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是private方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isPrivate()); // false
```

### isProtected

isProtected(): boolean

检查方法是否是protected方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是protected方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isProtected()); // false
```

### isFinal

isFinal(): boolean

检查方法是否是final方法。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果是final方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public final test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isFinal()); // true
```

### isAsync

isAsync(): boolean

检查方法是否是异步方法。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果是异步方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public async test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isAsync()); // true
```

### isAbstract

isAbstract(): boolean

检查方法是否是抽象方法。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果是抽象方法返回true，否则返回false。 |

**示例：**

```ts
abstract class MyClass {
    public abstract test(): void;
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test");
console.info(method!.isAbstract()); // true
```

### isGetter

isGetter(): boolean

检查方法是否是getter方法。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果是getter方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    private _name: string = '';
    public get name(): string {
        return this._name;
    }
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("%%get-name");
console.info(method!.isGetter()); // true
```

### isSetter

isSetter(): boolean

检查方法是否是setter方法。

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果是setter方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    private _name: string = '';
    public set name(value: string) {
        this._name = value;
    }
}
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("%%set-name");
console.info(method!.isSetter()); // true
```

### equals

equals(other: InstanceMethod): boolean

比较两个实例方法是否相等。

**参数：**

| 参数  | 类型            | 必填 | 说明                   |
| ----- | --------------- | ---- | ---------------------- |
| other | InstanceMethod  | 是   | 用于比较的另一个实例方法对象。 |

**返回值：**

| 类型    | 说明                     |
| ------- | ------------------------ |
| boolean | 如果两个方法相等返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public test() {}
}
let method1 = Class.of(new MyClass()).getInstanceMethod("test");
let method2 = Class.of(new MyClass()).getInstanceMethod("test");
console.info(method1!.equals(method2!)); // true
```

### invoke

invoke(thisObj: Object, args?: FixedArray\<Any>): Any

调用此实例方法。

**参数：**

| 参数    | 类型                | 必填 | 说明                               |
| ------- | ------------------- | ---- | ---------------------------------- |
| thisObj | Object              | 是   | 调用方法时使用的this对象。          |
| args    | FixedArray\<Any\>   | 否   | 调用方法时传递的参数数组。          |

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Any  | 方法的执行结果。 |

**异常：**

| 错误      | 说明                                         |
| --------- | -------------------------------------------- |
| TypeError | 当thisObj与方法不兼容时抛出。                |
| TypeError | 当无法在当前实例的类下获取非虚实例方法时抛出。 |
| TypeError | 当args的数量或类型与方法签名不匹配时抛出。   |

**示例：**

```ts
class MyClass {
    public test(msg: string): string {
        return "Hello " + msg;
    }
}
let obj = new MyClass();
let cls = Class.from<MyClass>();
let method = cls.getInstanceMethod("test", [Class.from<string>()]);
let result = method!.invoke(obj, ["World"]);
console.info(result); // "Hello World"
```

## StaticMethod

表示类的静态方法。

### getName

getName(): string

获取方法的名称。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 方法的名称。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.getName()); // "test"
```

### getOwner

getOwner(): Class

获取声明此方法的类或接口。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| [Class](#class)  | 声明此方法的类对象。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.getOwner().getName()); // "MyClass"
```

### getReturnType

getReturnType(): Class

获取方法的返回类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| [Class](#class)  | 表示方法返回类型的类对象。 |

**示例：**

```ts
class MyClass {
    public static test(): string {
        return "test";
    }
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.getReturnType().getName()); // "std.core.String"
```

### getParameterTypes

getParameterTypes(): FixedArray\<Class>

获取所有参数的类型。

**返回值：**

| 类型                | 说明               |
| ------------------- | ------------------ |
| FixedArray\<[Class](#class)\> | 包含所有参数类型的数组。 |

**示例：**

```ts
class MyClass {
    public static test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
let paramTypes = method!.getParameterTypes();
console.info(paramTypes.length); // 2
console.info(paramTypes[0].getName()); // "i32"
console.info(paramTypes[1].getName()); // "std.core.String"
```

### getParameterType

getParameterType(idx: int): Class | undefined

通过索引获取指定位置参数的类型。

**参数：**

| 参数 | 类型 | 必填 | 说明               |
| ---- | ---- | ---- | ------------------ |
| idx  | int  | 是   | 参数的索引位置。    |

**返回值：**

| 类型            | 说明                                            |
| --------------- | ----------------------------------------------- |
| [Class](#class) \| undefined | 指定索引位置的参数类型的类对象，索引无效时返回undefined。 |

**示例：**

```ts
class MyClass {
    public static test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
let paramType = method!.getParameterType(0);
console.info(paramType!.getName()); // "i32"
```

### getParametersNum

getParametersNum(): int

获取方法参数的数量。

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| int  | 方法参数的数量。    |

**示例：**

```ts
class MyClass {
    public static test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.getParametersNum()); // 2
```

### isNative

isNative(): boolean

检查方法是否是native方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是native方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static test(a: int, b: string): void {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.isNative()); // false
```

### isPublic

isPublic(): boolean

检查方法是否是public方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是public方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.isPublic()); // true
```

### isPrivate

isPrivate(): boolean

检查方法是否是private方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是private方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.isPrivate()); // false
```

### isProtected

isProtected(): boolean

检查方法是否是protected方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是protected方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.isProtected()); // false
```

### isAsync

isAsync(): boolean

检查静态方法是否是异步方法。

**返回值：**

| 类型    | 说明                                     |
| ------- | ---------------------------------------- |
| boolean | 如果是异步方法返回true，否则返回false。   |

**示例：**

```ts
class MyClass {
    public static async test() {}
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test");
console.info(method!.isAsync()); // true
```

### isGetter

isGetter(): boolean

检查静态方法是否是属性的getter访问器。

**返回值：**

| 类型    | 说明                                     |
| ------- | ---------------------------------------- |
| boolean | 如果是getter访问器返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    private static _name: string = '';
    public static get name(): string {
        return MyClass._name;
    }
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("%%get-name");
console.info(method!.isGetter()); // true
```

### isSetter

isSetter(): boolean

检查静态方法是否是属性的setter访问器。

**返回值：**

| 类型    | 说明                                     |
| ------- | ---------------------------------------- |
| boolean | 如果是setter访问器返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    private static _name: string = '';
    public static set name(value: string) {
        MyClass._name = value;
    }
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("%%set-name");
console.info(method!.isSetter()); // true
```

### equals

equals(other: StaticMethod): boolean

比较当前StaticMethod对象是否与另一个对象相等。

**参数：**

| 参数  | 类型          | 必填 | 说明                               |
| ----- | ------------- | ---- | ---------------------------------- |
| other | StaticMethod  | 是   | 用于比较的另一个StaticMethod对象。 |

**返回值：**

| 类型    | 说明                                           |
| ------- | ---------------------------------------------- |
| boolean | 如果两个对象指向同一方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public static test() {}
}
let cls = Class.from<MyClass>();
let method1 = cls.getStaticMethod("test");
let method2 = cls.getStaticMethod("test");
console.info(method1!.equals(method2!)); // true
```

### invoke

invoke(args?: FixedArray\<Any>): Any

调用静态方法。

**参数：**

| 参数 | 类型              | 必填 | 说明                 |
| ---- | ----------------- | ---- | -------------------- |
| args | FixedArray\<Any\> | 否   | 方法参数。           |

**返回值：**

| 类型 | 说明                               |
| ---- | ---------------------------------- |
| Any  | 方法返回值，`void`类型方法返回`undefined`。 |

**异常：**

| 错误              | 说明                                     |
| ----------------- | ---------------------------------------- |
| OutOfMemoryError  | 如果没有内存分配返回值时抛出。           |
| TypeError         | 如果参数数量或类型不匹配时抛出。         |

**示例：**

```ts
class MyClass {
    public static test(msg: string): string {
        return "Hello " + msg;
    }
}
let cls = Class.from<MyClass>();
let method = cls.getStaticMethod("test", [Class.from<string>()]);
let result = method!.invoke(["World"]);
console.info(result); // "Hello World"
```

## Constructor

表示类的构造函数。

### getName

getName(): string

获取方法的名称。

**返回值：**

| 类型     | 说明         |
| -------- | ------------ |
| string   | 方法的名称。 |

**示例：**

```ts
class MyClass {
    public constructor(msg: string) {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].getName()); // "constructor"
```

### getOwner

getOwner(): Class

获取声明此方法的类或接口。

**返回值：**

| 类型   | 说明               |
| ------ | ------------------ |
| [Class](#class)  | 声明此方法的类对象。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].getOwner().getName()); // "MyClass"
```

### getReturnType

getReturnType(): Class

获取方法的返回类型。

**返回值：**

| 类型   | 说明                   |
| ------ | ---------------------- |
| [Class](#class)  | 表示方法返回类型的类对象。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].getReturnType().getName()); // "void"
```

### getParameterTypes

getParameterTypes(): FixedArray\<Class>

获取所有参数的类型。

**返回值：**

| 类型                | 说明               |
| ------------------- | ------------------ |
| FixedArray\<[Class](#class)\> | 包含所有参数类型的数组。 |

**示例：**

```ts
class MyClass {
    public constructor(name: string, age: int) {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
let paramTypes = constructors[0].getParameterTypes();
console.info(paramTypes.length); // 2
console.info(paramTypes[0].getName()); // "std.core.String"
console.info(paramTypes[1].getName()); // "i32"
```

### getParameterType

getParameterType(idx: int): Class | undefined

通过索引获取指定位置参数的类型。

**参数：**

| 参数 | 类型 | 必填 | 说明               |
| ---- | ---- | ---- | ------------------ |
| idx  | int  | 是   | 参数的索引位置。    |

**返回值：**

| 类型            | 说明                                            |
| --------------- | ----------------------------------------------- |
| [Class](#class) \| undefined | 指定索引位置的参数类型的类对象，索引无效时返回undefined。 |

**示例：**

```ts
class MyClass {
    public constructor(name: string, age: int) {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
let paramType = constructors[0].getParameterType(0);
console.info(paramType!.getName()); // "std.core.String"
```

### getParametersNum

getParametersNum(): int

获取方法参数的数量。

**返回值：**

| 类型 | 说明               |
| ---- | ------------------ |
| int  | 方法参数的数量。    |

**示例：**

```ts
class MyClass {
    public constructor(name: string, age: int) {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].getParametersNum()); // 2
```

### isNative

isNative(): boolean

检查方法是否是native方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是native方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].isNative()); // false
```

### isPublic

isPublic(): boolean

检查方法是否是public方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是public方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].isPublic()); // true
```

### isPrivate

isPrivate(): boolean

检查方法是否是private方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是private方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].isPrivate()); // false
```

### isProtected

isProtected(): boolean

检查方法是否是protected方法。

**返回值：**

| 类型    | 说明                               |
| ------- | ---------------------------------- |
| boolean | 如果是protected方法返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();
console.info(constructors[0].isProtected()); // false
```

### equals

equals(other: Constructor): boolean

比较当前构造函数对象是否与另一个构造函数对象相等。

**参数：**

| 参数  | 类型         | 必填 | 说明                               |
| ----- | ------------ | ---- | ---------------------------------- |
| other | Constructor  | 是   | 用于比较的另一个构造函数对象。      |

**返回值：**

| 类型    | 说明                                           |
| ------- | ---------------------------------------------- |
| boolean | 如果两个构造函数对象相等返回true，否则返回false。 |

**示例：**

```ts
class MyClass {
    public constructor() {}
}
let cls = Class.from<MyClass>();
let ctor1 = cls.getConstructors()[0];
let ctor2 = cls.getConstructors()[0];
console.info(ctor1.equals(ctor2)); // true
console.info(ctor1 === ctor2); // false
```

### createInstance

createInstance(args?: FixedArray\<Any>): Any

调用此构造函数创建其所属类的新实例。

**参数：**

| 参数 | 类型              | 必填 | 说明                   |
| ---- | ----------------- | ---- | ---------------------- |
| args | FixedArray\<Any\> | 否   | 构造函数的参数列表。    |

**返回值：**

| 类型 | 说明             |
| ---- | ---------------- |
| Any  | 新创建的类实例。  |

**异常：**

| 错误              | 说明                                         |
| ----------------- | -------------------------------------------- |
| OutOfMemoryError  | 当没有足够内存创建对象时抛出。               |
| TypeError         | 当`thisObj`与方法不兼容时抛出。              |
| TypeError         | 当无法在当前实例的类下获取非虚实例方法时抛出。 |
| TypeError         | 当`args`的数量或类型与方法签名不匹配时抛出。 |

**示例：**

```ts
class MyClass {
    public name: string;

    public constructor() {
        this.name = "default";
    }

    public constructor(name: string) {
        this.name = name;
    }
}
let cls = Class.from<MyClass>();
let constructors = cls.getConstructors();

for (let i = 0; i < constructors.length; i++) {
    let ctor = constructors[i];
    if (ctor.getParametersNum() == 1) {
        let obj = ctor.createInstance(["test"]) as MyClass;
        console.info(obj.name); // "test"
    } else {
        let obj = ctor.createInstance() as MyClass;
        console.info(obj.name); // "default"
    }
}
```

## InvocationHandler

用于处理代理对象上调用的接口，定义管理属性访问、赋值和方法调用的方法。

### get

get(proxy: Proxy, method: InstanceMethod): Any

拦截代理对象上每个属性的getter操作。

**参数：**

| 参数   | 类型                            | 必填 | 说明                   |
| ------ | ------------------------------- | ---- | ---------------------- |
| proxy  | [Proxy](#proxy)                 | 是   | 被访问的代理对象。      |
| method | [InstanceMethod](#instancemethod) | 是   | 被拦截的方法。          |

**返回值：**

| 类型 | 说明           |
| ---- | -------------- |
| Any  | 属性的值。      |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
    test(msg: string): string;
}

class MyClass implements MyInterface {
    public name: string = '';
    public age: int = 0;
    public test(msg: string): string {
        return msg;
    }
}

class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        let val = method.invoke(this.target);
        if (!(proxy instanceof MyInterface)) {
            return val;
        }
        let name = method.getName();
        if (name == '%%get-name') {
            return 'hello: ' + (val as string);
        } else if (name =='%%get-age' ) {
            return 10 + (val as int);
        }
        return val;
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        return method.invoke(this.target, args);
    }
}
let obj = new MyClass();
obj.name = 'test';
let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler(obj);
let interfaces: FixedArray<Class> = [Class.from<MyInterface>()];
let proxyObj = reflect.Proxy.create(linker, interfaces, handler) as MyInterface;
console.info(obj.name); // "test"
console.info(proxyObj.name); // "hello: test"
console.info(obj.age); // 0
console.info(proxyObj.age); // 10
```

### set

set(proxy: Proxy, method: InstanceMethod, value: Any): void

拦截代理对象上每个属性的setter操作。

**参数：**

| 参数   | 类型                            | 必填 | 说明                               |
| ------ | ------------------------------- | ---- | ---------------------------------- |
| proxy  | [Proxy](#proxy)                 | 是   | 被修改的代理对象。                  |
| method | [InstanceMethod](#instancemethod) | 是   | 被拦截的方法。                      |
| value  | Any                             | 是   | 通过setter传递的值。        |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
    test(msg: string): string;
}

class MyClass implements MyInterface {
    public name: string = '';
    public age: int = 0;
    public test(msg: string): string {
        return msg;
    }
}

class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        return method.invoke(this.target);
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        return method.invoke(this.target, args);
    }
}

let obj = new MyClass();
let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler(obj);
let interfaces: FixedArray<Class> = [Class.from<MyInterface>()];
let proxyObj = reflect.Proxy.create(linker, interfaces, handler) as MyInterface;
console.info(obj.name); // ""
console.info(obj.age); // 0
proxyObj.name = 'test set';
proxyObj.age = 66;
console.info(obj.name); // "test set"
console.info(obj.age); // 66
```

### invoke

invoke(proxy: Proxy, method: InstanceMethod, args: FixedArray\<Any>): Any

拦截代理对象上方法的调用。

**参数：**

| 参数   | 类型                            | 必填 | 说明                         |
| ------ | ------------------------------- | ---- | ---------------------------- |
| proxy  | [Proxy](#proxy)                 | 是   | 调用方法的代理对象。          |
| method | [InstanceMethod](#instancemethod) | 是   | 被拦截的方法。                |
| args   | FixedArray\<Any\>               | 是   | 传递给方法的参数数组。        |

**返回值：**

| 类型 | 说明             |
| ---- | ---------------- |
| Any  | 方法调用的结果。  |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
    test(msg: string): string;
    sayHello(msg: string): string;
}

class MyClass implements MyInterface {
    public name: string = '';
    public age: int = 0;
    public test(msg: string): string {
        return msg;
    }
    public sayHello(msg: string): string {
        return msg;
    }
}

class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        return method.invoke(this.target);
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        if ((proxy instanceof MyInterface) && method.getName() == 'sayHello') {
            return 'hello: ' + method.invoke(this.target, args);
        }
        return method.invoke(this.target, args);
    }
}
let obj = new MyClass();
let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler(obj);
let interfaces: FixedArray<Class> = [Class.from<MyInterface>()];
let proxyObj = reflect.Proxy.create(linker, interfaces, handler) as MyInterface;
console.info(proxyObj.test('tom')); // "tom"
console.info(proxyObj.sayHello('tom')); // "hello: tom"
```

## Proxy

用于创建代理对象的基类，这些代理对象将方法调用和属性访问委托给InvocationHandler。提供静态方法用于在运行时动态生成代理类和实例化代理对象。


### create

static create(linker: RuntimeLinker, interfaces: FixedArray\<Class>, handler: InvocationHandler): Proxy

创建一个新的代理实例，该实例实现指定的接口并使用提供的处理器。

**参数：**

| 参数       | 类型   | 必填 | 说明                                       |
| ---------- | ------ | ---- | ------------------------------------------ |
| linker     | RuntimeLinker | 是   | 用于在运行时生成代理类的RuntimeLinker。     |
| interfaces | FixedArray\<[Class](#class)\> | 是   | 表示要代理的interface数组。           |
| handler    | [InvocationHandler](#invocationhandler) | 是   | 用于处理方法和属性操作的InvocationHandler。 |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| [Proxy](#proxy) | 作为Proxy的新代理实例。 |

**异常：**

| 错误  | 说明                                 |
| ----- | ------------------------------------ |
| Error | 给定类上不存在预期的构造函数时抛出。 |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
}
class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        return method.invoke(this.target);
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        return method.invoke(this.target, args);
    }
}

let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler({name: 'tom', age: 10} as MyInterface);
let interfaces: FixedArray<Class> = [Class.from<MyInterface>()];
let proxyObj = reflect.Proxy.create(linker, interfaces, handler);
console.info(reflect.Proxy.isProxyClass(Class.ofAny(proxyObj)!)); // true
console.info((proxyObj as MyInterface).name); // "tom"
console.info((proxyObj as MyInterface).age); // 10
```

### getHandler

getHandler(): InvocationHandler

获取与此代理关联的调用处理器。

**返回值：**

| 类型   | 说明                       |
| ------ | -------------------------- |
| [InvocationHandler](#invocationhandler) | 此代理使用的InvocationHandler。 |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
}

class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        return method.invoke(this.target);
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        return method.invoke(this.target, args);
    }
}
let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler({name: 'test', age: 10} as MyInterface);
let proxyObj = reflect.Proxy.create(linker, [Class.from<MyInterface>()], handler);
console.info(proxyObj.getHandler() == handler); // true
```

### isProxyClass

static isProxyClass(klass: Class): boolean

检查类是否由Proxy.create生成。

**参数：**

| 参数  | 类型   | 必填 | 说明           |
| ----- | ------ | ---- | -------------- |
| klass | [Class](#class) | 是   | 要检查是否为代理的类。 |

**返回值：**

| 类型    | 说明                                   |
| ------- | -------------------------------------- |
| boolean | 如果类是代理类返回true，否则返回false。 |

**示例：**

```ts
interface MyInterface {
    name: string;
    age: int;
}

class MyHandler implements reflect.InvocationHandler {
    target: Object;
    public constructor(other: Object) {
        this.target = other;
    }
    public get(proxy: reflect.Proxy, method: reflect.InstanceMethod): Any {
        return method.invoke(this.target);
    }
    public set(proxy: reflect.Proxy, method: reflect.InstanceMethod, value: Any): void {
        method.invoke(this.target, [value]);
    }
    public invoke(proxy: reflect.Proxy, method: reflect.InstanceMethod, args: FixedArray<Any>): Any {
        return method.invoke(this.target, args);
    }
}
let linker = Class.from<MyInterface>().getLinker();
let handler = new MyHandler({name: 'test', age: 10} as MyInterface);
let proxyObj = reflect.Proxy.create(linker, [Class.from<MyInterface>()], handler);
console.info(reflect.Proxy.isProxyClass(Class.of(proxyObj))); // true
console.info(reflect.Proxy.isProxyClass(Class.from<MyInterface>())); // false
```
