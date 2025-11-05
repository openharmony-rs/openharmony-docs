# @Watch

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>

@Watch装饰器用于状态管理V1中，监听状态变量的变化。

在ArkTS-Dyn中使用时，开发指南参考：[@Watch装饰器：状态变量更改通知（ArkTS-Dyn）](../../../ui/state-management/arkts-watch.md)。

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
  @State @Watch('onChange') count: number = 0;
  @State total: number = 0;

  onChange(propertyName: string): void {
    this.total += this.count;
  }

  build() {
    Column() {
      Text(`Total: ${this.total}`)
      Button('change')
        .onClick(() => {
          this.count++;
        })
    }
  }
}
```

