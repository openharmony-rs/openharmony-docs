# @ReusableV2：组件复用V2

为了降低反复创建销毁自定义组件带来的性能开销，开发者可以使用\@ReusableV2装饰\@ComponentV2装饰的自定义组件，达成组件复用的效果。开发指南参考：[\@ReusableV2装饰器：组件复用](../../../ui/state-management/arkts-new-reusableV2.md)。

> **说明：**
>
> - 本装饰器仅适用于ArkTS-Dyn。
>
> - 本装饰器首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

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
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('Reuse')
        .onClick(() => {
          this.condition = !this.condition;
        })
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  noDecoInfo: Info = new Info(30); // 未加装饰器，被视作常量
  @Monitor('noDecoInfo.age')
  onAgeChange(monitor: IMonitor) {
    console.info(`age change from ${monitor.value()?.before} to ${monitor.value()?.now}`);
  }
  aboutToRecycle() {
    this.noDecoInfo.age = 25;
  }
  aboutToReuse() {
    this.noDecoInfo.age = 35;
  }
  build() {
    Column() {
      Text(`noDecoInfo.age: ${this.noDecoInfo.age}`)
        .onClick(() => {
          this.noDecoInfo.age++;
        }) // 能够触发刷新但是不会被重置
    }
  }
}
```
