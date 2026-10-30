# @Styles：组件重用样式

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @BlYynNe-->
<!--Designer: @VictorS67-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Styles装饰器用于将多条样式设置提炼为一个方法，在组件声明处直接调用，实现自定义样式的定义与复用。适用于多个组件需要共享相同样式、减少重复代码、提升样式一致性维护效率的场景。

开发指南参考：[\@Styles装饰器：定义组件重用样式](../../../ui/state-management/arkts-style.md)。

> **说明：**
>
> - 本装饰器首批接口从API version 8开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 从API版本26.1.0开始，支持传入版本条件参数，声明样式的生效系统版本区间。

## @Styles

const Styles: MethodDecorator & ((version: VersionCondition) => MethodDecorator)

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称 | 类型 | 必填 | 说明 |
| ---- | ---- | ---- | ---- |
| version | [VersionCondition](#versioncondition) | 是 | 版本条件参数，声明样式的生效系统版本区间。以调用形式`@Styles({...})`使用时必须传入，且仅能传入一个。**起始版本：** 26.1.0 |

**示例：**

```ts
@Entry
@Component
struct FancyUse {
  @State heightValue: number = 50;

  // 使用@Styles装饰器定义可复用的样式方法
  @Styles
  fancy() {
    .height(this.heightValue)
    .backgroundColor(Color.Blue)
    .onClick(() => {
      this.heightValue = 100;
    })
  }

  build() {
    Column() {
      Button('change height')
        // 调用@Styles定义的fancy样式方法，应用复用样式
        .fancy()
    }
    .height('100%')
    .width('100%')
  }
}
```

从API版本26.1.0开始，支持传入版本条件参数，声明样式的生效系统版本区间：

```ts
// 仅在系统版本大于等于Api Version 12且小于Api Version 18时生效
@Styles({ minApiVersion: 12, maxApiVersion: 18 })
function globalFancy() {
  .width(150)
  .height(100)
  .backgroundColor(Color.Pink)
}

@Entry
@Component
struct FancyUse {
  build() {
    Column() {
      Text('Fancy')
        .globalFancy()
    }
  }
}
```

## VersionCondition

\@Styles装饰器的版本条件参数，声明样式的生效系统版本区间，作为\@Styles调用形式参数与\@Extend装饰器第二个参数的类型。区间语义为左闭右开`[minApiVersion, maxApiVersion)`：仅传入minApiVersion时，生效区间为大于等于minApiVersion对应的系统版本；仅传入maxApiVersion时，生效区间为小于maxApiVersion对应的系统版本。

**取值形态：**

minApiVersion与maxApiVersion支持以下两种取值形态：

- API版本号：数字或字符串形式，如`12`、`'18'`；从 API版本26.0.0开始仅支持字符串形式，如`'26.0.0'`、`'26.1.0'`；
- 系统版本号字符串：如`'5.0.0'`、`'6.0.0'`、`'26.0.0'`、`'26.1.0'`，不支持带括号形态（如`'5.0.0(12)'`）。

**取值范围：**

合法取值范围从API Version 12开始，对应系统版本号'5.0.0'；从 API版本26.0.0开始仅支持字符串形式，如`'26.0.0'`。

取值没有实际对应存在的API版本号及系统版本号(如`25`、`'26'`、`'6.0.3'`)会产生编译错误。

> **说明：**
>
> - 系统版本号'26.0.0'、'26.0.1'、'26.1.0'仅支持以字符串形式传入（如`'26.1.0'`），不支持整数简写。
> - 版本条件参数至少包含minApiVersion和maxApiVersion其中一个，不支持空对象`{}`；属性值必须为数字字面量或字符串字面量，不支持变量、表达式等；minApiVersion对应的系统版本必须小于maxApiVersion对应的系统版本，否则会产生编译错误。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

**卡片能力：** 从API版本26.1.0开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| ---- | ---- | ---- | ---- | ---- |
| minApiVersion | number \| string | 否 | 是 | 样式生效的系统版本区间下界，包含该版本（左闭）。与maxApiVersion至少需要传入其中一个。 |
| maxApiVersion | number \| string | 否 | 是 | 样式生效的系统版本区间上界，不包含该版本（右开）。与minApiVersion至少需要传入其中一个。 |
