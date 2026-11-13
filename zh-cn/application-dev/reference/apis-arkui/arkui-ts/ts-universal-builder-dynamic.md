# @Builder装饰器：自定义构建函数

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Builder装饰的函数也称为“自定义构建函数”，用于封装可复用的UI构建逻辑，可在自定义组件中多次调用，从而减少代码重复、提升UI构建的可维护性，适用于需要复用相同UI结构的场景。

开发指南参考：[@Builder装饰器：自定义构建函数](../../../ui/state-management/arkts-builder.md)。

> **说明：**
>
> - 该装饰器从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 从API版本26.1.0开始，支持传入[BuilderDecoratorConfig](#builderdecoratorconfig)配置项，声明占位构建函数。

## @Builder

const Builder: MethodDecorator & BuilderMethodDecorator

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**示例：**

```ts
@Entry
@Component
struct BuilderDemo {
  // @Builder装饰此函数，使其成为自定义构建函数，用于配置并构建Text组件
  @Builder
  showTextBuilder() {
    Text('Hello World')
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  @Builder
  showTextValueBuilder(param: string) {
    Text(param)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }

  build() {
    Column() {
      // 无参数
      this.showTextBuilder()
      // 有参数
      this.showTextValueBuilder('Hello @Builder')
    }
  }
}
```

## BuilderMethodDecorator

type BuilderMethodDecorator = (value: BuilderDecoratorConfig) => MethodDecorator

\@Builder装饰器传入配置项时的实际类型。

**起始版本：** 26.1.0

**卡片能力：** 从API版本26.1.0开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型     | 必填 | 说明                                                         |
| ------ | -------- | ---- | ------------------------------------------------------------ |
| value  | [BuilderDecoratorConfig](#builderdecoratorconfig) | 是   | \@Builder装饰器的配置项。                                     |

**返回值：**

| 类型            | 说明                                 |
| --------------- | ------------------------------------ |
| MethodDecorator | 方法装饰器，开发者无需关注该返回值。 |

## BuilderDecoratorConfig

\@Builder装饰器的配置选项。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.1.0开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称          | 类型    | 只读 | 可选 | 说明                                                         |
| ------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| isPlaceholder | boolean | 否   | 否   | 是否将\@Builder函数声明为占位构建函数。true：启用占位能力。此时该函数必须为全局且无参数的函数，内部仅执行不依赖状态变量的静态渲染，且不能注册手势或业务回调。通过[placeholderRegister](../../../ui/state-management/arkts-builder.md#占位构建函数)的register方法注册后，供可滚动组件的[scrollPlaceholder](../../../ui/state-management/arkts-builder.md#占位构建函数)属性使用。false：不启用占位能力，等价于未传入配置项的\@Builder。默认值为false。 |

**示例：**

下例声明占位构建函数，经placeholderRegister注册后由List的scrollPlaceholder属性使用。

```ts
import { PlaceholderOptions } from '@kit.ArkUI';

// 占位构建函数须为全局、无参，且仅执行不依赖状态变量的静态渲染
@Builder({ isPlaceholder: true })
function ItemPlaceholder() {
  Column() {
    Text('加载中...')
      .fontSize(16)
      .fontColor(0x999999)
  }
  .width('100%')
  .height(100)
  .justifyContent(FlexAlign.Center)
}

@Entry
@ComponentV2
struct BuilderPlaceholderList {
  @Local data: number[] = [];

  aboutToAppear(): void {
    // 通过UIContext获取占位注册表，占位构建函数经wrapBuilder包装后注册，供scrollPlaceholder按id引用
    this.getUIContext().getPlaceholderRegister()
      .register('itemPlaceholder', wrapBuilder(ItemPlaceholder));
    const list: number[] = [];
    for (let i = 0; i < 10000; i++) {
      list.push(i);
    }
    this.data = list;
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        Repeat<number>(this.data)
          .each((repeatItem: RepeatItem<number>) => {
            ListItem() {
              Text(repeatItem.item.toString())
                .fontSize(16)
                .width('100%')
                .height(100)
                .textAlign(TextAlign.Center)
            }
          })
      }
      .width('90%')
      .height(300)
      // id对应已注册的占位构建函数，size为占位的建议尺寸，与真实列表项高度一致，减小替换时的视觉跳动
      .scrollPlaceholder((index: number): PlaceholderOptions | undefined => {
        return { id: 'itemPlaceholder', size: { height: 100 } };
      })
    }
    .width('100%')
    .padding({ top: 10 })
    .backgroundColor('#FFDCDCDC')
  }
}
```
