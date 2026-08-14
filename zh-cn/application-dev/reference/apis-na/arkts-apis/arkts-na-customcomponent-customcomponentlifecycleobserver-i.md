# CustomComponentLifecycleObserver

用户注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CustomComponentLifecycleObserver--><!--Device-unnamed-export declare interface CustomComponentLifecycleObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
aboutToAppear(): void
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CustomComponentLifecycleObserver-aboutToAppear(): void--><!--Device-CustomComponentLifecycleObserver-aboutToAppear(): void-End-->

## aboutToDisappear

```TypeScript
aboutToDisappear(): void
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CustomComponentLifecycleObserver-aboutToDisappear(): void--><!--Device-CustomComponentLifecycleObserver-aboutToDisappear(): void-End-->

## aboutToRecycle

```TypeScript
aboutToRecycle(): void
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CustomComponentLifecycleObserver-aboutToRecycle(): void--><!--Device-CustomComponentLifecycleObserver-aboutToRecycle(): void-End-->

## aboutToReuse

```TypeScript
aboutToReuse(params?: ReuseObject): void
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CustomComponentLifecycleObserver-aboutToReuse(params?: ReuseObject): void--><!--Device-CustomComponentLifecycleObserver-aboutToReuse(params?: ReuseObject): void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [ReuseObject](arkts-na-customcomponent-reuseobject-c.md) | 否 |  |

## onDidBuild

```TypeScript
onDidBuild(): void
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CustomComponentLifecycleObserver-onDidBuild(): void--><!--Device-CustomComponentLifecycleObserver-onDidBuild(): void-End-->

## default

```TypeScript
default
```

当组件被回收后触发，先执行应用程序中定义的必要回收操作，完成回收后调用aboutToRecycle函数。随后该组件被冻结，以避免该组件处于回收池时进行UI更新。最后，aboutToRecycle函数会递归遍历所有子组件，对每个完成 回收的组件调用aboutToRecycle函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default--><!--Device-CustomComponentLifecycleObserver-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

