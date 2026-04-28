# @ReusableV2：组件复用V2

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰\@ComponentV2装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@ReusableV2装饰器：组件复用](../../../ui/state-management-static/arkts-static-new-reusableV2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Sta。
>
> - 本装饰器首批接口从API version 23开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
'use static'
import { Entry, ComponentV2, Local, Column, Button, ReusableV2, Text } from '@kit.ArkUI';
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('回收/复用')
        .onClick(() => {
          this.condition = !this.condition;
        }) // 点击切换回收/复用状态
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Local message: string = 'Hello World';
  aboutToRecycle() {
    console.info('ReusableV2Component aboutToRecycle'); // 回收时被调用
  }
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse'); // 复用时被调用
  }
  build() {
    Column() {
      Text(this.message)
    }
  }
}
```