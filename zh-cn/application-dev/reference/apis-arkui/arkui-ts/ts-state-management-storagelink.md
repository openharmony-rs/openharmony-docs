# @StorageLink：AppStorage双向数据同步

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@StorageLink用于状态管理V1中，与AppStorage中对应的属性建立双向数据同步。

开发指南参考：[AppStorage：应用全局的UI状态存储](../../../ui/state-management/arkts-appstorage.md)。

> **说明：**
>
> 从API version 7开始，支持该装饰器。

## @StorageLink

const StorageLink: (value: string) => PropertyDecorator

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| value  | string | 是   | AppStorage中的属性键值，用于建立与对应属性值的双向数据同步。 |

**示例：**

```ts
// 创建AppStorage的初始数据，键为'LinkA'，值为47
AppStorage.setOrCreate('LinkA', 47);
// 创建AppStorage的初始数据，键为'LinkB'，值为undefined
AppStorage.setOrCreate('LinkB', undefined);

@Entry
@Component
struct StorageLinkComponent {
  // 使用@StorageLink装饰器与AppStorage中'LinkA'对应属性建立双向数据同步
  @StorageLink('LinkA') linkA: number | null = null;
  // 使用@StorageLink装饰器与AppStorage中'LinkB'对应属性建立双向数据同步
  @StorageLink('LinkB') linkB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StorageLink接口初始化，@StorageLink取值')
      Text(`${this.linkA}`)
        .fontSize(20)
        .onClick(() => {
          // 点击切换linkA的值，变更会同步到AppStorage
          this.linkA = this.linkA ? null : 1;
        })
      Text(`${this.linkB}`)
        .fontSize(20)
        .onClick(() => {
          // 点击切换linkB的值，变更会同步到AppStorage
          this.linkB = this.linkB ? undefined : 1;
        })
    }
  }
}
```

