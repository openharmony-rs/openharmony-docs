# @State

@State用于将自定义组件内的普通变量转变为状态变量，管理组件内UI刷新。

在动态上下文中使用时，开发指南参考：[@State装饰器：组件内状态（ArkTS-DT）](../../../ui/state-management/arkts-state.md)；在静态上下文中使用时，开发指南参考：[@State装饰器：组件内状态（ArkTS-ST）](../../../ui/state-management-static/arkts-static-state.md)

> **说明：**
>
> 从API version 7开始，支持该装饰器。
>
> 从API version 9开始，该装饰器支持在ArkTS卡片中使用。
>
> 从API version 11开始，该装饰器支持在原子化服务中使用。

**参数：**

无

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

ArkTS1.1示例：

```ts
@Component
struct StateExample {
    @State count: number = 0;
    build() { }
}
```

ArkTS1.2示例：

```ts
import { State } from '@ohos.arkui.stateManagement';
import { Component } from '@ohos.arkui.component';

@Component
struct StateExample {
    @State count: number = 0;
    build() { }
}
```