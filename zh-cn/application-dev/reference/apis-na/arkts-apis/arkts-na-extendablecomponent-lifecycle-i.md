# LifeCycle

自定义组件和自定义对话框的生命周期接口。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface LifeCycle--><!--Device-unnamed-export declare interface LifeCycle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear(): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LifeCycle-aboutToAppear(): void--><!--Device-LifeCycle-aboutToAppear(): void-End-->

## aboutToDisappear

```TypeScript
aboutToDisappear(): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LifeCycle-aboutToDisappear(): void--><!--Device-LifeCycle-aboutToDisappear(): void-End-->

## onDidBuild

```TypeScript
onDidBuild(): void
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-LifeCycle-onDidBuild(): void--><!--Device-LifeCycle-onDidBuild(): void-End-->

## default

```TypeScript
default
```

onDidBuild函数在执行自定义组件的build()函数之后执行，开发者可以在这个阶段进行埋点数据上报等不影响实际UI的功能。不建议在onDidBuild函数中更改状态变量、使用animateTo等功能，这可能会导致不稳定 的UI表现。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LifeCycle-default--><!--Device-LifeCycle-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

