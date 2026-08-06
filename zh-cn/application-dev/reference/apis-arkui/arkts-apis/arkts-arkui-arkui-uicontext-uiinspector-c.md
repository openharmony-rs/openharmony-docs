# UIInspector

提供注册组件布局和组件绘制送显完成回调通知的能力。送显指节点的绘制命令发送到图形服务并完成显示。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作，适用于需要精确感知组件布局和绘制时机的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class UIInspector--><!--Device-unnamed-export declare class UIInspector-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## createComponentObserver

```TypeScript
createComponentObserver(id: string): inspector.ComponentObserver
```

注册组件布局和组件绘制送显完成回调通知。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIInspector-createComponentObserver(id: string): inspector.ComponentObserver--><!--Device-UIInspector-createComponentObserver(id: string): inspector.ComponentObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string | 是 | 指定组件id，该id通过通用属性id或者key设置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| inspector.ComponentObserver | 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

## createComponentObserver

```TypeScript
createComponentObserver(id: string | int): inspector.ComponentObserver
```

注册组件布局和组件绘制送显完成回调通知。送显指节点的绘制命令发送到图形服务并完成显示。例如，开发者可在组件布局完成后获取组件精确尺寸，或在送显完成后执行截图、动画同步等操作。 相比createComponentObserver，新增支持传入UniqueID（系统为节点分配的唯一标识）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIInspector-createComponentObserver(id: string | int): inspector.ComponentObserver--><!--Device-UIInspector-createComponentObserver(id: string | int): inspector.ComponentObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | string \| int | 是 | 类型为string时，为指定的组件id，该id通过通用属性id或者key设置。使用组件id创建监听句柄时，请确保该id对应的组件已经存在，否则后续监听无法生效。类型为int时，为系统为节点分配的唯一标识UniqueID，UniqueID通过getUniqueId获取。使用UniqueID创建监听句柄时，请确保UniqueID对应的节点已经存在，否则后续监听无法生效。int的取值范围为1~2147483647的整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| inspector.ComponentObserver | 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

