# ComponentObserver

组件布局和组件绘制送显完成回调的句柄，通过该句柄可调用以下方法。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-inspector-interface ComponentObserver--><!--Device-inspector-interface ComponentObserver-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offDraw

```TypeScript
offDraw(callback?: VoidCallback): void
```

通过句柄向对应的查询条件取消注册回调，当组件绘制送显完成时不再触发指定的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-offDraw(callback?: VoidCallback): void--><!--Device-ComponentObserver-offDraw(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。callback需要和onDraw方法中的callback为相同对象时才能取消回调成功。 |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: VoidCallback): void
```

通过句柄向对应的查询条件取消注册回调，当组件的子组件绘制送显完成时不再触发指定的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-offDrawChildren(callback?: VoidCallback): void--><!--Device-ComponentObserver-offDrawChildren(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onDrawChildren方法中的callback为相同对象时才能取消回调成功。 |

## offDrawChildren

```TypeScript
offDrawChildren(callback?: Callback<int[]>): void
```

取消注册drawChildren事件回调。要实现在子组件绘制送显完成后停止触发特定回调，只需通过ComponentObserver句柄，取消注册该回调即可。 如果组件树中存在多个drawChildren事件回调，取消最顶层的回调后，其余drawChildren事件回调也无法生效。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void--><!--Device-ComponentObserver-offDrawChildren(callback?: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int[]&gt; | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onDrawChildren方法中的callback为相同对象时才能取消回调成功。 |

## offLayout

```TypeScript
offLayout(callback?: VoidCallback): void
```

通过句柄向对应的查询条件取消注册回调，当组件布局完成时不再触发指定的回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-offLayout(callback?: VoidCallback): void--><!--Device-ComponentObserver-offLayout(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onLayout方法中的callback为相同对象时才能取消回调成功。 |

## offLayoutChildren

```TypeScript
offLayoutChildren(callback?: VoidCallback): void
```

通过句柄向对应的查询条件取消注册回调，当组件的子组件布局完成时不再触发指定的回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-offLayoutChildren(callback?: VoidCallback): void--><!--Device-ComponentObserver-offLayoutChildren(callback?: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 否 | 需要取消注册的回调，如果参数缺省则取消注册该句柄下所有的回调。 callback需要和onLayoutChildren方法中的callback为相同对象时才能取消回调成功。 |

## onDraw

```TypeScript
onDraw(callback: VoidCallback): void
```

通过句柄向对应的查询条件注册回调，当组件绘制送显完成时会触发该回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-onDraw(callback: VoidCallback): void--><!--Device-ComponentObserver-onDraw(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 是 | 监听draw的回调。 |

## onDrawChildren

```TypeScript
onDrawChildren(callback: VoidCallback): void
```

通过ComponentObserver注册drawChildren事件回调方法，当组件的子组件绘制送显完成时会触发该回调方法。 如果组件树中存在多个drawChildren事件回调，只会触发在最顶层的drawChildren事件回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-onDrawChildren(callback: VoidCallback): void--><!--Device-ComponentObserver-onDrawChildren(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 是 | 监听drawChildren的回调。 |

## onDrawChildren

```TypeScript
onDrawChildren(callback: Callback<int[]>): void
```

通过ComponentObserver注册drawChildren事件回调。使用callback异步回调。 与on('drawChildren')相比，本方法在回调中额外返回子组件的uniqueId信息（Callback&lt;int[]&gt;），便于开发者定位具体子组件。如需获取子组件标识，建议使用本方法；若不需要子组件信息，两者均可使用。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void--><!--Device-ComponentObserver-onDrawChildren(callback: Callback<int[]>): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;int[]&gt; | 是 | 监听drawChildren的回调，回调参数为子组件uniqueId数组，表示绘制送显完成的子组件的唯一标识列表。 |

## onLayout

```TypeScript
onLayout(callback: VoidCallback): void
```

通过句柄向对应的查询条件注册回调，当组件布局完成时会触发该回调。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-onLayout(callback: VoidCallback): void--><!--Device-ComponentObserver-onLayout(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 是 | 监听layout的回调。 |

## onLayoutChildren

```TypeScript
onLayoutChildren(callback: VoidCallback): void
```

以当前注册事件回调的节点为根节点，当子树中的节点位于UI组件主树中且完成布局时，会触发该回调。如果组件树中存在多个layoutChildren事件回调，只会触发最顶层的layoutChildren事件回调。 通过offLayoutChildren取消最顶层的回调后，其余layoutChildren事件回调也无法生效。当前节点注册回调后，不支持修改其在UI组件主树中的层级位置。如需调整，请先取消事件回调，再重新注册事件回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ComponentObserver-onLayoutChildren(callback: VoidCallback): void--><!--Device-ComponentObserver-onLayoutChildren(callback: VoidCallback): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | VoidCallback | 是 | 监听layoutChildren的回调。 |

