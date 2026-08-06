# CustomComponentLifecycleObserver

用户注册自定义组件生命周期回调后，当该自定义组件的生命周期发生变化时，将触发监听器中相应的生命周期回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

<!--Device-unnamed-export declare interface CustomComponentLifecycleObserver--><!--Device-unnamed-export declare interface CustomComponentLifecycleObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

```TypeScript
default aboutToAppear(): void
```

aboutToAppear函数在创建自定义组件的新实例后，执行其build()函数之前执行。开发者可以在此阶段修改状态变量。其功能与 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_类似，但是在自定义组件状 态机的约束下触发的。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default aboutToAppear(): void--><!--Device-CustomComponentLifecycleObserver-default aboutToAppear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

```TypeScript
default aboutToDisappear(): void
```

aboutToDisappear函数在自定义组件被销毁之前执行。不建议在aboutToDisappear函数中修改状态变量，特别是@Link变量的修改可能会导致应用程序行为不稳定。其功能与 \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_类似，不同的 是，CustomComponentLifecycleObserver中的aboutToDisappear函数受状态机约束，只有被监听的自定义组件状态向 CustomComponentLifecycleState.DISAPPEARED转变前触发回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default aboutToDisappear(): void--><!--Device-CustomComponentLifecycleObserver-default aboutToDisappear(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToRecycle

```TypeScript
default aboutToRecycle(): void
```

当组件被回收后触发，先执行应用程序中定义的必要回收操作，完成回收后调用aboutToRecycle函数。随后该组件被冻结，以避免该组件处于回收池时进行UI更新。最后，aboutToRecycle函数会递归遍历所有子组件，对每个完成 回收的组件调用aboutToRecycle函数。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default aboutToRecycle(): void--><!--Device-CustomComponentLifecycleObserver-default aboutToRecycle(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## aboutToReuse

```TypeScript
default aboutToReuse(params?: ReuseObject): void
```

当可复用的自定义组件从缓存中重新添加到节点树时调用aboutToReuse函数，以接收组件的构造参数。当params存在时，表示V1组件的复用回调。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default aboutToReuse(params?: ReuseObject): void--><!--Device-CustomComponentLifecycleObserver-default aboutToReuse(params?: ReuseObject): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 当params存在时，表示V1组件的复用回调。 |

## onDidBuild

```TypeScript
default onDidBuild(): void
```

onDidBuild函数在自定义组件的新实例构建完成后，执行其build()函数之后执行。开发者可以在此阶段实现一些不影响实际UI的功能，例如事件数据上报。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CustomComponentLifecycleObserver-default onDidBuild(): void--><!--Device-CustomComponentLifecycleObserver-default onDidBuild(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

