# @Watch：状态变量更改通知

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@Watch装饰器用于状态管理V1中，监听状态变量的变化。开发指南参考：[@Watch装饰器：状态变量更改通知](../../../ui/state-management/arkts-watch.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @Watch

const Watch: (value: string) => PropertyDecorator

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | ---------------------------------------- |
| value  | string | 是   | 用于监听的回调函数名，内容由开发者指定。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  // 使用@State声明状态变量count，并使用@Watch装饰器监听其变化
  // 当count值变化时，自动调用名为'onChange'的回调函数
  @State @Watch('onChange') count: number = 0;
  @State total: number = 0;

  // @Watch监听的回调函数，参数为发生变化的属性名
  onChange(propertyName: string): void {
    this.total += this.count;
  }

  build() {
    Column() {
      Text(`Total: ${this.total}`)
      Button('change')
        // 设置点击事件，点击后count值加1，触发@Watch回调
        .onClick(() => {
          this.count++;
        })
    }
  }
}
```

