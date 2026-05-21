# ArkTS方舟编程语言Changelog

## cl.arkcompiler.1 async函数类型判定修复

**访问级别**

其他

**变更原因**

在类中getter/setter之后定义的async函数，实际被初始化的类型为普通函数，导致无法在运行时正确地判定函数类型。

**变更影响**

1. 由于async的行为并不依赖函数类型，而是通过特定的字节码实现的，此变更前后async的语义均无问题。
2. 该变更会修复在运行时对async函数进行的类型判定，具体行为变化如下：

   变更前：

   在类中getter/setter（@State变量经过编译也会在TS中生成对应的getter/setter）之后定义的async函数：

   1. new util.types().isAsyncFunction 判断为false。
   2. (async () => {}).constructor.name 的结果为："Function"。
   3. worker通过callGlobalCallObjectMethod调用返回的错误码及错误信息为："10200006 An exception occurred during serialization"。

   变更后：

   在类中getter/setter（@State变量经过编译也会在TS中生成对应的getter/setter）之后定义的async函数：

   1. new util.types().isAsyncFunction 判断为true。
   2. (async () => {}).constructor.name 的结果为："AsyncFunction"。
   3. worker通过callGlobalCallObjectMethod调用返回的错误码及错误信息为："10200020 The method to be called is not callable or is an async method or a generator"。

具体的代码示例如下：
```typescript
import { util } from '@kit.ArkTS';

class Model {
  // 在类中getter setter之前定义的async function，类型正确。
  async testFunction1() {}
  get id() { return 1 }
  set id(id) {}
  // 在类中getter setter之后定义的async function，类型不正确，应当为AsyncFunction，实际为普通Function。
  async testFunction2() {}
}

@Entry
@Component
struct Index {
  // 在类中getter setter之前定义的async function，类型正确。
  async testFunction1() {}
  // 经过编译也会生成getter setter
  @State message: string = 'Hello World';
  // 在类中getter setter之后定义的async function，类型不正确，应当为AsyncFunction，实际为普通Function。
  async testFunction2() {}
  build() {
    RelativeContainer() {
      Text(this.message)
        .onClick(() => {
          let model: Model = new Model();
          let type = new util.types();
          
          // 输出true，行为是正确的，该变更无影响。
          type.isAsyncFunction(this.testFunction1);
          type.isAsyncFunction(model.testFunction1);
          // 输出AsyncFunction，行为是正确的，该变更无影响。
          console.info(this.testFunction1.constructor.name);
          console.info(model.testFunction1.constructor.name);
          
          // 输出false，变更后输出true。
          type.isAsyncFunction(this.testFunction2);
          type.isAsyncFunction(model.testFunction2);
          // 输出Function，变更后输出AsyncFunction。
          console.info(this.testFunction2.constructor.name);
          console.info(model.testFunction2.constructor.name);
        })
    }
  }
}
```

**起始 API Level**

API 8

**变更发生版本**

从OpenHarmony SDK 7.0.0.17开始。

**变更的接口/组件**

1. new util.types().isAsyncFunction
2. Function.constructor.name

**适配指导**

默认行为变更，开发者需排查new util.types().isAsyncFunction和Function.constructor.name的调用点，审视接口输出结果的变化是否对自身相关业务代码逻辑产生影响，若有影响需根据自身业务代码进行相应的适配。