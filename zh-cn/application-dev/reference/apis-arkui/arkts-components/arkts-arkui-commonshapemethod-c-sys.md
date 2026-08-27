# CommonShapeMethod

CommonShapeMethod@extends CommonMethod&lt;T&gt;

**继承/实现关系：** CommonShapeMethod extends CommonMethod<T>

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor()
```

constructor.

**起始版本：** 9

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**示例**

```TypeScript
@Builder
function myBuilder(value: string, size: number) {
  Text(value)
    .fontSize(size)
}

// 使用WrappedBuilder封装myBuilder
let builderVar: WrappedBuilder<[string, number]> = new WrappedBuilder<[string, number]>(myBuilder);
```
