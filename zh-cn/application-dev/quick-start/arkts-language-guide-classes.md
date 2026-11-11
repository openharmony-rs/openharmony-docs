---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "讲解ArkTS类的定义与使用，涵盖属性、方法、构造函数、访问控制、继承、抽象类及初始化等面向对象核心特性。"
keywords: [ArkTS, 类, class, 装饰器, 构造函数, 访问控制, 继承, 抽象类, 面向对象]
doctype: guide
status: active
---

# 类
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

类是面向对象编程的核心概念，用于封装数据和行为。ArkTS提供完整的类支持，包括属性、方法、构造函数、继承、访问控制、抽象类、装饰器等特性。

## 类的基础概念

类是面向对象编程的基本构造，封装数据（属性）和行为（方法），通过构造函数初始化实例。

**类的定义语法**

使用`class`关键字定义类，在花括号内声明属性、构造函数和方法。类可以作为类型标注使用；空类没有成员，应避免定义。

<!-- @[class_basic_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// 基本类定义
class Person {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  greet(): string {
    return `Hello, I'm ${this.name}`;
  }
}

// 创建实例
let person: Person = new Person('Alice', 25);
console.info(`${person.greet()}`);

// 空类
class EmptyClass {
}

let empty: EmptyClass = new EmptyClass();

// 类作为类型
function processPerson(person: Person): void {
  console.info(`${person.name}`);
}

processPerson(person);
```

**类的核心组成（属性、方法、构造函数）**

属性存储状态，构造函数初始化属性，方法封装行为，三者协同构成类的核心结构。

<!-- @[class_properties_methods_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class User {
  // 属性
  public id: number;
  public name: string;
  public email: string;
  private password: string;
  
  // 构造函数
  constructor(id: number, name: string, email: string) {
    this.id = id;
    this.name = name;
    this.email = email;
    this.password = '';
  }
  
  // 方法
  getInfo(): string {
    return `User ${this.id}: ${this.name} (${this.email})`;
  }
  
  setPassword(password: string): void {
    this.password = password;
  }
  
  validate(): boolean {
    return this.id > 0 && this.name.length > 0;
  }
}

let user: User = new User(1, 'Alice', 'alice@example.com');
console.info(`${user.getInfo()}`);
```

**方法与独立函数的差异**

方法依附于类，可通过`this`访问实例状态和私有成员；独立函数不依附类，无法访问实例状态。方法还支持访问修饰符控制可见性。

<!-- @[standalone_function_vs_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
// 独立函数：不依附于类
function standaloneAdd(a: number, b: number): number {
  return a + b;
}

// 类方法：依附于类，可访问类内部状态
class Accumulator {
  private total: number = 0;
  
  // 方法：可访问私有状态
  add(n: number): void {
    this.total += n;
  }
  
  getTotal(): number {
    return this.total;
  }
  
  // 方法优势：封装和状态管理
  reset(): void {
    this.total = 0;
  }
}

// 差异对比
console.info(`${standaloneAdd(1, 2).toString()}`);  // 3，无状态

let acc: Accumulator = new Accumulator();
acc.add(10);
acc.add(20);
console.info(`${acc.getTotal().toString()}`);  // 30，有状态管理

// 方法可以访问私有数据，函数不能
// 独立函数无法访问acc.total（私有）
```

**类的引用语义**

类的实例是引用类型，赋值和传参传递的是引用而非副本：修改任一变量指向的对象会影响所有引用。

复制对象时，浅拷贝只复制对象自身这一层：基本类型的属性被独立复制，引用类型的属性仍与原对象共享同一实例；深拷贝则逐层复制嵌套的引用类型，使副本完全独立，深拷贝需手动实现。

<!-- @[object_reference_copy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class CopyPerson {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

let person1: CopyPerson = new CopyPerson('Alice', 25);
let person2: CopyPerson = person1;  // 引用赋值，指向同一对象

person2.name = 'Bob';
console.info(`${person1.name}`);  // 'Bob'（person1也被修改）

// 深拷贝需要手动实现，可在类中提供拷贝方法
class CopyUser {
  public id: number;
  public name: string;
  
  constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
  
  copy(): CopyUser {
    return new CopyUser(this.id, this.name);
  }
}

let user1: CopyUser = new CopyUser(1, 'Alice');
let user2: CopyUser = user1.copy();
user2.name = 'Bob';
console.info(`${user1.name}`);  // 'Alice'（深拷贝，修改user2不影响user1）
console.info(`${user2.name}`);  // 'Bob'
```

**浅拷贝与深拷贝**

属性为引用类型时，浅拷贝与深拷贝的差异最为明显：

<!-- @[shallow_vs_deep_copy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// 属性为引用类型时，浅拷贝与深拷贝的差异
class ContactInfo {
  public email: string;
  
  constructor(email: string) {
    this.email = email;
  }
}

class Employee {
  public id: number;
  public contact: ContactInfo;
  
  constructor(id: number, contact: ContactInfo) {
    this.id = id;
    this.contact = contact;
  }
  
  // 浅拷贝：contact仍与原对象共享
  shallowCopy(): Employee {
    return new Employee(this.id, this.contact);
  }
  
  // 深拷贝：contact也复制为新实例
  deepCopy(): Employee {
    return new Employee(this.id, new ContactInfo(this.contact.email));
  }
}

let employee1: Employee = new Employee(1, new ContactInfo('alice@example.com'));

// 浅拷贝：基本类型属性独立，引用类型属性共享
let employee2: Employee = employee1.shallowCopy();
employee2.id = 100;
employee2.contact.email = 'bob@example.com';
console.info(`${employee1.id}`);              // 1（基本类型，独立）
console.info(`${employee1.contact.email}`);   // 'bob@example.com'（引用类型，共享）

// 深拷贝：嵌套的引用类型属性也不受影响
let employee3: Employee = new Employee(2, new ContactInfo('carol@example.com'));
let employee4: Employee = employee3.deepCopy();
employee4.contact.email = 'dave@example.com';
console.info(`${employee3.contact.email}`);   // 'carol@example.com'（引用类型，独立）
```

`===`比较两个引用是否指向同一对象，不比较内容是否相同；需要比较内容时应自定义比较方法。

<!-- @[object_comparison](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Point {
  public x: number;
  public y: number;
  
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let p1: Point = new Point(1, 2);
let p2: Point = new Point(1, 2);
let p3: Point = p1;

// 引用比较
console.info(`${p1 === p2}`);  // false（不同对象）
console.info(`${p1 === p3}`);  // true（同一引用）

// 内容比较需自定义方法
class PointWithEquals {
  public x: number;
  public y: number;
  
  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
  
  equals(other: PointWithEquals): boolean {
    return this.x === other.x && this.y === other.y;
  }
}

let pe1: PointWithEquals = new PointWithEquals(1, 2);
let pe2: PointWithEquals = new PointWithEquals(1, 2);

console.info(`${pe1 === pe2}`);      // false
console.info(`${pe1.equals(pe2)}`);  // true
```

**类之间的类型关系**

TypeScript中类之间的类型兼容性基于结构类型（鸭子类型），结构相同的类可互相替代，即使没有显式继承关系。**ArkTS不支持结构类型**，类之间的赋值必须有显式继承或`implements`关系。

**TypeScript对照**

<!-- @[ts_structural_typing](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript结构类型，ArkTS不支持
class TsRelPoint1 {
  public x: number = 0;
  public y: number = 0;
}

class TsRelPoint2 {
  public x: number = 0;
  public y: number = 0;
}

// 结构相同，可互相赋值（ArkTS不支持）
let tsRelP1: TsRelPoint1 = new TsRelPoint2();
let tsRelP2: TsRelPoint2 = new TsRelPoint1();
console.info(`${tsRelP1.x}`);
```

**嵌套类型**

TypeScript和ArkTS都不支持在类内部声明类。需要把只服务于某个外部类型的辅助类型收束在一起时，应在模块级别与主类并列声明，通过命名体现归属关系；辅助类需要访问外部类的实例数据时，通过构造函数传入引用。

<!-- @[nested_type_grouping](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ProcessorResult {
  public success: boolean = false;
  public data: string = '';
  public error: string = '';

  isSuccess(): boolean {
    return this.success;
  }
}

class NestedDataProcessor {
  process(input: string): ProcessorResult {
    let result: ProcessorResult = new ProcessorResult();
    if (input.length > 0) {
      result.success = true;
      result.data = input.trim();
    } else {
      result.error = 'Empty input';
    }
    return result;
  }
}

let ntProcessor: NestedDataProcessor = new NestedDataProcessor();
let ntResult: ProcessorResult = ntProcessor.process('hello');
console.info(`${ntResult.isSuccess()}`); // true
```

ArkTS不支持类表达式（将类赋值给变量），必须使用类声明，详见[从TypeScript到ArkTS的适配规则](typescript-to-arkts-migration-guide.md#不支持使用类表达式)。

## 类的属性

类的属性描述对象状态，以 `修饰符 名称: 类型 = 初始值` 形式声明，通过 `实例.属性名` 访问。属性分为实例属性和静态属性，并支持计算属性、可选属性、只读属性和默认值。

### 实例属性

实例属性是每个实例独立持有的属性，直接存储对象的数据值，随着实例的创建而存在，通过`实例对象.属性名`访问；类名无法直接访问实例属性。

<!-- @[property_definition_basics](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Person {
  // 属性定义：存储数据
  public name: string;         // 姓名属性
  public age: number;          // 年龄属性
  public email?: string;       // 可选属性
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // 属性的作用：封装数据，提供访问接口
  getInfo(): string {
    return `${this.name}, ${this.age} years old`;
  }
}

let person: Person = new Person('Alice', 25);
console.info(`${person.name}`);  // 'Alice'
console.info(`${person.age.toString()}`);   // 25

// 属性用于存储状态
class Counter {
  public count: number = 0;  // 存储计数状态
  
  increment(): void {
    this.count++;  // 通过属性管理状态
  }
  
  getCount(): number {
    return this.count;
  }
}

let counter: Counter = new Counter();
counter.increment();
console.info(`${counter.getCount().toString()}`);  // 1
```

### 静态属性

静态属性使用`static`关键字声明，属于类本身而非实例：在类加载时创建，所有实例共享，通过`类名.属性名`访问，无需创建实例。实例属性需要通过类实例访问、随实例创建而存在，两者在访问方式和生命周期上有明显区别。静态属性适合全局状态管理等类级别数据，其生命周期与类绑定，无论创建多少实例，静态属性只有一个副本。

<!-- @[instance_vs_static_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Configuration {
  // 实例属性：每个实例独立拥有
  public name: string;
  public value: number;
  
  // 静态属性：所有实例共享
  public static version: string = '1.0.0';
  public static instanceCount: number = 0;
  
  constructor(name: string, value: number) {
    this.name = name;
    this.value = value;
    Configuration.instanceCount++;
  }
  
  // 实例方法访问实例属性
  getInfo(): string {
    return `${this.name}: ${this.value}`;
  }
  
  // 静态方法访问静态属性
  static getVersion(): string {
    return Configuration.version;
  }
  
  static getInstanceCount(): number {
    return Configuration.instanceCount;
  }
}

let config1: Configuration = new Configuration('A', 10);
let config2: Configuration = new Configuration('B', 20);

// 实例属性独立
console.info(`${config1.name}`);  // 'A'
console.info(`${config2.name}`);  // 'B'

// 静态属性共享
console.info(`${Configuration.version}`);       // '1.0.0'
console.info(`${Configuration.instanceCount}`); // 2

// 实例通过this访问实例属性
// 静态通过类名访问静态属性
```

静态初始化块（`static { }`）在类加载时执行一次，适合封装需要错误处理的静态初始化逻辑，可直接访问私有静态字段；也可以改用静态方法显式控制初始化时机。

<!-- @[static_block](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class TsStaticConfig {
  private static count: number = 0;

  static {
    try {
      let data: string[] = ['a', 'b', 'c'];
      TsStaticConfig.count = data.length;
    } catch (e) {
      TsStaticConfig.count = 0;
    }
  }
}
```

**特殊静态成员名称**：类本身是函数，不能使用与`Function`原型冲突的静态成员名称，`name`、`length`、`call`等不能用作静态属性名。

**TypeScript对照**

<!-- @[ts_special_static_names](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class TsSsnConfig {
  static version: string = '1.0';

  static name: string = 'Config';  // 编译错误：与Function.name冲突
  static length: number = 0;       // 编译错误：与Function.length冲突

  static getConfigName(): string {
    return 'Config';
  }
}

console.info(`${TsSsnConfig.version}`);
console.info(`${TsSsnConfig.getConfigName()}`);
```

### 计算属性

计算属性通过`get`/`set`访问器定义：使用`get`关键字定义读取访问器，`set`关键字定义写入访问器，访问时像普通属性一样使用，但底层通过方法动态求值，可在读写时执行验证等自定义逻辑。

<!-- @[getter_setter_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Circle {
  private _radius: number = 0;
  
  // getter：获取计算值
  get radius(): number {
    return this._radius;
  }
  
  // setter：设置值并验证
  set radius(value: number) {
    if (value >= 0) {
      this._radius = value;
    }
  }
  
  // 计算属性：基于其他属性计算
  get area(): number {
    return Math.PI * this._radius * this._radius;
  }
  
  get diameter(): number {
    return this._radius * 2;
  }
  
  get circumference(): number {
    return 2 * Math.PI * this._radius;
  }
}

let circle: Circle = new Circle();

// 通过setter设置
circle.radius = 5;
console.info(`${circle.radius}`);      // 5

// 计算属性自动更新
console.info(`${circle.area}`);        // ~78.54
console.info(`${circle.diameter}`);    // 10
console.info(`${circle.circumference}`); // ~31.42

// setter有验证逻辑
circle.radius = -5;  // 无效，不设置
console.info(`${circle.radius}`);      // 5（保持原值）
```

只提供getter、不提供setter的计算属性为只读计算属性，只能读取不能写入；修改其源属性时，计算属性的值会自动更新。

<!-- @[ts_readonly_computed_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class Rectangle {
  public width: number = 0;
  public height: number = 0;

  // 只读计算属性：仅有getter
  get area(): number {
    return this.width * this.height;
  }

  get perimeter(): number {
    return 2 * (this.width + this.height);
  }

  // 无setter，不可直接设置area
  // set area(value: number) { }  // 不提供
}

let rect: Rectangle = new Rectangle();
rect.width = 10;
rect.height = 20;

console.info(`${rect.area}`);       // 200
console.info(`${rect.perimeter}`);  // 60

// 不可设置计算属性
rect.area = 100;  // 编译错误

// 通过修改源属性影响计算属性
rect.width = 5;
console.info(`${rect.area}`);  // 100（自动更新）
```

存储属性分配字段保存值，计算属性不分配字段，每次访问时通过getter动态求值；计算属性适合派生数据（如由姓和名拼接全名、由摄氏度换算华氏度）。

<!-- @[stored_vs_computed_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class Temperature {
  // 存储属性：直接存储值
  public celsius: number = 0;
  
  // 计算属性：基于存储属性计算
  get fahrenheit(): number {
    return this.celsius * 9 / 5 + 32;
  }
  
  set fahrenheit(value: number) {
    this.celsius = (value - 32) * 5 / 9;
  }
  
  // 存储属性：需要存储空间
  // 计算属性：无需存储空间，动态计算
  
  // 存储属性：直接赋值
  // 计算属性：通过getter/setter
}

let temp: Temperature = new Temperature();

// 设置存储属性
temp.celsius = 25;
console.info(`${temp.celsius}`);      // 25
console.info(`${temp.fahrenheit}`);   // 77

// 设置计算属性，影响存储属性
temp.fahrenheit = 100;
console.info(`${temp.celsius}`);      // ~37.78
console.info(`${temp.fahrenheit}`);   // 100
```

### 可选属性

可选属性使用`?`标记，可以不初始化、可延迟赋值；其值可能为`undefined`，使用前需检查`undefined`或通过`??`提供默认值，也可通过可选链安全访问。

<!-- @[optional_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class UserProfile {
  public name: string;
  public age?: number;          // 可选属性
  public email?: string;
  public bio?: string;
  
  constructor(name: string) {
    this.name = name;
    // 可选属性不必须初始化
  }
  
  setAge(age: number): void {
    this.age = age;
  }
  
  setEmail(email: string): void {
    this.email = email;
  }
  
  getAge(): number {
    return this.age ?? 0;
  }
  
  hasEmail(): boolean {
    return this.email !== undefined;
  }
}

let profile: UserProfile = new UserProfile('Alice');

// age尚未赋值，??提供默认值
console.info(`${profile.getAge()}`);  // 0

profile.setAge(25);
console.info(`${profile.getAge()}`);  // 25

// 可选属性访问需要检查
if (profile.email !== undefined) {
  console.info(`${profile.email}`);
}

// 使用可选链
let bioLength: number | undefined = profile.bio?.length;
console.info(`${bioLength}`);  // undefined
```

### 只读属性

只读属性使用`readonly`关键字声明，只能在声明处或构造函数中赋值，此后不可修改；需要“修改”时返回新实例而非修改原实例。

<!-- @[ts_readonly_instance_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class ImmutablePoint {
  // readonly只读属性
  public readonly x: number;
  public readonly y: number;

  constructor(x: number, y: number) {
    this.x = x;  // 构造函数中可赋值
    this.y = y;
  }

  // 只读属性不可修改
  move(dx: number, dy: number): void {
    this.x += dx;  // 编译错误
    this.y += dy;  // 编译错误
  }

  // 返回新实例而非修改
  translate(dx: number, dy: number): ImmutablePoint {
    return new ImmutablePoint(this.x + dx, this.y + dy);
  }
}

let point: ImmutablePoint = new ImmutablePoint(10, 20);
console.info(`${point.x}`);  // 10
console.info(`${point.y}`);  // 20

// 只读属性不可修改
point.x = 15;  // 编译错误

// 返回新实例
let newPoint: ImmutablePoint = point.translate(5, 5);
console.info(`${newPoint.x}`);  // 15
console.info(`${newPoint.y}`);  // 25

// 原实例不变
console.info(`${point.x}`);  // 10
```

将`readonly`与`static`结合，可以定义类级别不可变的常量。

<!-- @[ts_static_readonly_constants](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
// readonly与static结合
class AppConfig {
  public static readonly APP_NAME: string = 'MyApp';
  public static readonly VERSION: string = '1.0.0';
}

console.info(`${AppConfig.APP_NAME}`);   // 'MyApp'
console.info(`${AppConfig.VERSION}`);    // '1.0.0'

AppConfig.APP_NAME = 'NewApp';  // 编译错误
```

### 属性默认值

属性默认值在属性声明处（如`public name: string = 'default'`）直接给出，未提供值时使用预设值，避免出现`undefined`。属性初始化的时机有三种：声明时赋值适合固定默认值，构造函数体内赋值适合依赖参数或需要动态计算的值，可空类型延迟赋值适合运行时才能确定的值。

<!-- @[property_initialization_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
class User {
  // 声明时初始化
  public id: number = 0;
  public name: string = '';
  public active: boolean = true;
  
  // 构造函数中初始化
  constructor(id?: number, name?: string) {
    if (id !== undefined) {
      this.id = id;
    }
    if (name !== undefined) {
      this.name = name;
    }
  }
  
  // 延迟初始化
  public email: string | null = null;
  
  setEmail(email: string): void {
    this.email = email;  // 延迟赋值
  }
}

let user1: User = new User();
console.info(`${user1.id}`);    // 0
console.info(`${user1.name}`);  // ''

let user2: User = new User(1, 'Alice');
console.info(`${user2.id}`);    // 1
console.info(`${user2.name}`);  // 'Alice'

// 延迟初始化
user2.setEmail('alice@example.com');
console.info(`${user2.email}`);  // 'alice@example.com'
```

## 类的方法

方法是类中定义的函数，描述对象的行为，通过`this`访问实例状态。方法分为实例方法和静态方法，并支持方法重载；方法的可选参数、默认参数、剩余参数等参数特性与函数一致，详见[函数](arkts-language-guide-functions.md)。

### 实例方法

实例方法通过类的实例对象（`实例.方法名()`）调用，方法体内`this`指向当前实例，可访问实例属性和其他实例方法。

<!-- @[instance_method_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class Student {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // 实例方法声明
  study(): void {
    console.info(`${this.name} is studying`);
  }
  
  // 带参数的实例方法
  studyFor(subject: string): void {
    console.info(`${this.name} is studying ${subject}`);
  }
  
  // 带返回值的实例方法
  getInfo(): string {
    return `${this.name}, ${this.age} years old`;
  }
  
  // 带默认参数的方法
  greet(greeting: string = 'Hello'): string {
    return `${greeting}, I'm ${this.name}`;
  }
}

let student: Student = new Student('Alice', 20);

// 调用实例方法
student.study();               // 'Alice is studying'
student.studyFor('Math');       // 'Alice is studying Math'
console.info(`${student.getInfo()}`); // 'Alice, 20 years old'
console.info(`${student.greet()}`);   // 'Hello, I'm Alice'
console.info(`${student.greet('Hi')}`); // 'Hi, I'm Alice'
```

实例方法返回`this`可实现链式调用，常用于Builder模式。

<!-- @[instance_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Calculator {
  public value: number = 0;
  
  // 实例方法
  add(n: number): void {
    this.value += n;
  }
  
  subtract(n: number): void {
    this.value -= n;
  }
  
  multiply(n: number): void {
    this.value *= n;
  }
  
  divide(n: number): void {
    if (n !== 0) {
      this.value /= n;
    }
  }
  
  getValue(): number {
    return this.value;
  }
  
  reset(): void {
    this.value = 0;
  }
}

let calc: Calculator = new Calculator();
calc.add(10);
calc.multiply(2);
console.info(`${calc.getValue().toString()}`);  // 20

// 方法链式调用（需返回this）
class Builder {
  private data: string = '';
  
  add(text: string): Builder {
    this.data += text;
    return this;
  }
  
  addLine(text: string): Builder {
    this.data += text + '\n';
    return this;
  }
  
  build(): string {
    return this.data;
  }
}

let result: string = new Builder()
  .add('Hello')
  .add(' ')
  .add('World')
  .build();
console.info(`${result}`);  // 'Hello World'
```

### 静态方法

静态方法使用`static`关键字声明，属于类本身而非实例，通过类名调用，无需实例化；静态方法无法访问实例属性和实例`this`，只能访问静态成员。

<!-- @[ts_static_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class MathUtils {
  // 静态方法
  static add(a: number, b: number): number {
    return a + b;
  }
  
  static multiply(a: number, b: number): number {
    return a * b;
  }
  
  static max(a: number, b: number): number {
    return a > b ? a : b;
  }
  
  static min(a: number, b: number): number {
    return a < b ? a : b;
  }
}

// 静态方法通过类名调用
console.info(`${MathUtils.add(1, 2)}`);      // 3
console.info(`${MathUtils.multiply(3, 4)}`); // 12
console.info(`${MathUtils.max(5, 10)}`);     // 10

// 创建实例不影响静态方法
let utils: MathUtils = new MathUtils();
utils.add(1, 2);  // 编译错误：实例不能调用静态方法

// 静态方法无法访问实例属性
class StaticExample {
  public instanceValue: number = 10;
  public static staticValue: number = 20;
  
  static getStaticValue(): number {
    return StaticExample.staticValue;  // 可访问静态属性
  }
  
  static getInstanceValue(): number {
    return this.instanceValue;  // 编译错误：无法访问实例属性
  }
}
```

静态方法常用于工厂方法、单例模式和工具函数。

<!-- @[static_factory_singleton_utility](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
// 1. 工厂方法
class User {
  private id: number;
  private name: string;

  private constructor(id: number, name: string) {
    this.id = id;
    this.name = name;
  }
  
  // 静态工厂方法
  static create(id: number, name: string): User {
    return new User(id, name);
  }
  
  static createGuest(): User {
    return new User(0, 'Guest');
  }
  
  static createAdmin(id: number): User {
    return new User(id, 'Admin');
  }
  
  getInfo(): string {
    return `User ${this.id}: ${this.name}`;
  }
}

let admin: User = User.createAdmin(1);
let guest: User = User.createGuest();
console.info(`${admin.getInfo()}`);   // 'User 1: Admin'
console.info(`${guest.getInfo()}`);   // 'User 0: Guest'

// 2. 单例模式
class Singleton {
  private static instance: Singleton | undefined = undefined;
  
  private constructor() {}
  
  static getInstance(): Singleton {
    if (Singleton.instance === undefined) {
      Singleton.instance = new Singleton();
    }
    return Singleton.instance;
  }
  
  doSomething(): void {
    console.info('Singleton working');
  }
}

let s1: Singleton = Singleton.getInstance();
let s2: Singleton = Singleton.getInstance();
console.info(`${(s1 === s2).toString()}`);  // true，同一实例

// 3. 工具方法
class ArrayUtils {
  static isEmpty<T>(arr: T[]): boolean {
    return arr.length === 0;
  }
  
  static first<T>(arr: T[]): T | undefined {
    return arr[0];
  }
  
  static last<T>(arr: T[]): T | undefined {
    return arr[arr.length - 1];
  }
  
  static flatten<T>(arr: T[][]): T[] {
    let result: T[] = [];
    for (let sub of arr) {
      for (let item of sub) {
        result.push(item);
      }
    }
    return result;
  }
}
```

### 方法重载

方法重载为同一方法名提供多个类型签名，根据传入参数类型分发对应实现。ArkTS的重载采用多个重载签名加一个实现签名的形式：重载签名仅在编译期生效用于类型检查，实现签名对外不可见，调用方只能使用已声明的重载签名；实现签名须兼容所有重载签名，在函数体内通过`typeof`等运行时检查区分不同参数类型的逻辑。声明时更具体的类型签名应先声明。

<!-- @[method_overloading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class DataProcessor {
  // 方法重载签名
  process(data: string): string;
  process(data: number): number;
  process(data: string | number): string | number {
    if (typeof data === 'string') {
      return data.toUpperCase();
    }
    return data * 2;
  }
  
  // 多参数重载
  format(value: number): string;
  format(value: number, precision: number): string;
  format(value: number, precision?: number): string {
    if (precision !== undefined) {
      return value.toFixed(precision);
    }
    return value.toString();
  }
}

let processor: DataProcessor = new DataProcessor();

console.info(`${processor.process('hello')}`);  // 'HELLO'
console.info(`${processor.process(5)}`);        // 10

console.info(`${processor.format(3.14159)}`);       // '3.14159'
console.info(`${processor.format(3.14159, 2)}`);    // '3.14'
```

重载签名数量过多时应控制签名数量，改用可选参数、联合类型或为不同场景提供不同方法名。

<!-- @[overload_alternatives](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class SafeConverter {
  // 使用静态方法替代重载（更清晰）
  static toNumberFromString(value: string): number | null {
    let result: number = Number.parseInt(value, 10);
    return Number.isNaN(result) ? null : result;
  }
  
  static toNumberFromNumber(value: number): number {
    return value;
  }
  
  // 或使用联合类型和类型守卫
  convert(value: string | number): number | null {
    if (typeof value === 'string') {
      let result: number = Number.parseInt(value, 10);
      return Number.isNaN(result) ? null : result;
    }
    return value;
  }
  
  // 为不同场景提供不同方法名
  fromString(str: string): number | null {
    let result: number = Number.parseInt(str, 10);
    return Number.isNaN(result) ? null : result;
  }
  
  fromNumber(num: number): number {
    return num;
  }
}

let converter: SafeConverter = new SafeConverter();

console.info(`${SafeConverter.toNumberFromString('123')}`);  // 123
console.info(`${SafeConverter.toNumberFromNumber(456)}`);    // 456

console.info(`${converter.convert('42')}`);        // 42
console.info(`${converter.convert(100)}`);         // 100

console.info(`${converter.fromString('abc')}`);    // null
console.info(`${converter.fromNumber(200)}`);      // 200
```

### `this`关键字的使用

关键字`this`只能在类的实例（非静态）方法中使用，指向调用实例方法的对象或正在构造的对象。

将类方法赋值给变量后调用，`this`会丢失绑定，直接调用会产生运行时错误。

**TypeScript对照**

<!-- @[ts_runtime_this_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript对照写法，演示this丢失的运行时错误
class TsThisExample {
  public name: string = 'MyClass';

  getName(): string {
    return this.name;
  }
}

let tsThisEx: TsThisExample = new TsThisExample();
console.info(`${tsThisEx.getName()}`);  // 'MyClass'

let tsThisG = tsThisEx.getName;
tsThisG();  // 运行时错误：Cannot read property 'name' of undefined
```

使用箭头函数属性可绑定`this`，在创建时固定`this`指向；注意箭头函数属性每个实例都有一份函数副本，无法通过`super`调用基类方法。

<!-- @[arrow_function_this](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ArrowThisHandler {
  private name: string = 'handler';

  public handle = (): void => {
    console.info(`${this.name}`);
  };
}

let arrowHandler: ArrowThisHandler = new ArrowThisHandler();
let arrowH = arrowHandler.handle;
arrowH();  // handler（this正确绑定）
```

**`this`参数**：方法可声明`this`参数，在编译期强制调用方使用正确的上下文类型；`this`参数在编译后被擦除，不影响运行时。注意：`this`作为参数名标注是ArkTS支持的，但`this`作为类型（如返回类型`: this`或参数类型`other: this`）不支持。

<!-- @[this_parameter_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class TpThisCounter {
  public count: number = 0;
  increment(this: TpThisCounter): void {
    this.count++;
  }
}

let tpThisCounter: TpThisCounter = new TpThisCounter();
tpThisCounter.increment();
console.info(`${tpThisCounter.count}`); // 1
```

ArkTS对`this`有以下使用限制：

- 不支持`this`类型。
- 不支持在函数和类的静态方法中使用`this`。

**TypeScript对照**

<!-- @[ts_this_usage_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class TsThisLimitA {
  public n: number = 0;
  f1(arg1: this) {} // 编译错误：不支持this类型（arkts-no-typing-with-this）
  static f2(arg1: number): void {
    this.n = arg1;  // 编译错误：不支持在静态方法中使用this
  }
}

function foo(arg1: number) {
  this.n = arg1;    // 编译错误：不支持在函数中使用this
}
```

TypeScript中`this`作为返回类型（如`append(text: string): this`）可用于链式调用。ArkTS不支持`this`作为类型标注，使用显式类名作为返回类型实现同样的链式调用效果。

<!-- @[string_builder_explicit_return](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class StringBuilder {
  public parts: string[] = [];

  append(text: string): StringBuilder {
    this.parts.push(text);
    return this;
  }

  toString(): string {
    return this.parts.join('');
  }
}

let sb: StringBuilder = new StringBuilder();
let sbResult: string = sb.append('Hello').append(', ').append('World').toString();
console.info(`${sbResult}`); // 'Hello, World'
```

> **说明：**
>
> `this`作为参数类型（如`sameAs(other: this)`）同样不支持，使用显式类名作为参数类型替代。

## 类的访问控制

访问修饰符控制类成员的可访问性，保护内部数据：`public`、`private`、`protected`控制可见性，`readonly`控制可写性，二者可正交组合覆盖常见封装需求（如`public readonly`表示外部只读、`private readonly`表示内部只读）。

### 访问控制修饰符

`public`、`private`、`protected`控制属性在类外和子类中的可见性：`public`任何地方可访问，`private`仅类内部可访问，`protected`类及子类可访问。

<!-- @[ts_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class BankAccount {
  // public：公开访问
  public accountNumber: string;
  
  // private：私有，仅类内部访问
  private balance: number;
  
  // protected：受保护，类及子类访问
  protected ownerName: string;
  
  constructor(accountNumber: string, ownerName: string) {
    this.accountNumber = accountNumber;
    this.ownerName = ownerName;
    this.balance = 0;
  }
  
  // 公开方法访问私有属性
  deposit(amount: number): void {
    if (amount > 0) {
      this.balance += amount;
    }
  }
  
  getBalance(): number {
    return this.balance;
  }
  
  // protected方法
  protected updateOwner(name: string): void {
    this.ownerName = name;
  }
}

let account: BankAccount = new BankAccount('123', 'Alice');

// public可访问
console.info(`${account.accountNumber}`);

// private不可访问
console.info(`${account.balance}`);  // 编译错误

// protected不可访问
console.info(`${account.ownerName}`);  // 编译错误

// 通过方法访问
account.deposit(100);
console.info(`${account.getBalance()}`);  // 100
```

方法同样支持访问控制修饰符：`public`方法构成类的对外接口，`private`/`protected`方法仅供内部或子类使用。

<!-- @[ts_method_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class Service {
  // public：公开方法
  public start(): void {
    console.info(`Service started`);
    this.initialize();
  }

  // private：私有方法，仅类内部
  private initialize(): void {
    console.info(`Initializing...`);
    this.loadConfig();
  }

  // protected：受保护方法，子类可访问
  protected loadConfig(): void {
    console.info(`Loading configuration`);
  }

  // 公开方法调用私有方法
  public stop(): void {
    this.cleanup();
    console.info(`Service stopped`);
  }

  private cleanup(): void {
    console.info(`Cleaning up resources`);
  }
}

let service: Service = new Service();

// public方法可调用
service.start();  // Service started, Initializing..., Loading config
service.stop();   // Cleaning up..., Service stopped

// private方法不可访问
service.initialize();  // 编译错误

// protected方法不可访问
service.loadConfig();  // 编译错误

// 子类访问protected方法
class CustomService extends Service {
  configure(): void {
    this.loadConfig();  // 可访问protected
  }
}
```

各修饰符可单独或组合使用，分别控制类内、子类和类外的可见性与可写性。

<!-- @[ts_access_modifiers_summary](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class Example {
  // public：公开，任何地方可访问
  public publicProperty: string = 'public';
  
  // private：私有，仅类内部可访问
  private privateProperty: string = 'private';
  
  // protected：受保护，类及子类可访问
  protected protectedProperty: string = 'protected';
  
  // readonly：只读，初始化后不可修改
  readonly readonlyProperty: string = 'readonly';
  
  // 组合使用
  private readonly privateReadonly: string = 'private readonly';
  protected readonly protectedReadonly: string = 'protected readonly';
  
  public publicMethod(): void {
    // 可访问所有属性
    console.info(`${this.publicProperty}`);
    console.info(`${this.privateProperty}`);
    console.info(`${this.protectedProperty}`);
  }
  
  private privateMethod(): void {
    console.info(`Private method`);
  }
  
  protected protectedMethod(): void {
    console.info(`Protected method`);
  }
}

let example: Example = new Example();

// public可访问
console.info(`${example.publicProperty}`);
example.publicMethod();

// private不可访问
console.info(`${example.privateProperty}`);  // 编译错误
example.privateMethod();                // 编译错误

// protected不可访问
console.info(`${example.protectedProperty}`);  // 编译错误
example.protectedMethod();                // 编译错误

// readonly可读不可写
console.info(`${example.readonlyProperty}`);
example.readonlyProperty = 'new';  // 编译错误
```

修饰符的作用域：`public`在类内、子类和类外均可见；`private`仅在类内可见；`protected`在类内及子类可见，类外不可见。

<!-- @[ts_access_modifiers_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
class Base {
  public publicValue: number = 1;
  private privateValue: number = 2;
  protected protectedValue: number = 3;
  
  testAccess(): void {
    // 类内部可访问所有
    console.info(`${this.publicValue}`);
    console.info(`${this.privateValue}`);
    console.info(`${this.protectedValue}`);
  }
}

class Derived extends Base {
  testDerivedAccess(): void {
    // 子类可访问public和protected
    console.info(`${this.publicValue}`);
    console.info(`${this.privateValue}`);  // 编译错误
    console.info(`${this.protectedValue}`);
  }
}

// 外部访问
let base: Base = new Base();
console.info(`${base.publicValue}`);  // 1（public可访问）
console.info(`${base.privateValue}`);   // 编译错误
console.info(`${base.protectedValue}`); // 编译错误

let derived: Derived = new Derived();
console.info(`${derived.publicValue}`);  // 1（public可访问）
```

**ES私有字段（#field）**：TypeScript支持`#`前缀的私有字段，提供运行时也私有的成员；与`private`关键字不同，`#field`在编译后仍保持私有。ArkTS中使用`private`修饰符替代，详见[从TypeScript到ArkTS的适配规则](typescript-to-arkts-migration-guide.md#不支持以开头的私有字段)。

**TypeScript对照**

<!-- @[ts_private_fields](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript对照写法，ArkTS中使用private修饰符替代
class TsDog {
  #barkAmount: number = 0;
  public personality: string = 'happy';

  bark(): void {
    this.#barkAmount++;
  }
}
```

ArkTS中使用`private`修饰符。

<!-- @[private_field_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class PrivateFieldDog {
  private barkAmount: number = 0;
  public personality: string = 'happy';

  bark(): void {
    this.barkAmount++;
  }

  getBarkCount(): number {
    return this.barkAmount;
  }
}

let pfDog: PrivateFieldDog = new PrivateFieldDog();
pfDog.bark();
pfDog.bark();
console.info(`${pfDog.getBarkCount().toString()}`);  // 2
```

`private`为编译期检查（软私有），`#field`为运行时也私有（硬私有），ArkTS统一使用`private`修饰符。

## 类的初始化

初始化在对象创建时为属性设置有效初值，确保对象创建后处于可用状态。ArkTS通过构造函数、属性默认值、对象字面量等机制完成初始化，并由编译器强制检查初始化完整性。

### 构造函数

构造函数通过`constructor`关键字声明，在`new`创建实例时自动调用（分配内存、调用构造函数初始化属性、返回实例引用）。构造函数的职责包括初始化所有属性、验证参数有效性、准备必要资源并设置初始状态。

<!-- @[constructor_responsibilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class DatabaseConnection {
  private connection: string;
  private connected: boolean;
  private timeout: number;
  
  // 构造函数职责
  constructor(connectionString: string, timeout: number = 5000) {
    // 1. 属性初始化
    this.connection = connectionString;
    this.timeout = timeout;
    this.connected = false;
    
    // 2. 参数验证
    if (connectionString.length === 0) {
      throw new Error('Connection string cannot be empty');
    }
    
    // 3. 资源准备
    this.prepareConnection();
  }
  
  private prepareConnection(): void {
    console.info('Preparing connection resources');
  }
  
  connect(): void {
    this.connected = true;
    console.info(`Connected to ${this.connection}`);
  }
  
  disconnect(): void {
    this.connected = false;
    console.info('Disconnected');
  }
}

let db: DatabaseConnection = new DatabaseConnection('localhost:5432', 3000);
db.connect();
```

未定义构造函数时，编译器自动生成无参数的默认构造函数，将属性初始化为默认值。

<!-- @[default_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class SimpleClass {
  public value: number = 10;
  public name: string = 'default';
  
  // 无构造函数：编译器自动生成默认构造函数
  // constructor() {}  // 自动生成
}

let simple: SimpleClass = new SimpleClass();
console.info(`${simple.value.toString()}`);  // 10
console.info(`${simple.name}`);   // 'default'

class DefaultConstructor {
  public x: number = 0;
  public y: number = 0;
  
  // 显式无参构造函数
  constructor() {
    console.info('Default constructor called');
  }
  
  getValues(): string {
    return `${this.x}, ${this.y}`;
  }
}

let defaultObj: DefaultConstructor = new DefaultConstructor();
console.info(`${defaultObj.getValues()}`);  // '0, 0'

// 默认构造函数：
// 无参数
// 自动初始化属性为默认值
// 编译器自动生成（如果未定义）
```

构造函数支持重载：通过声明多个参数列表不同的构造函数签名，使对象可以按不同的参数组合初始化，编译器根据传入参数自动匹配对应签名；实现签名须兼容所有重载签名。实际开发中也常通过可选参数或静态工厂方法提供多种创建方式。

<!-- @[constructor_overloading](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class OverloadPoint {
  public x: number;
  public y: number;
  
  // 构造函数重载签名
  constructor();
  constructor(x: number);
  constructor(x: number, y: number);
  constructor(x?: number, y?: number) {
    this.x = x ?? 0;
    this.y = y ?? 0;
  }
}

let point1: OverloadPoint = new OverloadPoint();
let point2: OverloadPoint = new OverloadPoint(10);
let point3: OverloadPoint = new OverloadPoint(10, 20);

console.info(`${point1.x} ${point1.y}`);  // 0 0
console.info(`${point2.x} ${point2.y}`);  // 10 0
console.info(`${point3.x} ${point3.y}`);  // 10 20

class Color {
  public red: number;
  public green: number;
  public blue: number;
  
  constructor(hex: string);
  constructor(r: number, g: number, b: number);
  constructor(rOrHex: number | string, g?: number, b?: number) {
    if (typeof rOrHex === 'string') {
      // 从十六进制解析
      this.red = Number.parseInt(rOrHex.substring(1, 3), 16);
      this.green = Number.parseInt(rOrHex.substring(3, 5), 16);
      this.blue = Number.parseInt(rOrHex.substring(5, 7), 16);
    } else {
      this.red = rOrHex;
      this.green = g ?? 0;
      this.blue = b ?? 0;
    }
  }
}

let color1: Color = new Color('#FF0000');
let color2: Color = new Color(255, 128, 0);
```

**参数属性**：TypeScript支持在构造函数参数前添加访问修饰符（`public`、`private`、`protected`、`readonly`），编译器自动声明并赋值对应属性。**ArkTS不支持参数属性语法**，需显式声明属性并在构造函数中赋值。

**TypeScript对照**

<!-- @[ts_parameter_properties](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript写法，ArkTS不支持构造函数参数属性
class TsPoint {
  constructor(public x: number, public y: number) {}
}

let tsPt: TsPoint = new TsPoint(3, 4);
console.info(`${tsPt.x}, ${tsPt.y}`); // 3, 4
```

ArkTS替代方式：显式声明属性并在构造函数中赋值。

<!-- @[explicit_property_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ExplicitPoint {
  public x: number;
  public y: number;

  constructor(x: number, y: number) {
    this.x = x;
    this.y = y;
  }
}

let epPoint: ExplicitPoint = new ExplicitPoint(3, 4);
console.info(`${epPoint.x}, ${epPoint.y}`); // 3, 4
```

**静态工厂方法**通过命名方法表达不同的构造意图，可简化参数、提供默认值并针对特定场景快速创建对象。ArkTS不支持`this()`调用（在构造函数中调用同类的另一个构造函数），同样使用静态工厂方法替代。

<!-- @[static_factory_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class ColorValue {
  public red: number;
  public green: number;
  public blue: number;

  constructor(red: number, green: number, blue: number) {
    this.red = red;
    this.green = green;
    this.blue = blue;
  }

  static fromRGB(r: number, g: number, b: number): ColorValue {
    return new ColorValue(r, g, b);
  }

  static fromHex(hex: string): ColorValue {
    let r: number = Number.parseInt(hex.substring(1, 3), 16);
    let g: number = Number.parseInt(hex.substring(3, 5), 16);
    let b: number = Number.parseInt(hex.substring(5, 7), 16);
    return new ColorValue(r, g, b);
  }

  static fromName(name: string): ColorValue {
    switch (name) {
      case 'red':
        return new ColorValue(255, 0, 0);
      case 'green':
        return new ColorValue(0, 255, 0);
      case 'blue':
        return new ColorValue(0, 0, 255);
      default:
        return new ColorValue(0, 0, 0);
    }
  }
}

let cvColor1: ColorValue = ColorValue.fromRGB(255, 128, 0);
let cvColor2: ColorValue = ColorValue.fromHex('#FF8000');
let cvColor3: ColorValue = ColorValue.fromName('red');
```

构造函数同样受访问控制修饰符约束：声明为`private`时，外部无法直接实例化，常与静态工厂方法配合实现单例等模式；声明为`protected`时，仅类内部和子类可以实例化（子类构造函数中通过`super()`调用），常用于要求必须通过子类使用的基类。

<!-- @[private_constructor_with_factory](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class FactoryConfiguration {
  public apiUrl: string;
  public timeout: number;
  public debug: boolean;
  
  private constructor(apiUrl: string, timeout: number, debug: boolean) {
    this.apiUrl = apiUrl;
    this.timeout = timeout;
    this.debug = debug;
  }
  
  // 静态工厂方法替代构造函数重载
  static createDefault(): FactoryConfiguration {
    return new FactoryConfiguration('EXAMPLE_API_URL', 5000, false);
  }
  
  static createWithUrl(apiUrl: string): FactoryConfiguration {
    // 调用默认配置，修改部分参数
    let factoryDefaultConfig: FactoryConfiguration = FactoryConfiguration.createDefault();
    return new FactoryConfiguration(apiUrl, factoryDefaultConfig.timeout, factoryDefaultConfig.debug);
  }
  
  static createDebug(): FactoryConfiguration {
    return new FactoryConfiguration('EXAMPLE_API_URL', 5000, true);
  }
  
  static copy(config: FactoryConfiguration): FactoryConfiguration {
    return new FactoryConfiguration(config.apiUrl, config.timeout, config.debug);
  }
}

let factoryDefaultConfig: FactoryConfiguration = FactoryConfiguration.createDefault();
let factoryUrlConfig: FactoryConfiguration = FactoryConfiguration.createWithUrl('EXAMPLE_API_URL');
let debugConfig: FactoryConfiguration = FactoryConfiguration.createDebug();
let copiedConfig: FactoryConfiguration = FactoryConfiguration.copy(factoryDefaultConfig);
```

**初始化顺序**：当基类和派生类都有字段初始化时，执行顺序为：基类字段初始化→基类构造函数→派生类字段初始化→派生类构造函数；基类构造函数中看到的派生类字段还是基类自己的值，因为派生类字段初始化在基类构造函数之后才执行。此外，静态初始化块（`static { }`）在类首次被加载时执行，先于所有实例字段初始化和构造函数调用；静态字段的初始化按声明顺序执行，静态初始化块穿插在静态字段之间按顺序执行。

<!-- @[init_order](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class IoBase {
  public static baseStatic: number = 10;
  public name: string = 'base';

  static {
    console.info('Base static block');
  }

  constructor() {
    console.info(`Base constructor: name = ${this.name}`);
  }
}

class IoDerived extends IoBase {
  public static derivedStatic: number = 20;
  public name: string = 'derived';

  static {
    console.info('Derived static block');
  }

  constructor() {
    super();
    console.info(`Derived constructor: name = ${this.name}`);
  }
}

let ioD: IoDerived = new IoDerived();
// 输出：
// Base static block（类加载时执行静态初始化块，先于实例创建）
// Derived static block
// Base constructor: name = base（派生类字段尚未初始化）
// Derived constructor: name = derived
```

子类构造函数必须通过`super()`调用父类构造函数，确保父类属性先初始化，详细规则见[super关键字的使用](#super关键字的使用)。

### 对象字面量

对象字面量适合一次性、简单的数据组织。ArkTS要求对象字面量显式标注类型（类或接口），编译器按该类型检查属性：必须包含所有必选成员且类型匹配，多余属性会被拒绝；类中包含`private`属性时，无法通过对象字面量初始化该类，应使用构造函数。

类型选择建议：类适合封装数据连同其操作行为、且需要复用与继承的场景；接口适合仅描述数据结构形状；对象字面量适合一次性、简单的数据组织。

<!-- @[class_vs_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
// 使用类：需要封装数据和行为的场景
class Order {
  public id: number;
  public items: string[];
  public total: number;
  
  constructor(id: number) {
    this.id = id;
    this.items = [];
    this.total = 0;
  }
  
  addItem(item: string, price: number): void {
    this.items.push(item);
    this.total += price;
  }
  
  removeItem(item: string, price: number): void {
    let index: number = this.items.indexOf(item);
    if (index >= 0) {
      this.items.splice(index, 1);
      this.total -= price;
    }
  }
  
  getTotal(): number {
    return this.total;
  }
}

// 使用接口：只需数据结构的场景
interface Product {
  id: number;
  name: string;
  price: number;
}

let product: Product = { id: 1, name: 'Item', price: 100 };

// 类vs对象字面量
// 类：可复用、有方法、可继承
// 对象字面量：简单数据、一次性使用
```

对象字面量的详细用法见[接口](arkts-language-guide-interfaces.md)和[需要显式标注对象字面量的类型](typescript-to-arkts-migration-guide.md#需要显式标注对象字面量的类型)。

### 未初始化检查

ArkTS编译器强制执行属性初始化检查（等效于TypeScript的`strictPropertyInitialization`选项，但ArkTS中不可关闭）：所有非可选属性必须在声明时或构造函数中被赋值，否则编译报错；可选属性（`?`）不要求初始化。

**TypeScript对照**

<!-- @[ts_required_properties_initialization](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Initialization.ts) -->

``` TypeScript
class StrictInitialization {
  // 必需属性：必须初始化
  public name: string;  // 编译错误：未初始化
  public age: number;   // 编译错误：未初始化
  
  constructor() {
    // 未初始化name和age
    // TypeScript会报编译错误（TS2564）
  }
  
  // 正确做法：初始化所有属性
  correctConstructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

class ProperInitialization {
  // 声明时初始化
  public name: string = '';
  public age: number = 0;
  
  constructor() {
    // 属性已初始化
  }
}

class OptionalInitialization {
  // 可选属性：可不初始化
  public name?: string;
  public age?: number;
  
  constructor() {
    // 可选属性允许未初始化
  }
  
  initialize(name: string, age: number): void {
    this.name = name;
    this.age = age;
  }
}
```

通过确保属性有值、使用空值合并（`??`）和可选链（`?.`）等安全访问方式，避免`undefined`异常。

<!-- @[safe_initialization_techniques](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class SafeInitialization {
  public name: string;
  public age: number;
  public email?: string;
  
  constructor(name: string, age: number) {
    // 确保必需属性初始化
    this.name = name ?? 'default';
    this.age = age ?? 0;
    
    // 可选属性谨慎处理
    if (this.email === undefined) {
      console.info('Email not initialized');
    }
  }
  
  // 安全访问技巧
  getEmail(): string {
    return this.email ?? '';
  }
  
  hasEmail(): boolean {
    return this.email !== undefined && this.email.length > 0;
  }
  
  safeProcess(): void {
    // 检查后访问
    if (this.name !== undefined) {
      console.info(`${this.name}`);
    }
    
    // 使用空值合并
    let safeAge: number = this.age ?? 0;
    
    // 使用可选链（对象属性）
    let emailLength: number | undefined = this.email?.length;
  }
}
```

## 类的继承

通过`extends`关键字，子类继承父类的属性与方法，在构造函数中调用`super()`复用父类初始化逻辑，并可覆盖或新增方法以扩展父类行为。基类（父类）提供通用成员供复用，派生类（子类）在继承的基础上特化扩展。ArkTS只支持单继承，一个子类只能`extends`一个父类。

继承让子类复用父类成员以减少重复代码、随父类修改自动同步提升可维护性，并通过方法覆盖实现多态、建立清晰的类型层次。

<!-- @[basic_inheritance_example](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// 父类（基类）
class Animal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  speak(): void {
    console.info(`${this.name} makes a sound`);
  }
  
  move(): void {
    console.info(`${this.name} moves`);
  }
}

// 子类（派生类）继承父类
class Dog extends Animal {
  public breed: string;
  
  constructor(name: string, breed: string) {
    super(name);  // 调用父类构造函数
    this.breed = breed;
  }
  
  // 继承父类方法，可以覆盖
  speak(): void {
    console.info(`${this.name} barks`);
  }
  
  // 新增方法
  fetch(): void {
    console.info(`${this.name} fetches the ball`);
  }
}

let dog: Dog = new Dog('Max', 'Labrador');
dog.speak();   // 'Max barks'（覆盖方法）
dog.move();    // 'Max moves'（继承方法）
dog.fetch();   // 'Max fetches the ball'（新增方法）
```

通过继承复用父类的属性和方法，可以避免在多个子类中重复编写相同逻辑。

<!-- @[inheritance_code_reuse](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// 不使用继承：重复代码
class DogWithoutInheritance {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  eat(): void {
    console.info(`${this.name} is eating`);
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
  
  bark(): void {
    console.info(`${this.name} is barking`);
  }
}

class CatWithoutInheritance {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  eat(): void {
    console.info(`${this.name} is eating`);  // 重复代码
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);  // 重复代码
  }
  
  meow(): void {
    console.info(`${this.name} is meowing`);
  }
}

// 使用继承：代码复用
class ReuseAnimal {
  public name: string;
  public age: number;
  
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
  
  // 公共方法：子类复用
  eat(): void {
    console.info(`${this.name} is eating`);
  }
  
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
}

class ReuseDog extends ReuseAnimal {
  constructor(name: string, age: number) {
    super(name, age);
  }
  
  // 特有方法
  bark(): void {
    console.info(`${this.name} is barking`);
  }
}

class Cat extends ReuseAnimal {
  constructor(name: string, age: number) {
    super(name, age);
  }
  
  // 特有方法
  meow(): void {
    console.info(`${this.name} is meowing`);
  }
}

let reuseDog: ReuseDog = new ReuseDog('Max', 3);
let cat: Cat = new Cat('Whiskers', 2);

reuseDog.eat();    // 复用父类方法
reuseDog.sleep();  // 复用父类方法
reuseDog.bark();   // 子类特有方法

cat.eat();    // 复用父类方法
cat.sleep();  // 复用父类方法
cat.meow();   // 子类特有方法
```

空子类是不添加新成员的子类，常用于类型标记（通过`instanceof`做运行时区分）和为未来扩展预留继承位置；空子类无需显式声明构造函数，创建实例时隐式调用父类构造函数。

<!-- @[empty_child_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class Base {
  public value: number = 10;
  
  getValue(): number {
    return this.value;
  }
  
  increment(): void {
    this.value++;
  }
}

// 空子类：无新增属性和方法
class EmptyChild extends Base {
  // 空子类继承所有父类功能
}

let empty: EmptyChild = new EmptyChild();

// 空子类完全继承父类
console.info(`${empty.getValue()}`);  // 10
empty.increment();
console.info(`${empty.getValue()}`);  // 11

// 空子类使用场景：
// 1. 类型标记：区分不同类别
class User {
  public name: string;
  constructor(name: string) {
    this.name = name;
  }
}

class RegularUser extends User {}
class PremiumUser extends User {}

let regular: RegularUser = new RegularUser('Bob');
let premium: PremiumUser = new PremiumUser('Alice');

// 通过类型区分用户类别
function getServiceLevel(user: User): string {
  if (user instanceof PremiumUser) {
    return 'Premium service';
  }
  return 'Regular service';
}

console.info(`${getServiceLevel(regular)}`);   // 'Regular service'
console.info(`${getServiceLevel(premium)}`);   // 'Premium service'

// 2. 未来扩展预留
class FutureFeature extends Base {
  // 预留子类，未来可添加功能
}
```

**成员继承规则**：子类自动继承父类的`public`和`protected`成员；`private`成员不可继承，子类无法直接访问，只能通过父类提供的`public`方法间接调用。

<!-- @[ts_access_modifier_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class Parent {
  // 实例属性
  public publicValue: string = 'public';
  protected protectedValue: string = 'protected';

  // 实例方法
  public publicMethod(): void {
    console.info(`Public method`);
  }

  protected protectedMethod(): void {
    console.info(`Protected method`);
  }

  private privateMethod(): void {
    console.info(`Private method`);
  }

  // 访问私有方法的公开方法
  callPrivate(): void {
    this.privateMethod();
  }
}

class AccessChildTest extends Parent {
  // 继承public属性和方法
  testPublic(): void {
    console.info(`${this.publicValue}`);    // 可访问
    this.publicMethod();               // 可访问
  }

  // 继承protected属性和方法
  testProtected(): void {
    console.info(`${this.protectedValue}`); // 可访问
    this.protectedMethod();            // 可访问
  }

  // 无法继承private属性和方法
  testPrivate(): void {
    // this.privateMethod();  // 编译错误
    this.callPrivate();       // 通过公开方法访问
  }
}

let accessChild: AccessChildTest = new AccessChildTest();

accessChild.testPublic();     // 'public', 'Public method'
accessChild.testProtected();  // 'protected', 'Protected method'
accessChild.testPrivate();    // 'Private method'
```

静态属性和静态方法同样会被子类继承，通过子类类名即可访问。

<!-- @[static_member_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class MemberBase {
  // 静态属性
  public static staticValue: number = 100;
  
  // 静态方法
  public static staticMethod(): void {
    console.info('Static method');
  }
  
  public static getStaticValue(): number {
    return MemberBase.staticValue;
  }
}

class Derived extends MemberBase {
  // 继承静态方法
  callStaticMethod(): void {
    MemberBase.staticMethod();    // 通过父类名调用
    Derived.staticMethod(); // 通过子类名调用（继承）
  }
  
  // 继承静态属性
  getInheritedStaticValue(): number {
    return Derived.getStaticValue();  // 继承的静态方法
  }
  
  // 子类静态方法
  static childStaticMethod(): void {
    console.info('Child static method');
    Derived.staticMethod();  // 调用继承的静态方法
  }
}

// 静态方法通过类名调用
MemberBase.staticMethod();           // 'Static method'
Derived.staticMethod();        // 'Static method'（继承）
Derived.childStaticMethod();   // 'Child static method', 'Static method'

console.info(`${MemberBase.staticValue}`);       // 100
console.info(`${Derived.staticValue}`);    // 100（继承）

let derived: Derived = new Derived();
derived.callStaticMethod();           // 'Static method', 'Static method'
console.info(`${derived.getInheritedStaticValue()}`);  // 100

// 静态成员继承规则：
// 静态属性和方法通过类名访问
// 子类继承父类的静态成员
// 子类可以添加自己的静态成员
```

属性继承同理：子类继承父类的`public`和`protected`属性，可声明同名属性覆盖（隐藏）父类属性，但无法改变父类成员的访问级别。

<!-- @[ts_property_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Properties.ts) -->

``` TypeScript
class Parent {
  public publicProp: string = 'public';
  protected protectedProp: string = 'protected';
  private privateProp: string = 'private';

  getPrivateProp(): string {
    return this.privateProp;
  }
}

class Child extends Parent {
  // 新增属性
  public childProp: string = 'child';

  // 继承public属性
  getPublicFromParent(): string {
    return this.publicProp;  // 可访问
  }

  // 继承protected属性
  getProtectedFromParent(): string {
    return this.protectedProp;  // 可访问
  }

  // 无法继承private属性
  getPrivateFromParent(): string {
    return this.privateProp;  // 编译错误
  }

  // 通过父类公开方法访问私有属性
  getParentPrivate(): string {
    return this.getPrivateProp();  // 可访问
  }

  // 覆盖父类属性（隐藏）
  public publicProp: string = 'child override';

  testOverride(): void {
    console.info(`${this.publicProp}`);  // 'child override'
  }
}

let child: Child = new Child();

console.info(`${child.publicProp}`);           // 'child override'
console.info(`${child.getProtectedFromParent()}`); // 'protected'（继承）
console.info(`${child.childProp}`);            // 'child'
console.info(`${child.getParentPrivate()}`);   // 'private'

// 属性继承总结：
// public：完全继承，可覆盖
// protected：继承，子类可访问
// private：不继承，子类不可直接访问
```

**declare仅类型字段声明**：子类中重新声明继承字段的更精确类型时，使用`declare`避免运行时覆盖父类值。若不使用`declare`，子类字段的初始化器会在构造时执行，覆盖父类构造函数已设置的值，可能导致数据丢失或类型不一致；`declare`字段不会生成运行时代码，只用于确保类型正确。

<!-- @[declare_field](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Properties.ets) -->

``` TypeScript
interface DclAnimal {
  dateOfBirth: Date;
}

interface DclDog extends DclAnimal {
  breed: string;
}

class DclAnimalHouse {
  public resident: DclAnimal;

  constructor(animal: DclAnimal) {
    this.resident = animal;
  }
}

class DclDogHouse extends DclAnimalHouse {
  // declare：不生成运行时代码，仅修正类型
  public declare resident: DclDog;

  constructor(dog: DclDog) {
    super(dog);
  }
}

let dclDog: DclDog = { dateOfBirth: new Date(), breed: 'Labrador' };
let dclHouse: DclDogHouse = new DclDogHouse(dclDog);
console.info(`${dclHouse.resident.breed}`);  // 'Labrador'
```

**继承链与多级继承**：继承可形成多层结构（如`GrandParent → Parent → Child`），子类逐级继承祖先链上的成员。继承链使代码复用在多个层级间传递，但层数过深会增加理解难度和成员查找开销，建议层级不超过3层，复杂场景可考虑组合模式替代深层继承。

<!-- @[multi_level_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// 继承层级：多层继承
class GrandParent {
  methodGrandParent(): void {
    console.info('GrandParent method');
  }
}

class MultiLevelParent extends GrandParent {
  methodParent(): void {
    console.info('MultiLevelParent method');
  }
  
  methodGrandParent(): void {
    console.info('MultiLevelParent overrides GrandParent');
    super.methodGrandParent();  // 调用父类方法
  }
}

class MultiLevelChild extends MultiLevelParent {
  methodChild(): void {
    console.info('MultiLevelChild method');
  }
  
  methodParent(): void {
    console.info('MultiLevelChild overrides MultiLevelParent');
    super.methodParent();  // 调用父类方法
  }
}

let multiLevelChild: MultiLevelChild = new MultiLevelChild();

multiLevelChild.methodChild();           // 'MultiLevelChild method'
multiLevelChild.methodParent();          // 'MultiLevelChild overrides MultiLevelParent', 'MultiLevelParent method'
multiLevelChild.methodGrandParent();     // 'MultiLevelParent overrides GrandParent', 'GrandParent method'

// 继承链查找：从子类到父类
// MultiLevelChild.methodChild() -> MultiLevelChild自身
// MultiLevelChild.methodParent() -> MultiLevelChild覆盖 -> MultiLevelParent方法
// MultiLevelChild.methodGrandParent() -> MultiLevelParent覆盖 -> GrandParent方法

// 继承层级限制：避免过深继承
// 推荐：不超过3层继承
// 反例：继承层级过深，增加复杂度
```

**原型链**：原型链是类继承的底层机制，`prototype`对象存放所有实例共享的方法。访问实例成员时，引擎沿原型链从实例自身逐级向上查找：先在自身定义中匹配，未命中则依次查找父类、祖父类，直至命中为止；子类同名成员会覆盖父类成员。ArkTS通过`class extends`自动维护原型链，不支持直接操作`prototype`属性，详见[从TypeScript到ArkTS的适配规则](typescript-to-arkts-migration-guide.md#不支持在原型上赋值)。

<!-- @[prototype_chain](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class PcGrandParent {
  methodA(): void {
    console.info('GrandParent A');
  }
}

class PcParent extends PcGrandParent {
  methodB(): void {
    console.info('Parent B');
  }
}

class PcChild extends PcParent {
  methodC(): void {
    console.info('Child C');
  }
}

let pcChild: PcChild = new PcChild();

// 原型链查找
pcChild.methodA();  // GrandParent（继承）
pcChild.methodB();  // Parent（继承）
pcChild.methodC();  // Child（自身）

// 方法覆盖
class PcParent2 {
  method(): void {
    console.info('Parent method');
  }
}

class PcChild2 extends PcParent2 {
  method(): void {
    console.info('Child method');
    super.method();
  }
}

let pcChild2: PcChild2 = new PcChild2();
pcChild2.method();
```

### `super`关键字的使用

子类构造函数必须先通过`super()`调用父类构造函数完成父类部分初始化，再初始化子类自身属性。`super()`须在构造函数体中、任何`this`访问之前调用（其前可以有不含`this`的语句），参数须匹配父类构造函数签名；若子类未定义构造函数，编译器会自动生成调用父类构造函数的代码。

**TypeScript对照**

<!-- @[ts_super_call_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Initialization.ts) -->

``` TypeScript
class Vehicle {
  public brand: string;

  constructor(brand: string) {
    this.brand = brand;
    console.info(`Vehicle constructor`);
  }
}

class Car extends Vehicle {
  public model: string;

  constructor(brand: string, model: string) {
    super(brand);  // 必须先调用super()
    this.model = model;
    console.info(`Car constructor`);
  }

  getInfo(): string {
    return `${this.brand} ${this.model}`;
  }
}

let car: Car = new Car('Toyota', 'Camry');
// 输出：'Vehicle constructor', 'Car constructor'

// super() 规则：
// 1. 子类构造函数必须调用super()
// 2. super() 必须在第一行
// 3. super() 参数匹配父类构造函数

class InvalidChild extends Vehicle {
  public model: string;

  constructor(brand: string, model: string) {
    this.model = model;  // 编译错误：super() 未调用

    super(brand);  // 必须在访问this之前

    this.model = model;  // 正确
  }
}
```

子类构造函数通过`super(...)`将参数转发给父类构造函数，也可在传递前对参数做默认值处理或类型转换。

<!-- @[passing_parameters_to_super](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Initialization.ets) -->

``` TypeScript
class MultiParamParent {
  public name: string;
  public age: number;
  public email: string;
  
  constructor(name: string, age: number, email: string) {
    this.name = name;
    this.age = age;
    this.email = email;
  }
}

class MultiParamChild extends MultiParamParent {
  public phone: string;
  
  constructor(name: string, age: number, email: string, phone: string) {
    super(name, age, email);  // 传递所有父类参数
    this.phone = phone;
  }
  
  getInfo(): string {
    return `${this.name}, ${this.age}, ${this.email}, ${this.phone}`;
  }
}

let superChild: MultiParamChild = new MultiParamChild('Alice', 25, 'alice@example.com', '123-456');

// 参数处理方式：
class FlexibleParent {
  public value: number;
  
  constructor(value: number = 10) {
    this.value = value;
  }
}

class FlexibleChild extends FlexibleParent {
  public extra: number;
  
  constructor(value?: number, extra?: number) {
    super(value ?? 10);  // 传递处理后的参数
    this.extra = extra ?? 0;
  }
}

// 参数转换传递
class TransformedParent {
  public id: number;
  
  constructor(id: number) {
    this.id = id;
  }
}

class TransformedChild extends TransformedParent {
  public name: string;
  
  constructor(idString: string, name: string) {
    let id: number = Number.parseInt(idString, 10);
    super(id);  // 转换后传递
    this.name = name;
  }
}
```

在实例方法中通过`super.方法名()`调用父类实例方法，常在覆盖方法中复用父类逻辑后再添加子类特有行为。

<!-- @[super_keyword](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Parent {
  greet(): string {
    return 'Hello from Parent';
  }
  
  process(): void {
    console.info('Parent processing');
  }
}

class Child extends Parent {
  greet(): string {
    return 'Hello from Child';
  }
  
  greetWithParent(): string {
    return `${super.greet()} and ${this.greet()}`;
  }
  
  process(): void {
    super.process();  // 调用父类方法
    console.info('Child processing');
  }
}

let child: Child = new Child();
console.info(`${child.greetWithParent()}`);  
// 'Hello from Parent and Hello from Child'

child.process();
// 输出：Parent processing, Child processing

// super在构造函数中
class KwBase {
  protected value: number;
  
  constructor(value: number) {
    this.value = value;
  }
}

class Extended extends KwBase {
  public multiplier: number;
  
  constructor(value: number, multiplier: number) {
    super(value);  // 必须先调用super
    this.multiplier = multiplier;
  }
  
  getCalculated(): number {
    return this.value * this.multiplier;
  }
}
```

子类静态方法中可通过`super.静态方法名()`或父类类名调用父类静态成员。

<!-- @[static_method_call](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
class StaticBase {
  public static baseValue: number = 10;

  static baseMethod(): void {
    console.info(`Base static method`);
  }

  static getValue(): number {
    return StaticBase.baseValue;
  }
}

class StaticChild extends StaticBase {
  public static childValue: number = 20;

  // 子类静态方法调用父类静态方法
  static combinedMethod(): void {
    StaticBase.baseMethod();   // 通过父类名调用
    StaticChild.baseMethod();  // 通过子类名调用（继承）
  }

  // 子类静态方法访问父类静态属性
  static getTotalValue(): number {
    return StaticBase.baseValue + StaticChild.childValue;
  }

  // 调用继承的静态方法
  static getInheritedValue(): number {
    return StaticChild.getValue();  // 继承的静态方法
  }

  // 静态方法中可通过super调用父类静态方法
  static callViaSuper(): void {
    super.baseMethod();  // 通过super调用父类静态方法
  }
}

StaticChild.combinedMethod();       // 'Base static method', 'Base static method'
console.info(`${StaticChild.getTotalValue()}`);       // 30
console.info(`${StaticChild.getInheritedValue()}`);   // 10
StaticChild.callViaSuper();         // 'Base static method'

// 静态方法调用规则：
// 通过类名调用静态成员
// 子类名可调用继承的静态成员
// 可通过super调用父类静态方法
```

`super`的使用限制：`super()`须在任何`this`访问之前调用；不能通过`super`直接访问父类实例属性（应使用`this`访问）；`super`只能用于上述调用场景。

**TypeScript对照**

<!-- @[ts_super_usage_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class SuperBase {
  public value: number = 10;

  method(): void {
    console.info(`Base method`);
  }

  static staticMethod(): void {
    console.info(`Base static method`);
  }
}

class SuperChild extends SuperBase {
  public value: number = 20;

  method(): void {
    // super调用父类方法
    super.method();  // 正确

    // super不能直接访问父类实例属性
    console.info(`${super.value}`);  // 编译错误：不能通过super访问父类实例属性，应使用this访问

    // 应使用this或父类名访问属性
    console.info(`${this.value}`);          // 20（子类属性）
    console.info(`${SuperChild.prototype.value}`); // 反例：父类属性
  }

  anotherMethod(): void {
    // super只能调用方法
    super.method();

    // 不能用于其他场景
    let base: SuperBase = super;  // 编译错误
    return super;  // 编译错误
  }

  static childStaticMethod(): void {
    // 静态方法中使用super调用父类静态方法
    super.staticMethod();

    // 也可使用类名调用
    SuperBase.staticMethod();
  }

  constructor() {
    super();  // 构造函数中使用super() 调用父类构造
  }
}
```

### `override`关键字和方法覆盖

方法覆盖指子类重新定义父类的同名方法以实现多态。覆盖时须保持签名匹配：方法名相同、参数类型与数量一致、返回类型相同或兼容，且访问权限不能比父类更严格——`public`方法覆盖后必须保持`public`，`protected`方法覆盖后可保持`protected`或改为`public`，`private`方法不能覆盖。

`override`关键字标记被覆盖的方法，使编译器在父类方法被重命名或删除时发出错误提示，避免覆盖方法与父类方法意外脱钩。ArkTS中`override`为可选关键字，推荐在覆盖父类方法时显式标注`override`，以便编译器检查父类是否存在同名方法。

<!-- @[method_override](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class Base {
  method(): void {
    console.info('Base method');
  }
}

class Derived extends Base {
  // TypeScript使用override标记（可选）
  method(): void {
    console.info('Derived method');
  }
}

let derived: Derived = new Derived();
derived.method();  // 'Derived method'

// 覆盖带返回值的方法
class OverrideCalculator {
  calculate(a: number, b: number): number {
    return a + b;
  }
}

class AdvancedCalculator extends OverrideCalculator {
  calculate(a: number, b: number): number {
    return a * b;  // 改变计算逻辑
  }
}

let overrideCalc: OverrideCalculator = new AdvancedCalculator();
console.info(`${overrideCalc.calculate(3, 4)}`);  // 12

// 覆盖时保持签名一致
class Logger {
  log(message: string): void {
    console.info(`${message}`);
  }
}

class FileLogger extends Logger {
  log(message: string): void {  // 必须保持参数和返回类型一致
    // 写入文件
    console.info(`[File] ${message}`);
  }
}
```

覆盖方法的参数和返回值必须与父类方法保持匹配，确保类型安全。

**TypeScript对照**

<!-- @[ts_method_signature_match](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
class NumberProcessor {
  process(value: number): number {
    return value * 2;
  }

  convert(input: string): number {
    return Number.parseInt(input, 10);
  }
}

class AdvancedProcessor extends NumberProcessor {
  // 参数和返回值必须完全匹配
  process(value: number): number {
    return value * 3;  // 返回值类型相同
  }

  // 返回值兼容（子类返回类型可以是父类返回值的子类型）
  convert(input: string): number {
    let result: number = super.convert(input);
    return result * 10;
  }

  // 不能改变参数类型
  process(value: string): number {}  // 编译错误

  // 不能改变参数数量
  process(value: number, extra: number): number {}  // 编译错误

  // 不能改变返回类型为不兼容类型
  process(value: number): string {}  // 编译错误
}

let processor: AdvancedProcessor = new AdvancedProcessor();

console.info(`${processor.process(5).toString()}`);      // 15
console.info(`${processor.convert('10').toString()}`);   // 100

// 父类引用指向子类实例
let baseProcessor: NumberProcessor = new AdvancedProcessor();
console.info(`${baseProcessor.process(5).toString()}`);  // 15（调用子类覆盖方法）
```

覆盖方法不能降低访问权限，只能保持或提升权限。

**TypeScript对照**

<!-- @[ts_override_access_modifiers](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Methods.ts) -->

``` TypeScript
class Base {
  // public方法
  public publicMethod(): void {
    console.info(`Base public`);
  }

  // protected方法
  protected protectedMethod(): void {
    console.info(`Base protected`);
  }

  // private方法（不能覆盖）
  private privateMethod(): void {
    console.info(`Base private`);
  }

  protected loweredPublicMethod(): void {}
}

class Derived extends Base {
  // 覆盖public方法：保持public
  public publicMethod(): void {
    console.info(`Derived public`);
  }

  // 覆盖protected方法：可保持protected或改为public
  public protectedMethod(): void {
    console.info(`Derived public (was protected)`);
  }

  // 不能覆盖private方法
  // private privateMethod(): void {}  // 编译错误

  // 不能降低访问权限
  // private loweredPublicMethod(): void {}  // 编译错误：不能从protected改为private

  callProtected(): void {
    this.protectedMethod();  // 可访问父类protected
  }
}

let derived: Derived = new Derived();
derived.publicMethod();        // 'Derived public'
derived.protectedMethod();     // 'Derived public (was protected)'
derived.callProtected();       // 'Derived public (was protected)'
```

覆盖父类方法时，可以完全覆盖改变行为，也可以通过`super.方法名()`调用父类实现并添加新逻辑。

<!-- @[override_and_extend](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Methods.ets) -->

``` TypeScript
class ExtendLogger {
  log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
}

class DetailedLogger extends ExtendLogger {
  // 覆盖方法，改变行为
  log(message: string): void {
    console.info(`[DETAIL] ${message}`);
    console.info(`Timestamp: ${new Date().toISOString()}`);
  }
  
  // 保留父类方法并添加新行为
  logWithParent(message: string): void {
    super.log(message);  // 父类方法
    console.info(`Additional info for ${message}`);
  }
  
  // 新方法，不冲突
  logError(error: string): void {
    this.log(`ERROR: ${error}`);
  }
}

let detailed: DetailedLogger = new DetailedLogger();

detailed.log('test');           // [DETAIL] test, Timestamp: ...
detailed.logWithParent('test'); // [LOG] test, Additional info...
detailed.logError('failed');    // '[DETAIL] ERROR: failed'

// 父类引用
let logger: ExtendLogger = new DetailedLogger();
logger.log('test');  // [DETAIL] test（调用子类覆盖方法）
```

多态是方法覆盖的核心价值：不同子类对同一方法有不同实现，通过父类引用调用时表现出不同行为；新增子类类型不影响已有代码，且可用统一接口处理所有子类。

<!-- @[polymorphism_concept](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// 多态示例：不同子类对同一方法的不同实现
class ConceptShape {
  // 父类方法
  draw(): void {
    console.info('Drawing shape');
  }

  getArea(): number {
    return 0;
  }
}

class ConceptCircle extends ConceptShape {
  public radius: number;

  constructor(radius: number) {
    super();
    this.radius = radius;
  }

  // 覆盖方法：多态实现
  draw(): void {
    console.info(`Drawing circle with radius ${this.radius}`);
  }

  getArea(): number {
    return Math.PI * this.radius * this.radius;
  }
}

class ConceptRectangle extends ConceptShape {
  public width: number;
  public height: number;

  constructor(width: number, height: number) {
    super();
    this.width = width;
    this.height = height;
  }

  // 覆盖方法：多态实现
  draw(): void {
    console.info(`Drawing rectangle ${this.width}x${this.height}`);
  }

  getArea(): number {
    return this.width * this.height;
  }
}

// 多态：父类引用指向子类实例
let shapes: ConceptShape[] = [
  new ConceptCircle(5),
  new ConceptRectangle(10, 20),
  new ConceptCircle(3)
];

// 统一接口调用：表现出不同行为
for (let shape of shapes) {
  shape.draw();
  console.info(`Area: ${shape.getArea()}`);
}
```

### 抽象类和接口

抽象类使用`abstract`关键字声明，不能被实例化，用于定义子类的通用模板和契约：抽象方法（`abstract`修饰）强制子类实现，具体方法提供默认实现供子类继承或覆盖。

**TypeScript对照**

<!-- @[ts_abstract_class_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// 抽象类定义：不能实例化，只能继承
abstract class Animal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  // 抽象方法：子类必须实现
  abstract speak(): void;

  // 具体方法：子类可继承
  move(): void {
    console.info(`${this.name} is moving`);
  }

  // 具体方法：提供默认实现
  sleep(): void {
    console.info(`${this.name} is sleeping`);
  }
}

// 子类实现抽象类
class Dog extends Animal {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }

  // 实现抽象方法
  speak(): void {
    console.info(`${this.name} barks`);
  }

  // 覆盖具体方法
  move(): void {
    console.info(`${this.name} runs`);
  }
}

class Cat extends Animal {
  public color: string;

  constructor(name: string, color: string) {
    super(name);
    this.color = color;
  }

  // 实现抽象方法
  speak(): void {
    console.info(`${this.name} meows`);
  }
}

// 不能实例化抽象类
let animal: Animal = new Animal('Test');  // 编译错误

// 通过子类使用
let dog: Dog = new Dog('Max', 'Labrador');
let cat: Cat = new Cat('Whiskers', 'Orange');

dog.speak();  // Max barks（实现的方法）
dog.move();   // Max runs（覆盖的方法）
dog.sleep();  // Max is sleeping（继承的方法）

cat.speak();  // Whiskers meows（实现的方法）
cat.move();   // Whiskers is moving（继承的方法）
cat.sleep();  // Whiskers is sleeping（继承的方法）
```

`implements`子句用于检查类是否满足接口契约。与`extends`不同，`implements`仅做类型检查，不继承实现；一个类可以同时使用`extends`和`implements`，也可以实现多个接口。

<!-- @[implements_clause](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
interface InhComparable {
  compareTo(other: Object): number;
}

class InhProduct implements InhComparable {
  public price: number;

  constructor(price: number) {
    this.price = price;
  }

  compareTo(other: Object): number {
    if (other instanceof InhProduct) {
      return this.price - other.price;
    }
    return 0;
  }
}

class InhDiscountedProduct extends InhProduct implements InhComparable {
  public discount: number;

  constructor(price: number, discount: number) {
    super(price);
    this.discount = discount;
  }

  getFinalPrice(): number {
    return this.price * (1 - this.discount);
  }
}
```

ArkTS只支持单继承，不支持多继承（如`class C extends A, B`会编译报错）。限制为单继承的原因是：多继承会引入菱形继承问题——当两个父类定义了同名方法时，子类无法确定继承哪一个，导致歧义。需要组合多个类型的行为时，使用`implements`实现多个接口替代多继承，接口只定义契约不包含实现，不会产生冲突。

**TypeScript对照**

<!-- @[ts_single_inheritance_limitation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// ArkTS只支持单继承：一个子类只能有一个父类
class ParentA {
  methodA(): void {
    console.info(`Method A`);
  }
}

class ParentB {
  methodB(): void {
    console.info(`Method B`);
  }
}

// 不能同时继承ParentB
class ErrorChild extends ParentA, ParentB {}  // 编译错误

// 单继承：只能继承一个父类
class Child extends ParentA {
  // 可以继承ParentA
  methodA(): void {
    super.methodA();
    console.info(`Child overrides Method A`);
  }
}

let child: Child = new Child();
child.methodA();  // 'Method A', 'Child overrides Method A'
```

通过实现多个接口，组合多种行为契约。

<!-- @[interface_multi_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Inheritance.ets) -->

``` TypeScript
// 多继承的替代方案：接口实现
interface IFeatureA {
  methodA(): void;
}

interface IFeatureB {
  methodB(): void;
}

class MultiFeature implements IFeatureA, IFeatureB {
  methodA(): void {
    console.info(`Feature A`);
  }

  methodB(): void {
    console.info(`Feature B`);
  }
}

let multi: MultiFeature = new MultiFeature();
multi.methodA();
multi.methodB();
```

TypeScript可通过Mixin模式在运行时向类混入多个行为。**ArkTS不支持Mixin模式**，需要复用多个类的实现逻辑时，使用组合模式（在一个类中持有其他类的实例并委托调用）或接口实现替代。

**TypeScript对照**

<!-- @[ts_mixins](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Classes.ts) -->

``` TypeScript
// TypeScript写法，ArkTS不支持Mixin模式
class TsBaseWidget {
  public id: number = 0;
}

function Scoped(Base: typeof TsBaseWidget) {
  return class extends Base {
    public scope: string = 'local';
  };
}

let ScopedWidget = Scoped(TsBaseWidget);
let tsWidget = new ScopedWidget();
console.info(`${tsWidget.scope}`); // 'local'
```

ArkTS替代：组合模式。

<!-- @[mixin_composition_alternative](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
interface MixinLoggable {
  log(message: string): void;
}

class MixinConsoleLogger implements MixinLoggable {
  log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
}

class MixinService {
  public logger: MixinLoggable;

  constructor(logger: MixinLoggable) {
    this.logger = logger;
  }

  processData(data: string): void {
    this.logger.log(`Processing: ${data}`);
  }
}

let mixinService: MixinService = new MixinService(new MixinConsoleLogger());
mixinService.processData('test'); // '[LOG] Processing: test'
```

**继承内置类型**：继承`Error`、`Array`等内置类型在ES5 target下可能遇到原型链问题，需要手动修复。ArkTS不支持`Object.setPrototypeOf`和`prototype`操作，继承内置类型时优先使用组合而非继承。

**TypeScript对照**

<!-- @[ts_inherit_builtin_error](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Inheritance.ts) -->

``` TypeScript
// TypeScript对照写法，演示继承Error时修复原型链
class InhAppError extends Error {
  public code: number;

  constructor(message: string, code: number) {
    super(message);
    this.code = code;

    // 修复原型链（target为ES5时需要）
    Object.setPrototypeOf(this, InhAppError.prototype);
  }

  getInfo(): string {
    return `[${this.code}] ${this.message}`;
  }
}

let inhError: InhAppError = new InhAppError('Not found', 404);
console.info(`${inhError.getInfo()}`);  // '[404] Not found'
console.info(`${(inhError instanceof InhAppError).toString()}`);  // true
console.info(`${(inhError instanceof Error).toString()}`);  // true
```

## 装饰器

ArkTS支持类装饰器、方法装饰器、访问器装饰器、属性装饰器和参数装饰器。装饰器实现需遵循ArkTS语法规则：使用箭头函数替代函数表达式、显式标注类型、避免独立`this`。ArkUI的`@Component`、`@Entry`、状态装饰器，以及并发场景中的`@Sendable`、`@Concurrent`属于框架或并发模型定义的专用装饰器。

### 类装饰器

类装饰器通过函数修饰类声明，在类创建时执行装饰逻辑。

<!-- @[class_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logged(constructor: Function): void {
  console.info(`Class ${constructor.name} created`);
}

@logged
class DecoService {
  public name: string = 'default';
}

let decoService: DecoService = new DecoService();
// 控制台输出：Class DecoService created
```

### 装饰器工厂

装饰器工厂返回一个装饰器函数，可接收参数进行配置。

<!-- @[decorator_factory_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function format(prefix: string): (constructor: Function) => void {
  return (constructor: Function): void => {
    console.info(`${prefix} ${constructor.name}`);
  };
}

@format('Created')
class DecoFactoryService {
  public id: number = 0;
}

let decoFactoryService: DecoFactoryService = new DecoFactoryService();
// 控制台输出：Created DecoFactoryService
```

### 方法装饰器

方法装饰器接收`target`、`propertyKey`和`descriptor`三个参数，可读取或修改方法描述符。

<!-- @[method_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logMethod(target: Object, propertyKey: string, descriptor: PropertyDescriptor): void {
  console.info(`Method ${propertyKey} decorated`);
}

class DecoCalculator {
  @logMethod
  add(a: number, b: number): number {
    return a + b;
  }
}

let decoCalc: DecoCalculator = new DecoCalculator();
console.info(`${decoCalc.add(1, 2)}`); // 3
```

### 访问器装饰器

访问器装饰器用于修饰`get`/`set`访问器，参数与方法装饰器相同。

<!-- @[accessor_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logAccessor(target: Object, propertyKey: string, descriptor: PropertyDescriptor): void {
  console.info(`Accessor ${propertyKey} decorated`);
}

class DecoCounter {
  private _count: number = 0;

  @logAccessor
  get count(): number {
    return this._count;
  }

  set count(value: number) {
    this._count = value;
  }
}

let decoCounter: DecoCounter = new DecoCounter();
decoCounter.count = 5;
console.info(`${decoCounter.count}`); // 5
```

### 属性装饰器

属性装饰器接收`target`和`propertyKey`两个参数，常用于标记或注入。

<!-- @[property_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logProperty(target: Object, propertyKey: string): void {
  console.info(`Property ${propertyKey} decorated`);
}

class DecoConfig {
  @logProperty
  public name: string = 'default';
}

let decoConfig: DecoConfig = new DecoConfig();
console.info(`${decoConfig.name}`); // 'default'
```

### 参数装饰器

参数装饰器接收`target`、`propertyKey`和`parameterIndex`三个参数，常用于参数验证标记。

<!-- @[parameter_decorator_usage](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
function logParam(target: Object, propertyKey: string, parameterIndex: number): void {
  console.info(`Param ${parameterIndex} of ${propertyKey} decorated`);
}

class DecoProcessor {
  process(@logParam input: string): string {
    return input.toUpperCase();
  }
}

let decoProc: DecoProcessor = new DecoProcessor();
console.info(`${decoProc.process('hello')}`); // 'HELLO'
```

### 使用继承或组合实现横切逻辑

装饰器之外的另一种选择是通过基类继承（在父类构造函数或方法中注入日志等逻辑）或组合（持有一个功能对象并委托调用）实现横切逻辑。

<!-- @[base_class_pattern](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Classes.ets) -->

``` TypeScript
class LoggedBase {
  private className: string;

  constructor(className: string) {
    this.className = className;
    console.info(`Creating ${className}`);
  }

  protected log(methodName: string): void {
    console.info(`Calling ${this.className}.${methodName}`);
  }
}

class UserService extends LoggedBase {
  constructor() {
    super('UserService');
  }

  getData(): string {
    this.log('getData');
    return 'data';
  }
}

let service: UserService = new UserService();
console.info(`${service.getData()}`);
```
