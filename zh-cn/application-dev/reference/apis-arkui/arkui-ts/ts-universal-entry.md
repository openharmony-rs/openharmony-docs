# \@Entry：页面入口

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

\@Entry装饰的自定义组件将作为UI页面的入口，被框架识别为页面的根组件，适用于构建独立UI页面的场景。

> **说明：**
>
> 本模块首批接口从API version 7开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。

## \@Entry

在单个UI页面中，仅允许存在一个由\@Entry装饰的自定义组件作为页面的入口。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
// @Entry装饰的自定义组件作为UI页面的入口
@Entry
@Component
struct Index {
  build() {
    Text('@Entry Test')
  }
}
```

## EntryOptions<sup>10+</sup>

页面入口配置选项，用于在\@Entry装饰页面时配置路由名称和状态存储等相关参数。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                         | 类型                                                         | 只读 | 可选 | 说明                                                         |
| ------------------------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| routeName                      | string                                                       | 否  | 是 | 表示作为命名路由页面的名称。当需要通过命名路由方式跳转到此页面时，需设置此参数作为路由名称。不传入时，该页面不会注册为命名路由页面，无法通过命名路由方式跳转访问，仅作为默认入口页面加载。<br>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| storage                        | [LocalStorage](../../../ui/state-management/arkts-localstorage.md) | 否 | 是  | 页面级的UI状态存储。当需要在页面外部预先创建并管理UI状态、或需要将已有的LocalStorage实例绑定到此页面以实现状态共享时，传入此参数。当未传入时，框架会创建一个新的LocalStorage实例作为默认值。<br>**卡片能力：** 从API version 10开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。 |
| useSharedStorage<sup>12+</sup> | boolean                                                      | 否  | 是 | 是否使用[loadContent](../arkts-apis-window-WindowStage.md#loadcontent9)传入的LocalStorage实例对象。默认值false。true：使用共享的LocalStorage实例对象（前提条件：需确保loadContent接口已传入LocalStorage实例）。false：不使用共享的LocalStorage实例对象。该参数与storage参数的联合使用行为请参见相关接口说明。<br>**卡片能力：** 从API version 12开始，该接口支持在ArkTS卡片中使用。<br>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。 |

**示例：**

```ts
// 设置路由页面名字为myPage
@Entry({ routeName: 'myPage' })
@Component
struct Index {
  build() {
    Text('Index')
  }
}
```

