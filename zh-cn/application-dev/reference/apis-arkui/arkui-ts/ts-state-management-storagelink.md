# @StorageLink

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 7开始，支持该装饰器。

@StorageLink用于状态管理V1中，与AppStorage中对应的属性建立双向数据同步。

在ArkTS-Dyn中使用时，开发指南参考：[AppStorage：应用全局的UI状态存储（ArkTS-Dyn）](../../../ui/state-management/arkts-appstorage.md)。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| value  | string | 是   | 用于标识AppStorage的属性。 |

**示例：**

```ts
@Entry
@Component
struct StorageLinkComponent {
  @StorageLink('LinkA') linkA: number | null = null;
  @StorageLink('LinkB') linkB: number | undefined = undefined;

  build() {
    Column() {
      Text('@StorageLink接口初始化，@StorageLink取值')
      Text(this.linkA + '').fontSize(20).onClick(() => {
        this.linkA ? this.linkA = null : this.linkA = 1;
      })
      Text(this.linkB + '').fontSize(20).onClick(() => {
        this.linkB ? this.linkB = undefined : this.linkB = 1;
      })
    }
  }
}
```

