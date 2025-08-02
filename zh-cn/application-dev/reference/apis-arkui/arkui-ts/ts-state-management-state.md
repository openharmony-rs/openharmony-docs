# @State

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>

@State用于状态管理V1中，将自定义组件内的普通变量转变为状态变量，管理组件内UI刷新。

在动态语言上下文中使用时，开发指南参考：[@State装饰器：组件内状态（ArkTS-DT）](../../../ui/state-management/arkts-state.md)。

**卡片能力：** 从API version 9开始，该接口支持在ArkTS卡片中使用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@Component
struct StateExample {
  @State count: number = 0;
  build() {
    Column() {
      Text(`${this.count}`)
    }
  }
}
```
