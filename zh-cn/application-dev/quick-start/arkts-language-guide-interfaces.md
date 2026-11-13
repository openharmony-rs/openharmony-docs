---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS接口的定义与实现，涵盖接口继承与组合、可选成员、泛型约束接口等。"
keywords: [ArkTS, 接口, interface, 接口继承, 可选成员, 泛型约束]
doctype: guide
status: active
---

# 接口
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

接口是ArkTS中定义对象结构的重要方式。接口定义了一组属性和方法的契约，用于约束对象的结构，实现代码的解耦和复用。

## 接口的基础概念

接口定义对象的结构契约——规定属性名、类型和可选性，不包含实现，用于类型约束和代码解耦。

### 接口的核心作用

接口在编译期约束对象结构、通过统一契约解耦模块依赖、支持多个类复用同一类型定义，是ArkTS实现松耦合与类型安全的核心机制。类通过`implements`实现接口，确保实例具备所需成员。

<!-- @[simple_interface_definition](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// 定义一个简单的接口
interface User {
  id: number;
  name: string;
  email: string;
}

// 使用接口约束对象
let user: User = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com'
};

console.info(user.name); // 'Alice'
```

## 接口的声明与实现

`interface`关键字声明接口结构，类通过`implements`实现接口契约。

### 接口的声明语法

通过`interface`关键字声明接口，定义属性（名：类型）和方法签名，描述对象的结构契约。

<!-- @[basic_interface_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// 基本接口声明
interface Point {
  x: number;
  y: number;
}

let point: Point = {
  x: 10,
  y: 20
};

console.info(`Point: (${point.x}, ${point.y})`);
```

### 接口的成员定义

接口的成员包括属性、方法和访问器。

**属性类型**

接口属性包括必选属性、可选属性（`?`）和只读属性（`readonly`）。

