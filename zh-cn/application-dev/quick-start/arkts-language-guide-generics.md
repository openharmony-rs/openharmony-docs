---
kits: ["ArkTS Kit / 方舟编程语言"]
description: "介绍ArkTS泛型的使用，涵盖泛型函数、泛型类、泛型接口、泛型约束（型变与子类型）及通用数据结构等使用场景。"
keywords: [ArkTS, 泛型, 泛型函数, 泛型类, 泛型接口, 泛型约束, 型变]
doctype: guide
status: active
---

# 泛型
<!--Kit: ArkTS-->
<!--Subsystem: ArkCompiler-->
<!--Owner: @jokerxd-liu-->
<!--Designer: @jokerxd-liu-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->

泛型是ArkTS中强大的类型系统特性，允许在定义函数、类、接口时使用类型参数，实现代码的复用和类型安全。

## 泛型基础概念

### 泛型的定义与核心价值

泛型让类型参数化，一份代码适用于多种类型且保持编译期类型安全，编译器在调用处检查类型参数后将其擦除，兼顾复用性、类型推断与零运行时开销。

<!-- @[generics_introduction](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 不使用泛型：需要为每种类型编写函数
function identityNumber(arg: number): number {
  return arg;
}

function identityString(arg: string): string {
  return arg;
}

// 使用泛型：一个函数适用于所有类型
function identity<T>(arg: T): T {
  return arg;
}

let num: number = identity<number>(42);
let str: string = identity<string>('Hello');
let bool: boolean = identity<boolean>(true);

console.info(`${num}`);   // 42
console.info(`${str}`);   // 'Hello'
console.info(`${bool}`);  // true
```

## 泛型函数

泛型函数支持多种类型参数，实现可复用的类型安全代码。

### 泛型函数的声明语法

在函数名后用`<T>`声明类型参数，在参数和返回值中使用该参数。

<!-- @[generic_function_declarations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 基本泛型函数声明
function wrap<T>(value: T): T[] {
  return [value];
}

// 箭头函数形式的泛型函数
const wrapArrow = <T>(value: T): T[] => [value];

// 使用类型别名的泛型函数
type WrapFunction = <T>(value: T) => T[];
let wrapAlias: WrapFunction = wrap;

console.info(`${wrap<number>(42)[0]}`);           // 42
console.info(`${wrapArrow<string>('Hello')[0]}`); // 'Hello'
console.info(`${wrapAlias<boolean>(true)[0]}`);   // true
```

### 类型参数的命名规范

类型参数通常使用大写字母命名，常见约定如`T`（Type）、`U`、`K`（Key）、`V`（Value）、`E`（Element）。

<!-- @[multi_type_parameter_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// K（Key）、V（Value）常用于键值对场景
function getOrDefault<K, V>(source: Map<K, V>, key: K, fallback: V): V {
  let value: V | undefined = source.get(key);
  return value !== undefined ? value : fallback;
}

let scoreByName: Map<string, number> = new Map<string, number>();
scoreByName.set('Alice', 95);
scoreByName.set('Bob', 88);

let aliceScore: number = getOrDefault(scoreByName, 'Alice', 0);
let carolScore: number = getOrDefault(scoreByName, 'Carol', 60);

console.info(`${aliceScore}`);  // 95
console.info(`${carolScore}`);  // 60
```

### 泛型函数的调用方式

调用泛型函数时可显式指定类型参数，也可省略由编译器根据实参自动推断。

<!-- @[generic_type_inference](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
function repeatItem<T>(item: T, count: number): T[] {
  let result: T[] = [];
  for (let i = 0; i < count; i++) {
    result.push(item);
  }
  return result;
}

// 显式指定类型参数
let repeatedStrings: string[] = repeatItem<string>('Hi', 3);
console.info(`${repeatedStrings.join(', ')}`); // 'Hi, Hi, Hi'

// 类型参数自动推断
let repeatedNumbers: number[] = repeatItem(7, 2);
console.info(`${repeatedNumbers.join(', ')}`); // 7, 7

// 多类型参数的泛型函数
function createPair<T, U>(first: T, second: U): [T, U] {
  return [first, second];
}

let pair1: [string, number] = createPair<string, number>('Age', 25);
let pair2: [string, number] = createPair('Height', 180); // 自动推断为 [string, number]

console.info(`${pair1[0]}: ${pair1[1]}`); // 'Age: 25'
console.info(`${pair2[0]}: ${pair2[1]}`); // 'Height: 180'
```

### 多类型参数的泛型函数

函数可声明多个类型参数（如`<T, U>`），各自独立占位，支持不同类型间的关系表达。

<!-- @[multi_type_parameter_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 多类型参数的基本用法
function swap<T, U>(a: T, b: U): [U, T] {
  return [b, a];
}

let swapped: [string, number] = swap(1, 'Hello');
console.info(`${swapped[0]}, ${swapped[1]}`); // 'Hello, 1'

// 多类型参数的复杂用法：用显式结构保存两个不同类型的值
interface PairValue<T, U> {
  left: T;
  right: U;
}

function combineValues<T, U>(left: T, right: U): PairValue<T, U> {
  return {
    left: left,
    right: right
  };
}

interface Name {
  name: string;
}

interface Age {
  age: number;
}

let nameObj: Name = { name: 'Alice' };
let ageObj: Age = { age: 25 };

let combinedObj: PairValue<Name, Age> = combineValues<Name, Age>(nameObj, ageObj);
console.info(`${combinedObj.left.name}`);
console.info(`${combinedObj.right.age}`);

// 使用类型参数创建映射函数
function mapArray<T, R>(arr: T[], mapper: (item: T) => R): R[] {
  let result: R[] = [];
  for (let item of arr) {
    result.push(mapper(item));
  }
  return result;
}

let numbers: number[] = [1, 2, 3, 4, 5];
let doubled: number[] = mapArray<number, number>(numbers, (n: number): number => n * 2);
console.info(`${doubled.join(', ')}`); // 2, 4, 6, 8, 10

let strings: string[] = ['a', 'b', 'c'];
let uppercased: string[] = mapArray<string, string>(strings, (s: string): string => s.toUpperCase());
console.info(`${uppercased.join(', ')}`); // 'A, B, C'
```

## 泛型类和泛型接口

泛型类创建类型安全的类，支持多种数据类型；泛型接口将类型参数引入契约定义，使一份接口可适配多种数据类型，常用于回调、仓库等抽象。

### 泛型类的声明与实例化

在类名后用`<T>`声明类型参数，在类的属性和方法中使用该类型参数；实例化时通过`new ClassName<Type>(...)`指定类型参数，类型一致时可省略由编译器推断。

<!-- @[generic_class_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 基本泛型类声明
class Container<T> {
  private value: T;

  constructor(initialValue: T) {
    this.value = initialValue;
  }

  public getValue(): T {
    return this.value;
  }

  public setValue(newValue: T): void {
    this.value = newValue;
  }
}

// 显式指定类型参数实例化
let numberContainer: Container<number> = new Container<number>(42);
console.info(`${numberContainer.getValue()}`); // 42
numberContainer.setValue(100);
console.info(`${numberContainer.getValue()}`); // 100

// 省略类型参数，由编译器根据变量类型标注和构造参数自动推断
let stringContainer: Container<string> = new Container('Hello');
console.info(`${stringContainer.getValue()}`); // 'Hello'
stringContainer.setValue('World');
console.info(`${stringContainer.getValue()}`); // 'World'
```

### 泛型类中的属性与方法

泛型类的属性和方法可以使用类型参数，实现类型安全的容器和操作。例如`GenericCollection<T>`的`add(item: T)`确保只能添加`T`类型元素，`get(index: number): T`返回值自动推断为`T`类型，无需类型断言。

<!-- @[generic_collection_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
class GenericCollection<T> {
  // 泛型属性
  private items: T[] = [];
  public count: number = 0;
  
  // 泛型方法
  public add(item: T): void {
    this.items.push(item);
    this.count++;
  }
  
  public remove(item: T): boolean {
    let index = this.items.indexOf(item);
    if (index > -1) {
      this.items.splice(index, 1);
      this.count--;
      return true;
    }
    return false;
  }
  
  public get(index: number): T | undefined {
    return this.items[index];
  }
  
  public getAll(): T[] {
    return this.items;
  }
  
  // 泛型方法返回泛型类型
  public filter(predicate: (item: T) => boolean): GenericCollection<T> {
    let filtered = new GenericCollection<T>();
    this.items.forEach((item: T): void => {
      if (predicate(item)) {
        filtered.add(item);
      }
    });
    return filtered;
  }
}

let collection: GenericCollection<number> = new GenericCollection<number>();
collection.add(1);
collection.add(2);
collection.add(3);
collection.add(4);
collection.add(5);

console.info(`${collection.count}`); // 5
console.info(`${collection.get(0)}`); // 1

let evenNumbers: GenericCollection<number> = collection.filter((n: number): boolean => n % 2 === 0);
console.info(`${evenNumbers.getAll().join(', ')}`); // 2, 4
```

### 多类型参数的泛型类

泛型类可声明多个类型参数（如`<K, V>`），常用于键值对等需要多种类型协作的结构。

<!-- @[multi_type_parameter_generic_class](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 多类型参数的泛型类
class ParamPair<K, V> {
  private key: K;
  private value: V;
  
  constructor(key: K, value: V) {
    this.key = key;
    this.value = value;
  }
  
  public getKey(): K {
    return this.key;
  }
  
  public getValue(): V {
    return this.value;
  }
  
  public setKey(newKey: K): void {
    this.key = newKey;
  }
  
  public setValue(newValue: V): void {
    this.value = newValue;
  }
  
  public toString(): string {
    return `(${this.key}: ${this.value})`;
  }
}

let paramPair1: ParamPair<string, number> = new ParamPair<string, number>('Age', 25);
console.info(`${paramPair1.toString()}`); // '(Age: 25)'

let paramPair2: ParamPair<number, string> = new ParamPair<number, string>(1, 'One');
console.info(`${paramPair2.toString()}`); // '(1: One)'

// 多类型参数的复杂泛型类
class Triple<A, B, C> {
  private first: A;
  private second: B;
  private third: C;
  
  constructor(first: A, second: B, third: C) {
    this.first = first;
    this.second = second;
    this.third = third;
  }
  
  public getFirst(): A {
    return this.first;
  }
  
  public getSecond(): B {
    return this.second;
  }
  
  public getThird(): C {
    return this.third;
  }
  
  public toArray(): [A, B, C] {
    return [this.first, this.second, this.third];
  }
}

let triple: Triple<string, number, boolean> = new Triple<string, number, boolean>('Hello', 42, true);
let tripleValues: [string, number, boolean] = triple.toArray();
console.info(`${tripleValues[0]}, ${tripleValues[1]}, ${tripleValues[2]}`); // 'Hello,42,true'
```

ArkTS支持元组类型（如`[A, B, C]`）作为返回类型和变量类型，元素通过索引访问（`tuple[0]`）；但不支持元组解构语法（如`let [a, b, c] = tuple`），需通过索引逐个提取。

### 泛型接口的声明语法

在接口名后用`<T>`声明类型参数，在成员签名中使用该类型参数。

<!-- @[generic_interface_basic](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 基本泛型接口声明：接口方法使用类型参数
interface MembershipChecker {
  contains<T>(items: T[], value: T): boolean;
}

class ArrayMembershipChecker implements MembershipChecker {
  public contains<T>(items: T[], value: T): boolean {
    return items.indexOf(value) > -1;
  }
}

// 泛型接口作为变量类型
let membershipChecker: MembershipChecker = new ArrayMembershipChecker();

console.info(`${membershipChecker.contains<string>(['a', 'b', 'c'], 'b')}`); // true

// 类型参数作为接口参数
interface Predicate<T> {
  test(value: T): boolean;
}

class EvenNumberPredicate implements Predicate<number> {
  public test(value: number): boolean {
    return value % 2 === 0;
  }
}

let isEven: Predicate<number> = new EvenNumberPredicate();

console.info(`${isEven.test(42)}`); // true
```

### 泛型接口作为函数类型约束

用泛型接口描述回调或函数签名，使回调的类型参数与具体实现保持一致。

<!-- @[generic_interface_callback](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 泛型接口定义函数类型
interface Callback<T> {
  invoke(result: T): void;
}

interface AsyncCallback<T> {
  invoke(result: T): Promise<void>;
}

// 使用泛型接口约束函数类型
function processData<T>(data: T, callback: Callback<T>): void {
  callback.invoke(data);
}

class StringCallback implements Callback<string> {
  public invoke(result: string): void {
    console.info(`Processed: ${result}`);
  }
}

class NumberCallback implements Callback<number> {
  public invoke(result: number): void {
    console.info(`Processed: ${result}`);
  }
}

processData<string>('Hello', new StringCallback());

processData<number>(42, new NumberCallback());

// 异步函数使用泛型接口
async function processAsyncData<T>(data: T, callback: AsyncCallback<T>): Promise<void> {
  await callback.invoke(data);
}

class AsyncStringCallback implements AsyncCallback<string> {
  public async invoke(result: string): Promise<void> {
    console.info(`Async processed: ${result}`);
  }
}

processAsyncData<string>('Hello', new AsyncStringCallback());
```

### 泛型接口作为类的实现约束

类实现泛型接口时需指定具体类型参数，统一约束该类对外暴露的方法签名与实体类型。

<!-- @[generic_interface_repository](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface Repository<T> {
  findById(id: number): T | null;
  findAll(): T[];
  save(entity: T): void;
  delete(id: number): void;
}

interface User {
  id: number;
  name: string;
  email: string;
}

class UserRepository implements Repository<User> {
  private users: User[] = [];
  
  public findById(id: number): User | null {
    return this.users.find((user: User): boolean => user.id === id) ?? null;
  }
  
  public findAll(): User[] {
    return [...this.users];
  }
  
  public save(entity: User): void {
    let existing: User | null = this.findById(entity.id);
    if (existing !== null) {
      let index = this.users.indexOf(existing);
      this.users[index] = entity;
    } else {
      this.users.push(entity);
    }
  }
  
  public delete(id: number): void {
    this.users = this.users.filter((user: User): boolean => user.id !== id);
  }
}

let userRepo = new UserRepository();

userRepo.save({ id: 1, name: 'Alice', email: 'alice@example.com' });
userRepo.save({ id: 2, name: 'Bob', email: 'bob@example.com' });

console.info(`${userRepo.findAll().length}`); // 2
console.info(`${userRepo.findById(1)?.name}`); // 'Alice'

userRepo.delete(1);
console.info(`${userRepo.findAll().length}`); // 1
```

### 泛型接口的默认类型参数

泛型接口的默认类型参数在未指定时使用默认类型，简化调用。

<!-- @[generic_interface_default_type](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 泛型接口的默认类型参数
interface ApiResponse<T = string> {
  data: T;
  status: number;
  message: string;
}

// 使用默认类型：T为string
let response1: ApiResponse = {
  data: 'OK',
  status: 200,
  message: 'Success'
};

// 指定具体类型：覆盖默认类型，T为number
let response2: ApiResponse<number> = {
  data: 42,
  status: 200,
  message: 'Success'
};

console.info(`${response1.data}`);
console.info(`${response2.data}`);

// 多类型参数的默认值
interface DefaultPair<T = string, U = number> {
  first: T;
  second: U;
}

let defaultPair1: DefaultPair = { first: 'Hello', second: 42 };
let defaultPair2: DefaultPair<number> = { first: 100, second: 200 };
let pair3: DefaultPair<number, string> = { first: 100, second: 'Hello' };

console.info(`${defaultPair1}`);
console.info(`${defaultPair2}`);
console.info(`${pair3}`);
```

## 泛型约束

泛型约束处理泛型与子类型系统的两类关系。一类是型变标注，声明类型参数的子类型关系如何传递到泛型类型本身；另一类是子类型约束，通过`extends`限定类型参数必须是某个类型的子类型。

### 型变标注

子类型关系的基本概念（若类型S的任意值都可以安全地赋给类型T的变量，则S是T的子类型）已在[子类型](arkts-language-guide-types.md#子类型)中介绍。型变描述该关系如何从类型参数传递到泛型类型本身：

- 协变（`out`）：子类型关系保持方向，`Producer<Cat>`是`Producer<Animal>`的子类型。
- 逆变（`in`）：子类型关系方向反转，`Consumer<Animal>`是`Consumer<Cat>`的子类型。
- 不变（`in out`）：泛型类型之间无子类型关系。

ArkTS支持`in`/`out`/`in out`型变标注语法。

<!-- @[variance_annotations](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface VaConsumer<in T> {
  consume(arg: T): void;
}

interface VaProducer<out T> {
  make(): T;
}

interface VaProducerConsumer<in out T> {
  consume(arg: T): void;
  make(): T;
}

class VaAnimal {
  public name: string;

  constructor(name: string) {
    this.name = name;
  }
}

class VaDog extends VaAnimal {
  public breed: string;

  constructor(name: string, breed: string) {
    super(name);
    this.breed = breed;
  }
}

// 协变（out）：VaProducer<VaDog>是VaProducer<VaAnimal>的子类型
class VaDogFactory implements VaProducer<VaDog> {
  public make(): VaDog {
    return new VaDog('Buddy', 'Golden Retriever');
  }
}

let vaAnimalFactory: VaProducer<VaAnimal> = new VaDogFactory();
console.info(`${vaAnimalFactory.make().name}`); // 'Buddy'

// 逆变（in）：VaConsumer<VaAnimal>是VaConsumer<VaDog>的子类型
class VaAnimalFeeder implements VaConsumer<VaAnimal> {
  public consume(arg: VaAnimal): void {
    console.info(`Feeding: ${arg.name}`);
  }
}

let vaDogFeeder: VaConsumer<VaDog> = new VaAnimalFeeder();
vaDogFeeder.consume(new VaDog('Max', 'Beagle')); // Feeding: Max

// 不变（in out）：VaProducerConsumer<VaAnimal>与VaProducerConsumer<VaDog>互不为子类型，相互赋值会编译报错
```

ArkTS泛型默认不变，型变关系需通过`in`/`out`/`in out`显式标注，编译器会校验标注的合法性。

### 子类型约束

通过`extends`对类型参数施加约束，限定其必须满足的接口或结构，使泛型在灵活性与类型安全间取得平衡。

用`<T extends SomeInterface>`约束类型参数必须具备特定结构（如`length`属性），不满足则编译报错。

<!-- @[ts_generic_constraint_length](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Generics.ts) -->

``` TypeScript
// 约束泛型参数必须具有length属性
interface Lengthwise {
  length: number;
}

function getLength<T extends Lengthwise>(arg: T): number {
  return arg.length;
}

class LengthSample implements Lengthwise {
  public length: number;

  constructor(length: number) {
    this.length = length;
  }
}

console.info(`${getLength('Hello')}`);        // 5
console.info(`${getLength([1, 2, 3])}`);      // 3
console.info(`${getLength(new LengthSample(10))}`); // 10

// 编译错误：number类型没有length属性
console.info(`${getLength(42)}`);
```

将类型参数约束为某个接口或类，确保泛型函数内可调用该接口定义的方法。

<!-- @[ts_generic_constraint_serializable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/tsPages/Generics.ts) -->

``` TypeScript
interface Serializable {
  serialize(): string;
}

class User implements Serializable {
  public name: string;
  public age: number;

  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }

  public serialize(): string {
    return JSON.stringify({ name: this.name, age: this.age });
  }
}

class Product implements Serializable {
  public id: number;
  public title: string;

  constructor(id: number, title: string) {
    this.id = id;
    this.title = title;
  }

  public serialize(): string {
    return JSON.stringify({ id: this.id, title: this.title });
  }
}

// 约束泛型参数必须实现Serializable接口
function saveToStorage<T extends Serializable>(entity: T): void {
  let serialized = entity.serialize();
  console.info(`Saving: ${serialized}`);
}

let user = new User('Alice', 25);
let product = new Product(1, 'Laptop');

saveToStorage(user);    // Saving: {"name":"Alice","age":25}
saveToStorage(product); // Saving: {"id":1,"title":"Laptop"}

// 编译错误：number类型没有serialize方法
saveToStorage(42);
```

通过接口定义所需属性集合，约束类型参数必须同时拥有这些属性。

<!-- @[generic_constraint_property](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface HasId {
  id: number;
}

interface HasName {
  name: string;
}

// 约束泛型参数必须包含id属性
function findById<T extends HasId>(items: T[], id: number): T | null {
  for (let item of items) {
    if (item.id === id) {
      return item;
    }
  }
  return null;
}

// 约束泛型参数必须包含name属性
function findByName<T extends HasName>(items: T[], name: string): T | null {
  for (let item of items) {
    if (item.name === name) {
      return item;
    }
  }
  return null;
}

interface ConstraintUser extends HasId, HasName {
  email: string;
}

let users: ConstraintUser[] = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' }
];

let userById: ConstraintUser | null = findById<ConstraintUser>(users, 1);
let userByName: ConstraintUser | null = findByName<ConstraintUser>(users, 'Bob');
console.info(`${userById ? userById.name : ''}`);    // 'Alice'
console.info(`${userByName ? userByName.id : 0}`); // 2
```

## 泛型的使用场景

泛型常用于通用数据结构、工具函数和网络请求封装。

### 通用数据结构

泛型数据结构（队列、栈、链表等）适用于任意元素类型。

<!-- @[generic_data_structures](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 通用队列数据结构
class Queue<T> {
  private items: T[] = [];
  
  enqueue(item: T): void {
    this.items.push(item);
  }
  
  dequeue(): T | undefined {
    return this.items.shift();
  }
  
  front(): T | undefined {
    return this.items[0];
  }
  
  isEmpty(): boolean {
    return this.items.length === 0;
  }
  
  size(): number {
    return this.items.length;
  }
}

let stringQueue = new Queue<string>();
stringQueue.enqueue('First');
stringQueue.enqueue('Second');
stringQueue.enqueue('Third');

console.info(`${stringQueue.dequeue()}`); // 'First'
console.info(`${stringQueue.front()}`);   // 'Second'
console.info(`${stringQueue.size()}`);    // 2
```

### 通用工具函数

泛型工具函数如`map`、`filter`适用于任意类型的集合操作。

<!-- @[generic_array_utilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 通用数组工具函数
function utilitiesFirst<T>(arr: T[]): T | undefined {
  return arr[0];
}

function last<T>(arr: T[]): T | undefined {
  return arr[arr.length - 1];
}

function shuffle<T>(arr: T[]): T[] {
  let result = [...arr];
  for (let i = result.length - 1; i > 0; i--) {
    let j = Math.floor(Math.random() * (i + 1));
    let temp: T = result[i];
    result[i] = result[j];
    result[j] = temp;
  }
  return result;
}

function unique<T>(arr: T[]): T[] {
  return Array.from(new Set(arr));
}

let utilitiesNumbers: number[] = [1, 2, 3, 4, 5, 3, 2];
let utilitiesStrings: string[] = ['a', 'b', 'c', 'b', 'a'];

let firstResult: number | undefined = utilitiesFirst(utilitiesNumbers);
console.info(`${firstResult}`);  // 1

let lastResult: string | undefined = last(utilitiesStrings);
console.info(`${lastResult}`);  // 'a'

let shuffled: number[] = shuffle(utilitiesNumbers);
console.info(`${shuffled.join(', ')}`);  // 随机打乱

let uniqueNumbers: number[] = unique(utilitiesNumbers);
console.info(`${uniqueNumbers.join(', ')}`);  // 1, 2, 3, 4, 5

let uniqueStrings: string[] = unique(utilitiesStrings);
console.info(`${uniqueStrings.join(', ')}`);  // 'a, b, c'

interface UtilitiesUser {
  id: number;
  name: string;
  email: string;
}

let utilitiesUser: UtilitiesUser = {
  id: 1,
  name: 'Alice',
  email: 'alice@example.com'
};

// ArkTS中优先使用明确的属性访问，避免依赖keyof和索引访问类型
function renameUser(target: UtilitiesUser, newName: string): void {
  target.name = newName;
}

console.info(`${utilitiesUser.name}`);  // 'Alice'
renameUser(utilitiesUser, 'Bob');
console.info(`${utilitiesUser.name}`);  // 'Bob'
```

### 组件封装

泛型组件通过类型参数描述`props`、`render`等结构，使同一组件适配多种数据类型而不失去类型安全。

<!-- @[generic_ui_components](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
// 通用列表组件
interface ListComponentProps<T> {
  items: T[];
  renderItem: (item: T, index: number) => string;
  onItemClick?: (item: T, index: number) => void;
}

class ListComponent<T> {
  private props: ListComponentProps<T>;
  
  constructor(props: ListComponentProps<T>) {
    this.props = props;
  }
  
  render(): string {
    let itemsHtml = this.props.items.map((item, index) =>
      this.props.renderItem(item, index)
    ).join('');
    
    return `<ul>${itemsHtml}</ul>`;
  }
  
  handleClick(index: number): void {
    if (this.props.onItemClick) {
      this.props.onItemClick(this.props.items[index], index);
    }
  }
}

interface ComponentsUser {
  id: number;
  name: string;
  email: string;
}

let componentsUsers: ComponentsUser[] = [
  { id: 1, name: 'Alice', email: 'alice@example.com' },
  { id: 2, name: 'Bob', email: 'bob@example.com' },
  { id: 3, name: 'Charlie', email: 'charlie@example.com' }
];

let userList = new ListComponent<ComponentsUser>({
  items: componentsUsers,
  renderItem: (user) => `<li>${user.name} (${user.email})</li>`,
  onItemClick: (user) => console.info(`Clicked: ${user.name}`)
});

console.info(`${userList.render()}`);

// 通用表格组件
interface TableColumn<T> {
  header: string;
  getValue: (row: T) => string;
}

interface TableComponentProps<T> {
  columns: TableColumn<T>[];
  data: T[];
}

class TableComponent<T> {
  private props: TableComponentProps<T>;
  
  constructor(props: TableComponentProps<T>) {
    this.props = props;
  }
  
  render(): string {
    let headerHtml = this.props.columns.map(col =>
      `<th>${col.header}</th>`
    ).join('');
    
    let bodyHtml = this.props.data.map(row => {
      let cells = this.props.columns.map(col => {
        return `<td>${col.getValue(row)}</td>`;
      }).join('');
      return `<tr>${cells}</tr>`;
    }).join('');
    
    return `<table><thead><tr>${headerHtml}</tr></thead><tbody>${bodyHtml}</tbody></table>`;
  }
}

let userTable = new TableComponent<ComponentsUser>({
  columns: [
    { header: 'ID', getValue: (row: ComponentsUser): string => row.id.toString() },
    { header: 'Name', getValue: (row: ComponentsUser): string => row.name },
    { header: 'Email', getValue: (row: ComponentsUser): string => row.email }
  ],
  data: componentsUsers
});

console.info(`${userTable.render()}`);
```

### 接口请求封装

泛型封装网络请求，统一处理不同接口的请求和响应类型。

<!-- @[generic_api_client](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/Start/LearningArkTs/ArkTSFullLanguageGuide/entry/src/main/ets/pages/Generics.ets) -->

``` TypeScript
interface ClientApiResponse<T> {
  data: T;
  status: number;
  message: string;
}

class ApiClient {
  private baseUrl: string;

  constructor(baseUrl: string) {
    this.baseUrl = baseUrl;
  }

  async get<T>(endpoint: string): Promise<ClientApiResponse<T>> {
    let url: string = `${this.baseUrl}${endpoint}`;
    let result: string = await this.mockRequest(url);
    let data: T = JSON.parse(result) as T;
    return { data: data, status: 200, message: 'Success' };
  }

  async post<T, U>(endpoint: string, body: T): Promise<ClientApiResponse<U>> {
    let url: string = `${this.baseUrl}${endpoint}`;
    let result: string = await this.mockRequest(url);
    let data: U = JSON.parse(result) as U;
    return { data: data, status: 200, message: 'Success' };
  }

  private mockRequest(url: string): Promise<string> {
    return new Promise<string>((resolve: (value: string) => void): void => {
      setTimeout(() => {
        resolve(JSON.stringify({ id: 1, name: 'Alice', email: 'alice@example.com' }));
      }, 100);
    });
  }
}

interface ClientUser {
  id: number;
  name: string;
  email: string;
}

interface CreateUserRequest {
  name: string;
  email: string;
}

let gacClient: ApiClient = new ApiClient('EXAMPLE_API_URL');

async function gacFetchUser(id: number): Promise<void> {
  try {
    let response: ClientApiResponse<ClientUser> = await gacClient.get<ClientUser>(`/users/${id}`);
    console.info(`${response.data.name}`); // 'Alice'
  } catch (error) {
    console.error(`Error: ${(error as Error).message}`);
  }
}

async function gacCreateUser(name: string, email: string): Promise<void> {
  try {
    let request: CreateUserRequest = { name: name, email: email };
    let response: ClientApiResponse<ClientUser> = await gacClient.post<CreateUserRequest, ClientUser>('/users', request);
    console.info(`${response.data.id}`); // 1
  } catch (error) {
    console.error(`Error: ${(error as Error).message}`);
  }
}

gacFetchUser(1);
gacCreateUser('Alice', 'alice@example.com');
```
