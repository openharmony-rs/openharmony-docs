# @LocalStorageProp

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 9开始，支持该装饰器。

@LocalStorageProp用于状态管理V1中，与LocalStorage中给定属性建立单向同步关系。

在ArkTS-Dyn中使用时，开发指南参考：[LocalStorage：页面级UI状态存储（ArkTS-Dyn）](../../../ui/state-management/arkts-localstorage.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型   | 必填 | 说明                         |
| ------ | ------ | ---- | ---------------------------- |
| value  | string | 是   | 用于标识LocalStorage的属性。 |

**示例：**

```ts
let para: Record<string, number> = { 'PropA': 47 };
let storage: LocalStorage = new LocalStorage(para);

@Entry(storage)
@Component
struct Parent {
  @LocalStorageProp('PropA') propA: number = 1;

  build() {
    Column() {
      Button(`Parent from LocalStorage ${this.propA}`)
        .onClick((e: ClickEvent) => {
          this.propA += 1;
        })
      Child()
    }
  }
}

@Component
struct Child {
  @LocalStorageProp('PropA') propB: number = 2;

  build() {
    Column() {
      Text(`Child from LocalStorage ${this.propB}`)
    }
  }
}
```

