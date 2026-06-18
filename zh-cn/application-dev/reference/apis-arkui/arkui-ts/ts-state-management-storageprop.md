# @StorageProp：应用全局的UI状态存储

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@StorageProp用于状态管理V1中，与AppStorage中对应的属性建立单向数据同步。

在ArkTS-Dyn中使用时，开发指南参考：[AppStorage：应用全局的UI状态存储（ArkTS-Dyn）](../../../ui/state-management/arkts-appstorage.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @StorageProp

const StorageProp: (value: string) => PropertyDecorator

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| value  | string | 是   | 用于标识AppStorage的属性。 |

**示例：**

```ts
@Entry
@Component
struct StoragePropComponent {
  // 使用@StorageProp装饰器与AppStorage中'PropA'属性建立单向绑定
  // AppStorage变化会同步到组件，但组件本地修改不会同步回AppStorage
  @StorageProp('PropA') propA: number | null = null;
  @StorageProp('PropB') propB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StorageProp接口初始化，@StorageProp取值')
      // 显示propA的值，点击时在null和1之间切换（本地修改不会同步回AppStorage）
      Text(`${this.propA}`)
        .fontSize(20)
        .onClick(() => {
          this.propA = this.propA ? null : 1;
        })
      Text(`${this.propB}`)
        .fontSize(20)
        .onClick(() => {
          this.propB = this.propB ? undefined : 1;
        })
    }
  }
}
```

