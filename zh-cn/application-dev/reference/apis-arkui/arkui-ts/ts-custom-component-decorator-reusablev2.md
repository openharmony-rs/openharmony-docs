# @ReusableV2：组件复用V2

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰\@ComponentV2装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@ReusableV2装饰器：组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## @ReusableV2

const ReusableV2: ClassDecorator & ((options: ReusableOptions) => ClassDecorator)

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型     | 必填   | 说明                                    |
| ----------- | ------ | ---- | --------------------------------------- |
| options  | [ReusableOptions](./ts-custom-component-parameter.md#reusableoptions) | 否    | 可复用自定义组件的参数，用于配置内存优化策略，缺省时默认无内存优化策略。<br>**起始版本：** 26.0.0               |

**示例：**

```ts
@ObservedV2
class Info {
  @Trace age: number;
  constructor(age: number) {
    this.age = age;
  }
}
@Entry
@ComponentV2
struct Index {
  // 使用@Local控制子组件的显示与隐藏
  @Local condition: boolean = true; 
  build() {
    Column() {
      Button('Reuse')
        .onClick(() => {
          // 点击按钮切换子组件的显示状态
          this.condition = !this.condition; 
        })
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
// 使用@ReusableV2装饰器标记可复用组件，配合@ComponentV2使用
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  noDecoInfo: Info = new Info(30);
  @Monitor('noDecoInfo.age')
  onAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
  // 组件被回收时的回调
  aboutToRecycle() {
    this.noDecoInfo.age = 25;
  }
  // 组件被复用时的回调
  aboutToReuse() {
    this.noDecoInfo.age = 35;
  }
  build() {
    Column() {
      Text(`noDecoInfo.age: ${this.noDecoInfo.age}`)
        .onClick(() => {
          // 能够触发刷新但是不会被重置
          this.noDecoInfo.age++;
        }) 
    }
  }
}
```
