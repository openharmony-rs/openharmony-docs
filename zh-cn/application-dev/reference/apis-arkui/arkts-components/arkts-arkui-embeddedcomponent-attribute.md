# EmbeddedComponent属性/事件

定义EmbeddedComponent的属性函数。

**继承/实现关系：** EmbeddedComponentAttribute extends [CommonMethod<EmbeddedComponentAttribute>](CommonMethod<EmbeddedComponentAttribute>)

**起始版本：** 12

<!--Device-unnamed-declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>--><!--Device-unnamed-declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="ondrawready"></a>
## onDrawReady

```TypeScript
onDrawReady(callback: Callback<void>)
```

EmbeddedUIExtensionAbility绘制首帧时的回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedComponentAttribute-onDrawReady(callback: Callback<void>): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onDrawReady(callback: Callback<void>): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 |  |

<a id="onerror"></a>
## onError

```TypeScript
onError(callback: import('../api/@ohos.base').ErrorCallback)
```

当发生错误时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedComponentAttribute-onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').ErrorCallback | 是 |  |

<a id="onterminated"></a>
## onTerminated

```TypeScript
onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>)
```

当嵌入式UI的提供方终止时回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EmbeddedComponentAttribute-onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>): EmbeddedComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;TerminationInfo&gt; | 是 |  |

