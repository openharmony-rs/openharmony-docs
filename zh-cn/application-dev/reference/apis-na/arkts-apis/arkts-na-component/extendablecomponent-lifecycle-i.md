# LifeCycle

自定义组件和自定义对话框的生命周期接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface LifeCycle--><!--Device-unnamed-export declare interface LifeCycle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
default aboutToAppear(): void
```

aboutToAppear Method. The aboutToAppear function is executed after a new instance of the custom component is created, before its build() function is executed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LifeCycle-default aboutToAppear(): void--><!--Device-LifeCycle-default aboutToAppear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
default aboutToDisappear(): void
```

aboutToDisappear Method. The aboutToDisappear function executes before a custom component is destroyed.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LifeCycle-default aboutToDisappear(): void--><!--Device-LifeCycle-default aboutToDisappear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## build

```TypeScript
build(): void
```

Customize the build process of the custom component.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LifeCycle-build(): void--><!--Device-LifeCycle-build(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDidBuild

```TypeScript
default onDidBuild(): void
```

onDidBuild函数在执行自定义组件的build()函数之后执行，开发者可以在这个阶段进行埋点数据上报等不影响实际UI的功能。不建议在onDidBuild函数中更改状态变量、使用animateTo等功能，这可能会导致不稳定 的UI表现。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LifeCycle-default onDidBuild(): void--><!--Device-LifeCycle-default onDidBuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

