# ArkUI子系统Changelog

## cl.arkui.1 新增状态管理V1校验报错
**访问级别**

其他

**变更原因**

自定义组件struct中使用状态管理V1的装饰器装饰Function类型的变量时，会出现运行时crash异常，提示开发者不支持装饰Function类型。为提升开发者运行时代码的稳定性，新增编译报错：如果自定义组件struct中使用状态管理V1的装饰器装饰Function类型的变量，则编译报错并中断编译。

**变更影响**

此变更涉及应用适配

变更前：自定义组件struct中使用状态管理V1装饰器装饰Function类型的变量时，编译能通过，但运行时会出现crash，并提示不支持该装饰方式。

变更后：新增编译报错：如果自定义组件struct中使用状态管理V1的装饰器装饰Function类型的变量，则编译报错并中断编译，编译报错：The V1 decorator 'xxx' cannot be applied to a Function-type variable 'yyy'。

**起始 API Level**

不涉及API

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

ArkUI状态管理V1装饰器：

@State, @Prop, @Link, @Provide, @Consume, @StorageLink, @LocalStorageLink, @StorageProp, @LocalStorageProp, @ObjectLink

**适配指导**

当被状态管理V1的装饰器装饰的变量类型为Function类型（如下示例为Function类型）时，可以将对应的状态管理V1的装饰器移除，使用常规变量声明修复编译与运行时异常。

编译报错示例：

```ts
@Entry
@Component
struct Index {
  @State func1: Function = () => {}; // 编译报错
  @State func2: (input: number) => void = (input: number) => {}; // 编译报错

  build() {
    // 业务代码
  }
}
```

将`@State`移除后可修复编译报错：

```ts
@Entry
@Component
struct Index {
  func1: Function = () => {};
  func2: (input: number) => void = (input: number) => {};

  build() {
    // 业务代码
  }
}
```