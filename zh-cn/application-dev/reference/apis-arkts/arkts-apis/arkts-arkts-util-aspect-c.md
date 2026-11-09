# Aspect

```TypeScript
class Aspect
```

提供支持面向切面编程（AOP）的 API。这些 API 可用于对类方法进行插桩或替换。

**起始版本：** 11

<!--Device-util-class Aspect--><!--Device-util-class Aspect-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## addAfter

```TypeScript
static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void
```

在指定的类方法执行后插入一段逻辑。最终返回插入函数执行后的返回值。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Aspect-static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void--><!--Device-Aspect-static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetClass | Object | 是 | 指定的类对象。 |
| methodName | string | 是 | 指定的原方法名，不支持read-only方法。 |
| isStatic | boolean | 是 | 指定的原方法是否为静态方法。true表示静态方法，false表示实例方法。 |
| after | Function | 是 | 要插入的函数。函数有参数时，则第一个参数是this对象（若isStatic为true，则为类对象即targetClass；若isStatic为false，则为调用方法的实例对象），第二个参数是原方法的返回值（如果原方法没有返回值，则为undefined），其余参数是原方法的参数。函数也可以无参，无参时不做处理。 |

**示例**

```TypeScript
class MyClass {
  msg: string = 'msg000';
  foo(arg: string): string {
    console.info('foo arg is ' + arg);
    return this.msg;
  }
}

let asp = new MyClass();
let result = asp.foo('123');
// 输出结果：foo arg is 123
console.info('result is ' + result);
// 输出结果：result is msg000
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg000

util.Aspect.addAfter(MyClass, 'foo', false, (instance: MyClass, ret: string, arg: string): string => {
  console.info('arg is ' + arg);
  console.info('ret is ' + ret);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
  return 'msg222';
});

result = asp.foo('123');
// 输出结果：foo arg is 123
// 输出结果：arg is 123
// 输出结果：ret is msg000
// 输出结果：msg is changed to msg111
console.info('result is ' + result);
// 输出结果：result is msg222
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg111

// 分别添加前置和后置插桩的例子
class AroundTest {
  foo(arg: string) {
    console.info('execute foo with arg ' + arg);
  }
}
util.Aspect.addBefore(AroundTest, 'foo', false, () => {
  console.info('execute before');
});
util.Aspect.addAfter(AroundTest, 'foo', false, () => {
  console.info('execute after');
});

(new AroundTest()).foo('hello');
// 输出结果：execute before
// 输出结果：execute foo with arg hello
// 输出结果：execute after
```

## addBefore

```TypeScript
static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void
```

在指定的类对象的原方法执行前插入一个函数，适用于日志记录、性能监控、权限校验等需要在方法执行前进行拦截处理的场景。执行addBefore接口后，先运行插入的函数逻辑，再执行指定类对象的原方法。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Aspect-static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void--><!--Device-Aspect-static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetClass | Object | 是 | 指定的类对象。 |
| methodName | string | 是 | 指定的原方法名，不支持read-only方法。 |
| isStatic | boolean | 是 | 指定的原方法是否为静态方法。true表示静态方法，false表示实例方法。 |
| before | Function | 是 | 要插入的函数对象。函数有参数，则第一个参数是this对象（若isStatic为true，则为类对象即targetClass；若isStatic为false，则为调用方法的实例对象），其余参数是原方法的参数。函数也可以无参数，无参时不做处理。 |

**示例**

```TypeScript
class MyClass {
  msg: string = 'msg000';
  foo(arg: string): string {
    console.info('foo arg is ' + arg);
    return this.msg;
  }

  static data: string = 'data000';
  static bar(arg: string): string {
    console.info('bar arg is ' + arg);
    return MyClass.data;
  }
}

let asp = new MyClass();
let result = asp.foo('123');
// 输出结果：foo arg is 123
console.info('result is ' + result);
// 输出结果：result is msg000
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg000

util.Aspect.addBefore(MyClass, 'foo', false, (instance: MyClass, arg: string) => {
  console.info('arg is ' + arg);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
});

result = asp.foo('123');
// 输出结果：arg is 123
// 输出结果：msg is changed to msg111
// 输出结果：foo arg is 123
console.info('result is ' + result);
// 输出结果：result is msg111
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg111


let res = MyClass.bar('456');
// 输出结果：bar arg is 456
console.info('res is ' + res);
// 输出结果：res is data000
console.info('MyClass.data is ' + MyClass.data);
// 输出结果：MyClass.data is data000

util.Aspect.addBefore(MyClass, 'bar', true, (target: Object, arg: string) => {
  console.info('arg is ' + arg);
  let newVal = 'data111';
  Reflect.set(target, 'data', newVal);
  console.info('data is changed to ' + newVal);
});

res = MyClass.bar('456');
// 输出结果：arg is 456
// 输出结果：data is changed to data111
// 输出结果：bar arg is 456
console.info('res is ' + res);
// 输出结果：res is data111
console.info('MyClass.data is ' + MyClass.data);
// 输出结果：MyClass.data is data111
```

## replace

```TypeScript
static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function) : void
```

将指定类的原方法替换为另一个函数，适用于行为替换、兼容性适配、条件执行等需要完全改变方法实现逻辑的场景。replace接口执行完成后，调用指定的类方法时，仅执行替换后的逻辑。最终返回替换函数执行完毕的返回值。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-Aspect-static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function) : void--><!--Device-Aspect-static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function) : void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| targetClass | Object | 是 | 指定的类对象。 |
| methodName | string | 是 | 指定的原方法名，不支持read-only方法。 |
| isStatic | boolean | 是 | 指定的原方法是否为静态方法。true表示静态方法，false表示实例方法。 |
| instead | Function | 是 | 要用来替换原方法的函数。函数有参数时，则第一个参数是this对象（若isStatic为true，则为类对象即targetClass；若isStatic为false，则为调用方法的实例对象），其余参数是原方法的参数。函数也可以无参，无参时不做处理。 |

**示例**

```TypeScript
class MyClass {
  msg: string = 'msg000';
  foo(arg: string): string {
    console.info('foo arg is ' + arg);
    return this.msg;
  }
}

let asp = new MyClass();
let result = asp.foo('123');
// 输出结果：foo arg is 123
console.info('result is ' + result);
// 输出结果：result is msg000
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg000

util.Aspect.replace(MyClass, 'foo', false, (instance: MyClass, arg: string): string => {
  console.info('execute instead');
  console.info('arg is ' + arg);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
  return 'msg222';
});

result = asp.foo('123');
// 输出结果：execute instead
// 输出结果：arg is 123
// 输出结果：msg is changed to msg111
console.info('result is ' + result);
// 输出结果：result is msg222
console.info('asp.msg is ' + asp.msg);
// 输出结果：asp.msg is msg111
```