<!-- @[ts_interface_property_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Product {
  // 必选属性
  id: number;
  name: string;
  price: number;

  // 可选属性（使用 ?）
  description?: string;
  stock?: number;

  // 只读属性（使用readonly）
  readonly createdAt: Date;
}

let product: Product = {
  id: 1,
  name: 'Laptop',
  price: 999,
  createdAt: new Date()
};

// 可以访问可选属性
if (product.description) {
  console.info(`${product.description}`);
}

// 只读属性不能修改
product.createdAt = new Date(); // 编译错误
```

**方法声明**

接口方法包括必选方法和可选方法（`?`），类通过`implements`实现接口方法。

<!-- @[interface_method_declaration](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Calculator {
  reset(): void;
  add(a: number, b: number): number;
  subtract(a: number, b: number): number;

  // 可选方法（使用 ?）
  logResult?(): void;
}

class BasicCalculator implements Calculator {
  private result: number = 0;
  
  public reset(): void {
    this.result = 0;
    console.info('Calculator reset');
  }
  
  public add(a: number, b: number): number {
    this.result = a + b;
    return this.result;
  }
  
  public subtract(a: number, b: number): number {
    this.result = a - b;
    return this.result;
  }
  
  // 可选方法可以不实现，如需实现可参考以下写法
  public logResult(): void {
    console.info(`Result: ${this.result}`);
  }
}

let calculator: BasicCalculator = new BasicCalculator();
let sum: number = calculator.add(10, 5);
console.info(`${sum}`); // 15
```

**访问器（getter/setter）**

接口可以声明`get`/`set`访问器，要求实现类提供同名的getter和setter，用法与类的计算属性一致，详见[类的计算属性](arkts-language-guide-classes.md#计算属性)。

<!-- @[interface_accessors](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface PersonInfo {
  get fullName(): string;
  set fullName(name: string);
}

class Person implements PersonInfo {
  private firstName: string;
  private lastName: string;

  constructor(firstName: string, lastName: string) {
    this.firstName = firstName;
    this.lastName = lastName;
  }

  get fullName(): string {
    return `${this.firstName} ${this.lastName}`;
  }

  set fullName(name: string) {
    let parts: string[] = name.split(' ');
    this.firstName = parts[0];
    this.lastName = parts[1];
  }
}

let person: PersonInfo = new Person('John', 'Smith');
console.info(`${person.fullName}`); // 'John Smith'

person.fullName = 'Bob Brown';
console.info(`${person.fullName}`); // 'Bob Brown'
```

### 类实现接口

类通过`implements`关键字实现接口，必须提供接口中所有必选成员的实现，不同类可以实现同一接口提供不同行为。

<!-- @[class_implements_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Logger {
  log(message: string): void;
  error(message: string): void;
  warn(message: string): void;
}

class ConsoleLogger implements Logger {
  public log(message: string): void {
    console.info(`[LOG] ${message}`);
  }
  
  public error(message: string): void {
    console.error(`[ERROR] ${message}`);
  }
  
  public warn(message: string): void {
    console.info(`[WARN] ${message}`);
  }
}

class FileLogger implements Logger {
  private fileName: string;
  
  constructor(fileName: string) {
    this.fileName = fileName;
  }
  
  public log(message: string): void {
    // 模拟写入文件
    console.info(`Writing to ${this.fileName}: [LOG] ${message}`);
  }
  
  public error(message: string): void {
    console.info(`Writing to ${this.fileName}: [ERROR] ${message}`);
  }
  
  public warn(message: string): void {
    console.info(`Writing to ${this.fileName}: [WARN] ${message}`);
  }
}

let consoleLogger = new ConsoleLogger();
let fileLogger = new FileLogger('app.log');

consoleLogger.log('Application started');
// [LOG] Application started

fileLogger.error('Connection failed');
// Writing to app.log: [ERROR] Connection failed
```

## 接口的继承与组合

接口通过`extends`单继承和多继承复用、组合类型定义。

### 接口的单继承

接口使用`extends`继承单个父接口，子接口在父接口成员的基础上添加新成员；子接口还可以继续被继承，形成多级层次结构，最末端的子接口包含所有父接口的成员。

<!-- @[interface_multi_level_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Animal {
  name: string;
  age: number;
}

interface Pet extends Animal {
  owner: string;
}

interface Dog extends Pet {
  breed: string;
  bark(): void;
}

class DemoDog implements Dog {
  public name: string;
  public age: number;
  public owner: string;
  public breed: string;

  constructor(name: string, age: number, owner: string, breed: string) {
    this.name = name;
    this.age = age;
    this.owner = owner;
    this.breed = breed;
  }

  public bark(): void {
    console.info(`${this.name} barks: Woof! Woof!`);
  }
}

let myDog: Dog = new DemoDog('Buddy', 3, 'Alice', 'Golden Retriever');

myDog.bark(); // 'Buddy barks: Woof! Woof!'
```

### 接口的多继承

可以通过`extends`继承多个父接口，组合多个类型契约。

<!-- @[interface_multiple_inheritance](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface MiSerializable {
  serialize(): string;
}

interface MiComparable {
  compareTo(other: Object): number;
}

interface MiEntity extends MiSerializable, MiComparable {
  id: number;
}

class MiUserEntity implements MiEntity {
  public id: number;

  constructor(id: number) {
    this.id = id;
  }

  public serialize(): string {
    return `User#${this.id}`;
  }

  public compareTo(other: Object): number {
    let otherUser: MiUserEntity = other as MiUserEntity;
    return this.id - otherUser.id;
  }
}

let miUser1: MiUserEntity = new MiUserEntity(1);
let miUser2: MiUserEntity = new MiUserEntity(2);

console.info(`${miUser1.serialize()}`);        // 'User#1'
console.info(`${miUser1.compareTo(miUser2)}`); // -1
```

### 接口继承的约束规则

接口继承时可以添加新成员，也可以覆盖同名成员。覆盖方法时签名需与父接口兼容，返回类型可以不同。但不能把成员重新声明为不兼容的类型，否则会编译错误。

<!-- @[ts_interface_inheritance_rules](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Interfaces.ts) -->

``` TypeScript
interface Base {
  method(): void;
}

interface Derived extends Base {
  // 可以添加新成员
  newMethod(): void;

  // 可以覆盖同名方法，返回类型可以与父接口不同（签名兼容即可）
  method(): string;
}

// 覆盖属性时，类型必须与父接口兼容
interface Colorable {
  color: string;
}

interface BadColorable extends Colorable {
  // 不能把属性重新声明为不兼容的类型
  color: number; // 编译错误：类型不匹配
}
```

## 接口的可选成员

可选成员使用`?`标记，实现时可以省略。

### 可选属性与可选方法

可选属性和可选方法在成员名后使用`?`标记，表示该成员可能不存在，实现对象可按需提供。

<!-- @[optional_properties_methods](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Configuration {
  // 必选属性
  apiUrl: string;

  // 可选属性（使用 ?）
  timeout?: number;

  // 可选方法
  logError?: (error: Error) => void;
}

// 只提供必选成员
let config1: Configuration = {
  apiUrl: 'EXAMPLE_API_URL'
};

// 可选成员可按需提供
let config2: Configuration = {
  apiUrl: 'EXAMPLE_API_URL',
  timeout: 5000
};

// 使用可选成员前需要检查是否存在
if (config2.timeout !== undefined) {
  console.info(`Timeout: ${config2.timeout}ms`);
}

if (config2.logError) {
  config2.logError(new Error('Test error'));
}
```

### 可选成员的调用注意事项

调用可选成员前需检查是否存在，避免访问`undefined`。

<!-- @[using_optional_members](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface OptionalInterface {
  requiredMethod(): void;
  optionalMethod?(): void;
  requiredProperty: string;
  optionalProperty?: number;
}

function useOptionalInterface(obj: OptionalInterface): void {
  // 必选成员可以直接调用
  obj.requiredMethod();
  console.info(`${obj.requiredProperty}`);
  
  // 可选方法需要先检查是否存在
  if (obj.optionalMethod) {
    obj.optionalMethod();
  }
  
  // 可选属性需要先检查是否存在
  if (obj.optionalProperty !== undefined) {
    console.info(`${obj.optionalProperty}`);
  }
  
  // 使用可选链（?.）
  obj.optionalMethod?.();
  console.info(`${obj.optionalProperty?.toFixed(2)}`);
  
  // 使用空值合并（??）
  let value: number = obj.optionalProperty ?? 0;
  console.info(`${value}`);
}
```

### 替代方案：使用接口扩展实现可选成员

通过让扩展接口继承基础接口并添加可选成员，实现类可以按需决定是否提供可选能力。

<!-- @[extending_interface_with_optionals](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// 基础接口（必选成员）
interface BaseInterface {
  requiredMethod(): void;
  requiredProperty: string;
}

// 扩展接口（包含可选成员）
interface ExtendedInterface extends BaseInterface {
  optionalMethod?(): void;
  optionalProperty?: number;
}

class BaseInterfaceImpl implements BaseInterface {
  public requiredProperty: string = 'Required value';

  public requiredMethod(): void {
    console.info('Required method');
  }
}

class ExtendedInterfaceImpl implements ExtendedInterface {
  public requiredProperty: string = 'Required value';
  public optionalProperty: number = 42;

  public requiredMethod(): void {
    console.info('Required method');
  }

  public optionalMethod(): void {
    console.info('Optional method');
  }
}

// 使用基础接口
let baseObj: BaseInterface = new BaseInterfaceImpl();

// 使用扩展接口（可以选择是否提供可选成员）
let extendedObj: ExtendedInterface = new ExtendedInterfaceImpl();

// 让扩展接口继承基础接口
function processObject(obj: BaseInterface): void {
  obj.requiredMethod();
  console.info(`${obj.requiredProperty}`);
  
  // 如果传入扩展接口对象，可以先转换为扩展接口再检查可选成员
  let extended: ExtendedInterface = obj as ExtendedInterface;
  if (extended.optionalMethod !== undefined) {
    extended.optionalMethod();
  }
}

processObject(baseObj);
processObject(extendedObj);
```

## 泛型接口

泛型接口通过`<T>`引入类型参数，使一份接口适配多种数据类型。

<!-- @[generic_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
// 泛型接口
interface Container<T> {
  value: T;
  getValue(): T;
  setValue(value: T): void;
}

class NumberContainer implements Container<number> {
  public value: number;
  
  constructor(initialValue: number) {
    this.value = initialValue;
  }
  
  public getValue(): number {
    return this.value;
  }
  
  public setValue(value: number): void {
    this.value = value;
  }
}

class StringContainer implements Container<string> {
  public value: string;
  
  constructor(initialValue: string) {
    this.value = initialValue;
  }
  
  public getValue(): string {
    return this.value;
  }
  
  public setValue(value: string): void {
    this.value = value;
  }
}

let numContainer = new NumberContainer(42);
let strContainer = new StringContainer('Hello');

console.info(`${numContainer.getValue().toString()}`); // 42
console.info(`${strContainer.getValue()}`); // 'Hello'
```

泛型的详细介绍（类型约束、泛型类、泛型函数等），请阅读[泛型](arkts-language-guide-generics.md)。

## 接口与类的结合

类通过`implements`实现接口，接口定义契约、类提供实现。

### 类实现单个接口

类使用`implements`关键字实现单个接口，必须提供接口中所有必选成员的实现。

<!-- @[single_interface_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Drawable {
  draw(): void;
}

class Circle implements Drawable {
  private radius: number;
  
  constructor(radius: number) {
    this.radius = radius;
  }
  
  public draw(): void {
    console.info(`Drawing a circle with radius ${this.radius}`);
  }
}

let circle = new Circle(5);
circle.draw(); // Drawing a circle with radius 5
```

### 类实现多个接口

类通过逗号分隔实现多个接口（如`implements A, B, C`），必须提供所有接口的必选成员实现。

<!-- @[multiple_interface_implementation](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface Printable {
  print(): void;
}

interface Saveable {
  save(): void;
}

interface Loadable {
  load(): void;
}

class Document implements Printable, Saveable, Loadable {
  private title: string;
  private content: string;
  
  constructor(title: string, content: string) {
    this.title = title;
    this.content = content;
  }
  
  public print(): void {
    console.info(`Printing: ${this.title}`);
    console.info(`${this.content}`);
  }
  
  public save(): void {
    console.info(`Saving: ${this.title}`);
  }
  
  public load(): void {
    console.info(`Loading: ${this.title}`);
  }
}

let document = new Document('My Document', 'This is the content.');
document.print();
document.save();
document.load();
```

### 继承类同时实现接口

类可以同时使用`extends`继承父类和`implements`实现接口，既复用父类代码又满足接口契约。

<!-- @[class_inheritance_with_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
class BaseEntity {
  public id: number;
  public createdAt: Date;
  
  constructor(id: number) {
    this.id = id;
    this.createdAt = new Date();
  }
  
  public getInfo(): string {
    return `ID: ${this.id}, Created: ${this.createdAt}`;
  }
}

interface Named {
  name: string;
  getName(): string;
}

interface Active {
  active: boolean;
  activate(): void;
  deactivate(): void;
}

class InterfaceUser extends BaseEntity implements Named, Active {
  public name: string;
  public active: boolean;
  
  constructor(id: number, name: string) {
    super(id);
    this.name = name;
    this.active = false;
  }
  
  public getName(): string {
    return this.name;
  }
  
  public activate(): void {
    this.active = true;
    console.info(`${this.name} activated`);
  }
  
  public deactivate(): void {
    this.active = false;
    console.info(`${this.name} deactivated`);
  }
}

let interfaceUser = new InterfaceUser(1, 'Alice');
console.info(`${interfaceUser.getInfo()}`);  // 'ID: 1, Created: ...'
console.info(`${interfaceUser.getName()}`);  // 'Alice'
interfaceUser.activate();
interfaceUser.deactivate();
```

### 接口作为类的类型约束

接口可用作泛型参数的约束（如`<T extends Comparable<T>>`），限制类型参数必须实现指定接口，从而在泛型代码中安全调用接口成员。

<!-- @[comparable_equatable_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface EquatableComparable<T> {
  compareTo(other: T): number;
}

interface Equatable<T> {
  equals(other: T): boolean;
}

class NumericValue implements EquatableComparable<NumericValue>, Equatable<NumericValue> {
  public value: number;
  
  constructor(value: number) {
    this.value = value;
  }
  
  public compareTo(other: NumericValue): number {
    return this.value - other.value;
  }
  
  public equals(other: NumericValue): boolean {
    return this.value === other.value;
  }
}

let num1 = new NumericValue(10);
let num2 = new NumericValue(20);
let num3 = new NumericValue(10);

console.info(`${num1.compareTo(num2)}`); // -10
console.info(`${num1.equals(num2)}`);    // false
console.info(`${num1.equals(num3)}`);    // true

// 使用接口类型约束
function findMax<T extends EquatableComparable<T>>(items: T[]): T | null {
  if (items.length === 0) {
    return null;
  }
  
  let max: T = items[0] as T;
  for (let i = 1; i < items.length; i++) {
    let current: T = items[i] as T;
    if (current.compareTo(max) > 0) {
      max = current;
    }
  }
  return max;
}

let values: NumericValue[] = [new NumericValue(5), new NumericValue(15), new NumericValue(10)];
let maxValue = findMax(values);
console.info(`${maxValue ? maxValue.value : 0}`); // 15
```

## 接口作为类型使用

接口可以作为变量的类型标注，约束对象的结构。

### 接口作为变量类型

接口名可直接作为变量的类型标注，赋值时对象字面量必须包含所有必选成员且类型匹配，多余属性会被编译器拒绝。

<!-- @[interface_object_literal_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface LiteralPoint {
  x: number;
  y: number;
}

let literalPoint: LiteralPoint = { x: 10, y: 20 };

interface Color {
  red: number;
  green: number;
  blue: number;
}

let color: Color = { red: 255, green: 128, blue: 0 };

console.info(`LiteralPoint: (${literalPoint.x}, ${literalPoint.y})`);
console.info(`Color: RGB(${color.red}, ${color.green}, ${color.blue})`);
```

### 接口作为函数参数/返回值类型

接口作为函数参数和返回值类型，约束输入输出的结构。

<!-- @[interface_function_types](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface UserRequest {
  name: string;
  email: string;
}

interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
}

// 接口作为参数类型
function validateRequest(request: UserRequest): boolean {
  return request.name.length > 0 && request.email.includes('@');
}

// 接口作为返回值类型
function getUserName(id: number): ApiResponse<string> {
  if (id > 0) {
    return { success: true, data: 'Alice' };
  }
  return { success: false, error: 'Invalid user ID' };
}

console.info(`${validateRequest({ name: 'Alice', email: 'alice@example.com' })}`); // true

let response: ApiResponse<string> = getUserName(1);
if (response.success && response.data !== undefined) {
  console.info(`${response.data}`); // 'Alice'
}
```

### 接口类型的多态特性

接口类型变量可以指向任何实现该接口的类实例，调用同名方法时执行各自实现，实现运行时多态。

<!-- @[interface_polymorphism](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface PolyAnimal {
  name: string;
  speak(): void;
}

class PolyDog implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} barks: Woof! Woof!`);
  }
}

class Cat implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} meows: Meow!`);
  }
}

class Cow implements PolyAnimal {
  public name: string;
  
  constructor(name: string) {
    this.name = name;
  }
  
  public speak(): void {
    console.info(`${this.name} moos: Moo!`);
  }
}

// 使用接口类型实现多态
function makeAnimalSpeak(animal: PolyAnimal): void {
  animal.speak();
}

let dog = new PolyDog('Buddy');
let cat = new Cat('Whiskers');
let cow = new Cow('Daisy');

makeAnimalSpeak(dog); // 'Buddy barks: Woof! Woof!'
makeAnimalSpeak(cat); // 'Whiskers meows: Meow!'
makeAnimalSpeak(cow); // 'Daisy moos: Moo!'

// 使用接口类型的数组
let animals: PolyAnimal[] = [dog, cat, cow];

animals.forEach(animal => {
  animal.speak();
});
```

### 接口类型与具体类型的转换

接口类型变量可以通过`instanceof`判断具体类型后使用`as`断言转换回子类型，以访问实现类特有的成员。

<!-- @[interface_type_casting](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface CastingVehicle {
  brand: string;
  model: string;
}

class CastingCar implements CastingVehicle {
  public brand: string;
  public model: string;
  public doors: number;

  constructor(brand: string, model: string, doors: number) {
    this.brand = brand;
    this.model = model;
    this.doors = doors;
  }

  public drive(): void {
    console.info(`Driving ${this.brand} ${this.model}`);
  }
}

// 接口类型转换为具体类型（需要类型检查）
function processVehicle(vehicle: CastingVehicle): void {
  if (vehicle instanceof CastingCar) {
    let car: CastingCar = vehicle as CastingCar;
    console.info(`Doors: ${car.doors}`);
    car.drive();
  }
}

let car: CastingVehicle = new CastingCar('Toyota', 'Camry', 4);

processVehicle(car);
// Doors: 4
// Driving Toyota Camry
```

## implements的注意事项

`implements`子句用于检查类是否满足接口，但有几个重要限制。

**`implements`不改变类类型**——`implements`只做检查，不会将接口的类型信息传递到类体中。类中成员的类型不会从接口自动推断，必须显式标注。

**`implements`不创建可选属性**——接口中的可选属性允许不实现。实现类没有声明该属性时，实例上就不存在这个属性，通过实例访问它会编译报错；如果需要该属性，应在类中显式声明。

**`implements`只检查实例侧**——`implements`只检查类的实例成员是否满足接口，类的静态成员（`static`）不参与检查，接口中也不能声明静态成员。

<!-- @[implements_cautions](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface ImplCheckable {
  check(name: string): boolean;
}

class ImplNameChecker implements ImplCheckable {
  // implements不会把接口的类型信息传递到类体中，
  // 参数类型需显式标注，不能依赖接口推断
  check(s: string): boolean {
    return s.toLowerCase() === 'ok';
  }
}

interface ImplConfigA {
  x: number;
  y?: number;
}

class ImplC implements ImplConfigA {
  public x: number = 0;
  // y是可选成员，可以不声明；不声明时实例上不存在y属性
}

let implC: ImplC = new ImplC();
console.info(`${implC.x.toString()}`); // 0

// console.info(`${implC.y}`); // 编译错误：ImplC上不存在y属性
```

<!-- @[implements_static_members](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
interface ImplLoggable {
  log(message: string): void;
}

class ImplStaticCounter implements ImplLoggable {
  // 静态成员不参与implements检查
  private static count: number = 0;

  log(message: string): void {
    ImplStaticCounter.count++;
    console.info(`[${ImplStaticCounter.count}] ${message}`);
  }
}

let staticCounter = new ImplStaticCounter();
staticCounter.log('hello'); // '[1] hello'
```

## 抽象类与接口的对比

抽象类与接口都无法实例化。抽象类是类的抽象，用来捕捉子类的通用特性；接口是行为的抽象。在ArkTS语法中抽象类与接口的区别如下：

- 一个类只能继承一个抽象类，而一个类可以实现一个或多个接口。

<!-- @[bird_multiple_interface](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AcAnimal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }

  abstract makeSound(): void;
}

interface AcCanFly {
  fly(): void;
}

interface AcCanSwim {
  swim(): void;
}

class AcBird extends AcAnimal implements AcCanFly, AcCanSwim {
  constructor(name: string) {
    super(name);
  }

  makeSound(): void {
    console.info(`${this.name} chirps`);
  }

  fly(): void {
    console.info(`${this.name} flies`);
  }

  swim(): void {
    console.info(`${this.name} swims`);
  }
}

let acBird: AcBird = new AcBird('Sparrow');
acBird.makeSound(); // 'Sparrow chirps'
acBird.fly();       // 'Sparrow flies'
acBird.swim();      // 'Sparrow swims'
```

- 接口中不能含有静态代码块以及静态方法，而抽象类可以有静态代码块（至多一个）和静态方法。

<!-- @[abstract_vs_interface_static](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AviAbstractClass {
  static staticMethod(): void { console.info('static'); }
  static { console.info('static initialization block'); }
}
```

- 抽象类里面可以有方法的实现，但是接口没有方法的实现，是完全抽象的。

<!-- @[abstract_vs_interface_method](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AimAbstractClass {
  func(): void { console.info('func'); }
}
```

- 抽象类可以有构造函数，而接口不能有构造函数。

<!-- @[abstract_vs_interface_constructor](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Interfaces.ets) -->

``` TypeScript
abstract class AvicAbstractClass {
  constructor() {}
}
```
