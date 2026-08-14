# TreeListenerManagerV2

树视图组件的监听管理器，可以将此对象绑定至树视图组件，然后通过它管理树视图监听器的变化，同一个监听管理器不可以控制多个树视图组件。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class TreeListenerManagerV2--><!--Device-unnamed-export declare class TreeListenerManagerV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getInstance

```TypeScript
static getInstance(): TreeListenerManagerV2
```

获取树视图组件的监听管理器单例对象。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TreeListenerManagerV2-static getInstance(): TreeListenerManagerV2--><!--Device-TreeListenerManagerV2-static getInstance(): TreeListenerManagerV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TreeListenerManagerV2](arkts-na-arkui-advanced-treeviewv2-treelistenermanagerv2-c.md) | 返回获取到的树视图组件的监听管理器单例对象。 |

## getTreeListener

```TypeScript
getTreeListener(): TreeListenerV2
```

获取树视图监听器实例。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TreeListenerManagerV2-getTreeListener(): TreeListenerV2--><!--Device-TreeListenerManagerV2-getTreeListener(): TreeListenerV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [TreeListenerV2](arkts-na-arkui-advanced-treeviewv2-treelistenerv2-c.md) | 返回获取到的树视图监听器实例。 |

