# @Reusable: 组件复用

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@Reusable装饰\@Component装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@Reusable装饰器：组件复用](../../../ui/state-management/arkts-reusable.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
class Message {
  value: string | undefined;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State switch: boolean = true;

  build() {
    Column() {
      Button('Hello')
        .fontSize(30)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.switch = !this.switch;
        })
      if (this.switch) {
        // 如果只有一个复用的组件，可以不用设置reuseId。
        Child({ message: new Message('Child') })
          .reuseId('Child')
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');

  aboutToReuse(params: Record<string, ESObject>) {
    console.info('Recycle====Child==');
    this.message = params.message as Message;
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(30)
    }
    .borderWidth(1)
    .height(100)
  }
}
```
