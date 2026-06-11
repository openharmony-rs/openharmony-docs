# @LocalStorageLink：页面级UI状态存储

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@LocalStorageLink用于状态管理V1中，与LocalStorage中给定属性建立双向同步关系。

在ArkTS-Dyn中使用时，开发指南参考：[LocalStorage：页面级UI状态存储（ArkTS-Dyn）](../../../ui/state-management/arkts-localstorage.md)。

> **说明：**
>
> 从API version 9开始，支持该装饰器。

## @LocalStorageLink

const LocalStorageLink: (value: string) => PropertyDecorator

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                         |
| ------ | ------ | ---- | ---------------------------- |
| value  | string | 是   | 用于标识LocalStorage的属性。 |

**示例：**

```ts
// 创建LocalStorage的初始数据，键为'LinkA'，值为47
let para: Record<string, number> = { 'LinkA': 47 };
let storage: LocalStorage = new LocalStorage(para);

// 使用@Entry装饰器标记入口组件，并传入LocalStorage实例
@Entry(storage)
@Component
struct Parent {
  // 使用@LocalStorageLink装饰器与LocalStorage中'LinkA'属性建立双向绑定
  @LocalStorageLink('LinkA') linkA: number = 1;

  build() {
    Column() {
      Text(`incr @LocalStorageLink variable`)
        // 设置点击事件，点击后linkA值加1，变更会同步到LocalStorage
        .onClick(() => {
          this.linkA += 1;
        })
      // 显示当前@LocalStorageLink绑定的变量值
      Text(`@LocalStorageLink: ${this.linkA}`)
    }
  }
}
```

