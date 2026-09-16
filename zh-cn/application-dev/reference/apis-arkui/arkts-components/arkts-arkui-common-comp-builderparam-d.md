# @BuilderParam

```TypeScript
declare const BuilderParam: PropertyDecorator
```

\@BuilderParam用于装饰指向[@Builder](arkts-arkui-common-comp-builder-d.md#builder)函数的变量，使自定义组件能够接收外部传入的\@Builder函数，实现UI内容的自定义渲染。适用于需要将父组件的UI构建逻辑传递给子组件、实现组件内容动态定制的场景。

开发指南参考：[@BuilderParam装饰器：引用@Builder函数](../../../ui/state-management/arkts-builderparam.md)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
