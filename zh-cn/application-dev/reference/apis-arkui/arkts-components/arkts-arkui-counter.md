# Counter

计数器组件，提供增加或减少的计数操作。适用于商品数量选择、参数调整等需要频繁修改数值的场景，帮助用户快速直观地调整数值。
> **说明：** > > - 该组件从API版本26.0.0开始支持WithTheme。

## 子组件

可以包含子组件。

## Counter

```TypeScript
Counter()
```

创建计数器组件。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

## 示例

该示例展示了Counter组件的基本使用方法。点击+、-按钮可以修改计数器的数值。

```TypeScript
// xxx.ets
@Entry
@Component
struct CounterExample {
  @State counterValue1: number = 0;
  @State counterValue2: number = 0;

  build() {
    Column({ space: 50 }) {
      Counter() {
        Text(this.counterValue1.toString())
      }
      .onInc(() => {
        this.counterValue1++;
      })
      .onDec(() => {
        this.counterValue1--;
      })

      Counter() {
        Text(this.counterValue2.toString())
      }
      .onInc(() => {
        this.counterValue2++;
      })
      .onDec(() => {
        this.counterValue2--;
      })
      .enableInc(true)
      .enableDec(false)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```
