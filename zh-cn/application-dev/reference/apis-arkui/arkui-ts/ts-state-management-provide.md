# @Provide

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zany_pink-->
<!--SE: @s10021109-->
<!--TSE: @TerryTsao-->

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>

\@Provide和\@Consume配套使用，用于状态管理V1中，实现跨组件层级的双向同步。@Provide修饰数据源，对其所有后代组件可用。

在ArkTS-Dyn中使用时，开发指南参考：[\@Provide装饰器和\@Consume装饰器：与后代组件双向同步（ArkTS-Dyn）](../../../ui/state-management/arkts-provide-and-consume.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                        | 必填 | 说明                         |
| ------ | ------------------------------------------------- | ---- | ---------------------------- |
| value  | string \| ProvideOptions<br/>ProvideOptions用于设置allowOverride参数，指定是否允许重写。 | 否   | 用于设置别名及是否允许重写。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  @Provide str: string = 'aaa';
  build() {
    Column() {
      Text(`provide: ${this.str}`)
      Child()
    }
  }
}

@Component
struct Child {
  @Consume str: string;
  build() {
    Column() {
      Text(`consume: ${this.str}`)
    }
  }
}
```

