# @Event：规范组件输出

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Event装饰回调方法，用于状态管理V2中，作为自定义组件的输出。

开发指南参考：[@Event：规范组件输出](../../../ui/state-management/arkts-new-event.md)。

> **说明：**
>
> 从API version 12开始，支持该装饰器。

## @Event

const Event: PropertyDecorator

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API version 23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@ComponentV2
struct Index {
  @Local name: string = 'Tom';

  build() {
    Column() {
      Child({
        name: this.name,
        changeFactory: (type: number) => {
          // @Event装饰的函数，在实现中修改父组件中的状态变量
          if (type == 1) {
            this.name = 'Tom';
          } else if (type == 2) {
            this.name = 'Jerry';
          }
        }
      })
    }
  }
}

@ComponentV2
struct Child {
  @Param name: string = '';
  // @Event装饰函数，用于向父组件传递消息
  @Event changeFactory: (x: number) => void = (x: number) => {};

  build() {
    Column() {
      Text(`name: ${this.name}`)
      Button('change to Tom')
        .onClick(() => {
          this.changeFactory(1);
        })
      Button('change to Jerry')
        .onClick(() => {
          this.changeFactory(2);
        })
    }
  }
}
```

