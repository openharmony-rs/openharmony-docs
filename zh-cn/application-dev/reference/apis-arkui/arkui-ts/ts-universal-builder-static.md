# @Builder装饰器：自定义构建函数

\@Builder装饰的函数也称为“自定义构建函数”。开发指南见[\@Builder装饰器：自定义构建函数](../../../ui/state-management/arkts-builder.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 该装饰器从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @Builder

@interface Builder

\@Builder装饰器的配置接口，声明\@Builder装饰器的配置项（如占位构建函数标记isPlaceholder）。

**示例：**

```ts
'use static'

import { Entry, Component, Column, Text, Builder, FontWeight } from '@kit.ArkUI';

@Entry
@Component
struct BuilderDemo {
  // @Builder装饰此函数，使其能以链式调用的方式配置并构建Text组件
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

### 属性

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 26.1.0

| 名称          | 类型    | 只读 | 可选 | 说明                                                         |
| ------------- | ------- | ---- | ---- | ------------------------------------------------------------ |
| isPlaceholder | boolean | 否   | 否   | 是否将\@Builder函数声明为占位构建函数。true：启用占位能力。此时该函数必须为全局且无参数的函数，内部仅执行不依赖状态变量的静态渲染，且不能注册手势或业务回调。通过[placeholderRegister](../arkts-apis-placeholderregister.md)的[register](../arkts-apis-placeholderregister.md#register)方法注册后，供可滚动组件的[scrollPlaceholder](./ts-container-list.md#scrollplaceholderarkts-sta)属性使用。false：不启用占位能力，等价于未传入配置项的\@Builder。默认值为false。 |

**示例：**

下例声明占位构建函数，经placeholderRegister注册后由List的scrollPlaceholder属性使用。

ArkTS-Sta示例：

```ts
import { Column, Text, Builder, FlexAlign } from '@kit.ArkUI';

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
```

完整注册与使用流程（wrapBuilder包装、getPlaceholderRegister注册、scrollPlaceholder按id引用）参考[@ohos.arkui.placeholderRegister (滚动占位注册)](../arkts-apis-placeholderregister.md)的[示例1（注册滚动占位模板并设置滚动占位）](../arkts-apis-placeholderregister.md#示例1注册滚动占位模板并设置滚动占位)。
