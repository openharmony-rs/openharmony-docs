# Aspect

Provides APIs that support Aspect Oriented Programming (AOP). These APIs can be used to perform instrumentation or replacement on class methods.

**Since:** 11

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## addAfter

```TypeScript
static addAfter(targetClass: Object, methodName: string, isStatic: boolean, after: Function): void
```

Inserts a function after a method of a class object. The final return value is the return value of the function inserted.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetClass | Object | Yes | Target class object. |
| methodName | string | Yes | Name of the method. Read-only methods are not supported. |
| isStatic | boolean | Yes | Whether the method is a static method. The value **true** means a static method, and **false** means an instance method. |
| after | Function | Yes | Function to insert. If the function carries parameters, then the first parameter is the **this** object, which is the target class object (specified by **targetClass**) if **isStatic** is **true** or the instance object of the method if **isStatic** is **false**; the second parameter is the return value of the original method (**undefined** if the original method does not have a return value); other parameters are the parameters carried by the original method. If the function does not carry any parameter, no processing is performed. |

**Examples**

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
// Output: foo arg is 123
console.info('result is ' + result);
// Output: result is msg000
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg000

util.Aspect.addAfter(MyClass, 'foo', false, (instance: MyClass, ret: string, arg: string): string => {
  console.info('arg is ' + arg);
  console.info('ret is ' + ret);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
  return 'msg222';
});

result = asp.foo('123');
// Output: foo arg is 123
// Output: arg is 123
// Output: ret is msg000
// Output: msg is changed to msg111
console.info('result is ' + result);
// Output: result is msg222
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg111

// Examples of addBefore() and addAfter()
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
// Output: execute before
// Output: execute foo with arg hello
// Output: execute after
```

## addBefore

```TypeScript
static addBefore(targetClass: Object, methodName: string, isStatic: boolean, before: Function): void
```

Inserts a function before a method of a class object. The inserted function is executed in prior to the original method of the class object.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetClass | Object | Yes | Target class object. |
| methodName | string | Yes | Name of the method. Read-only methods are not supported. |
| isStatic | boolean | Yes | Whether the method is a static method. The value **true** means a static method, and **false** means an instance method. |
| before | Function | Yes | Function to insert. If the function carries parameters, then the first parameter is the **this** object, which is the target class object (specified by **targetClass**) if **isStatic** is **true** or the instance object of the method if **isStatic** is **false**; other parameters are the parameters carried in the original method. If the function does not carry any parameter, no processing is performed. |

**Examples**

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
// Output: foo arg is 123
console.info('result is ' + result);
// Output: result is msg000
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg000

util.Aspect.addBefore(MyClass, 'foo', false, (instance: MyClass, arg: string) => {
  console.info('arg is ' + arg);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
});

result = asp.foo('123');
// Output: arg is 123
// Output: msg is changed to msg111
// Output: foo arg is 123
console.info('result is ' + result);
// Output: result is msg111
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg111


let res = MyClass.bar('456');
// Output: bar arg is 456
console.info('res is ' + res);
// Output: res is data000
console.info('MyClass.data is ' + MyClass.data);
// Output: MyClass.data is data000

util.Aspect.addBefore(MyClass, 'bar', true, (target: Object, arg: string) => {
  console.info('arg is ' + arg);
  let newVal = 'data111';
  Reflect.set(target, 'data', newVal);
  console.info('data is changed to ' + newVal);
});

res = MyClass.bar('456');
// Output: arg is 456
// Output: data is changed to data111
// Output: bar arg is 456
console.info('res is ' + res);
//Output: res is data111
console.info('MyClass.data is ' + MyClass.data);
// Output: MyClass.data is data111
```

## replace

```TypeScript
static replace(targetClass: Object, methodName: string, isStatic: boolean, instead: Function) : void
```

Replaces a method of a class object with another function. After the replacement, only the new function logic is executed. The final return value is the return value of the new function.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetClass | Object | Yes | Target class object. |
| methodName | string | Yes | Name of the method. Read-only methods are not supported. |
| isStatic | boolean | Yes | Whether the method is a static method. The value **true** means a static method, and **false** means an instance method. |
| instead | Function | Yes | Function to be used replacement. If the function carries parameters, then the first parameter is the **this** object, which is the target class object (specified by **targetClass**) if **isStatic** is **true** or the instance object of the method if **isStatic** is **false**; other parameters are the parameters carried in the original method. If the function does not carry any parameter, no processing is performed. |

**Examples**

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
// Output: foo arg is 123
console.info('result is ' + result);
// Output: result is msg000
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg000

util.Aspect.replace(MyClass, 'foo', false, (instance: MyClass, arg: string): string => {
  console.info('execute instead');
  console.info('arg is ' + arg);
  instance.msg = 'msg111';
  console.info('msg is changed to ' + instance.msg);
  return 'msg222';
});

result = asp.foo('123');
// Output: execute instead
// Output: arg is 123
// Output: msg is changed to msg111
console.info('result is ' + result);
// Output: result is msg222
console.info('asp.msg is ' + asp.msg);
// Output: asp.msg is msg111
```
