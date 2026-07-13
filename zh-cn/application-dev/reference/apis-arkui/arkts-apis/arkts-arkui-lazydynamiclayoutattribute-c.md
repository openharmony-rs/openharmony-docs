# LazyDynamicLayoutAttribute

定义LazyDynamicLayout组件。

**继承/实现关系：** LazyDynamicLayoutAttribute extends [CommonMethod<LazyDynamicLayoutAttribute>](CommonMethod<LazyDynamicLayoutAttribute>)

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onVisibleIndexesChange

```TypeScript
onVisibleIndexesChange(callback: Callback<number[]> | undefined): LazyDynamicLayoutAttribute
```

当可见索引更改时调用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;number[]&gt; \| undefined | 是 | 可见索引变化时回调的回调函数。<br>传递undefined将取消注册回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| LazyDynamicLayoutAttribute | @syscap SystemCapability.ArkUI.ArkUI.Full@stagemodelonly@crossplatform@atomicservice |

