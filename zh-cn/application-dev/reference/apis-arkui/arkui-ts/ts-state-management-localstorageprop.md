# @LocalStorageProp：页面级UI状态存储

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhangboren-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

@LocalStorageProp用于状态管理V1中，与LocalStorage中给定属性建立单向同步关系。

在ArkTS-Dyn中使用时，开发指南参考：[LocalStorage：页面级UI状态存储（ArkTS-Dyn）](../../../ui/state-management/arkts-localstorage.md)。

> **说明：**
>
> 从API version 9开始，支持该装饰器。

## @LocalStorageProp

const LocalStorageProp: (value: string) => PropertyDecorator

**卡片能力（仅ArkTS-Dyn）：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                         |
| ------ | ------ | ---- | ---------------------------- |
| value  | string | 是   | 用于标识LocalStorage的属性。 |

**示例：**

```ts
// 创建LocalStorage的初始数据，键为'PropA'，值为47
let para: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(para);

// 使用@Entry装饰器标记入口组件，并传入LocalStorage实例
@Entry(storage)
@Component
struct Parent {
  // 使用@LocalStorageProp装饰器与LocalStorage中'PropA'属性建立单向绑定
  // 本地修改不会同步回LocalStorage
  @LocalStorageProp('PropA') propA: number = 1;

  build() {
    Column() {
      Button(`Parent from LocalStorage ${this.propA}`)
        // 设置点击事件，点击后propA值加1，但不会同步回LocalStorage
        .onClick((e: ClickEvent) => {
          this.propA += 1;
        })
      Child()
    }
  }
}

@Component
struct Child {
  // 使用@LocalStorageProp装饰器与LocalStorage中'PropA'属性建立单向绑定
  // 子组件的propB会从LocalStorage读取'PropA'的值，但本地修改不会同步回去
  @LocalStorageProp('PropA') propB: number = 2;

  build() {
    Column() {
      Text(`Child from LocalStorage ${this.propB}`)
    }
  }
}
```

