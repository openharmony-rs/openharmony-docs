# EmbeddedComponent属性/事件

支持通用属性。

与屏幕坐标相关的事件信息，根据**EmbeddedComponent**的位置、宽高进行转换后，传递给EmbeddedUIExtensionAbility处理。

不支持点击事件等通用事件。仅支持以下事件。

**继承/实现关系：** EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onDrawReady

```TypeScript
onDrawReady(callback: Callback<void>)
```

被拉起的EmbeddedUIExtensionAbility绘制第一帧时触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | 是 | 回调函数，在EmbeddedUIExtensionAbility绘制第一帧时触发。 |

## onError

```TypeScript
onError(callback: import('../api/@ohos.base').ErrorCallback)
```

被拉起的EmbeddedUIExtensionAbility在运行过程中发生异常，或出现拉起EmbeddedUIExtensionAbility失败、通知提供方切后台/销毁EmbeddedUIExtensionAbility失败、在EmbeddedUIExtensionAbility中嵌套使用EmbeddedComponent等异常情形时，触发本回调。可通过回调参数中的code、name和message获取错误信息并做处理，业务错误码详细介绍请参见UIExtension错误码。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').ErrorCallback | 是 | 回调函数，入参用于接收异常信息，类型为BusinessError，可通过参数中的`code`、`name`和`message`获取错误信息并做处理。 |

## onTerminated

```TypeScript
onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>)
```

被拉起的EmbeddedUIExtensionAbility通过调用terminateSelfWithResult或者terminateSelf正常退出时，触发本回调函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;[TerminationInfo](arkts-arkui-terminationinfo-i.md)&gt; | 是 | 回调函数，入参用于接收EmbeddedUIExtensionAbility的返回结果，类型为TerminationInfo。 |
