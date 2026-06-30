# @StorageProp：AppStorage单向数据同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@StorageProp用于状态管理V1中，与AppStorage中对应的属性建立单向数据同步。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @StorageProp

const StorageProp: (value: string) => PropertyDecorator

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| value  | string | 是   | AppStorage中的属性键值，用于建立与对应属性值的单向数据同步。 |

**示例：**

```ts
// 创建AppStorage的初始数据，键为'PropA'，值为47
AppStorage.setOrCreate('PropA', 47);
// 创建AppStorage的初始数据，键为'PropB'，值为undefined
AppStorage.setOrCreate('PropB', undefined);

@Entry
@Component
struct StoragePropComponent {
  // 使用@StorageProp装饰器与AppStorage中'PropA'对应属性建立单向数据同步
  // AppStorage变化会同步到组件，但组件本地修改不会同步回AppStorage
  @StorageProp('PropA') propA: number | null = null;
  // 使用@StorageProp装饰器与AppStorage中'PropB'对应属性建立单向数据同步
  @StorageProp('PropB') propB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StorageProp接口初始化，@StorageProp取值')
      Text(`${this.propA}`)
        .fontSize(20)
        .onClick(() => {
          // 点击切换propA的值，该变更不会同步到AppStorage
          this.propA = this.propA ? null : 1;
        })
      Text(`${this.propB}`)
        .fontSize(20)
        .onClick(() => {
          // 点击切换propB的值，该变更不会同步到AppStorage
          this.propB = this.propB ? undefined : 1;
        })
    }
  }
}
```

