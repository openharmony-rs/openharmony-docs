# ISinglePropertyChangeSubscriber（系统接口）

继承自[IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)。用来定义变量。

**继承/实现关系：** ISinglePropertyChangeSubscriber extends [IPropertySubscriber](arkts-arkui-ipropertysubscriber-i-sys.md)

**起始版本：** 7

<!--Device-unnamed-interface ISinglePropertyChangeSubscriber<T> extends IPropertySubscriber--><!--Device-unnamed-interface ISinglePropertyChangeSubscriber<T> extends IPropertySubscriber-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

<a id="haschanged"></a>
## hasChanged

```TypeScript
hasChanged(newValue: T): void
```

变化时调用。

**起始版本：** 7

<!--Device-ISinglePropertyChangeSubscriber-hasChanged(newValue: T): void--><!--Device-ISinglePropertyChangeSubscriber-hasChanged(newValue: T): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| newValue | T | 是 | T类型实例。 |

